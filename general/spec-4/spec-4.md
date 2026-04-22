---
name: Spec
description: ## 1. 系统概述 (Overview)

**OmniBox** 是一个用于管理 AI Agent 运行时环境的高性能、安全、可扩展的沙箱编排系统。它旨在为上层 Agent（如 Coding Agent, Browser Agent）提供统一的、标准化的计算环境。

### 核心目标

model: claude-sonnet-4-5
---
# Project Name: OmniBox (Enterprise Sandbox Orchestration System)

## 1. 系统概述 (Overview)

**OmniBox** 是一个用于管理 AI Agent 运行时环境的高性能、安全、可扩展的沙箱编排系统。它旨在为上层 Agent（如 Coding Agent, Browser Agent）提供统一的、标准化的计算环境。

### 核心目标

1. **统一抽象**：通过统一的 API 管理不同类型的沙箱（CLI Code Runner, GUI Cloud Browser）。
2. **安全隔离**：支持从 Docker 原生隔离平滑升级到 gVisor (runsc) 内核态隔离。
3. **状态持久化**：支持挂载用户数据（如浏览器 Profile、代码仓库），实现 Long-running Sessions。
4. **可观测性**：内置 VNC 视觉流、Log 流、Metrics 监控。

---

## 2. 系统架构 (System Architecture)

### 2.1 顶层架构图

```mermaid
graph TD
    Client[Agent / Client] -- REST/gRPC --> Core[OmniBox Core Service]
    
    subgraph "Infrastructure Layer"
        Core -- "Driver Interface" --> DockerDriver[Docker Driver]
        Core -- "Driver Interface" --> K8sDriver[K8s Driver (Future)]
        Core -- "Driver Interface" --> FirecrackerDriver[MicroVM Driver (Future)]
    end

    subgraph "Runtime Plane (Host)"
        DockerDriver -- Manage --> Container[Sandbox Container]
        
        subgraph "Sandbox Container"
            Sidecar[Sidecar Agent (RPC Server)]
            App[User Application / Chrome]
            Supervisord[Process Manager]
            VNC[X11/VNC Server (Optional)]
        end
    end

    Client -- WebSocket --> Sidecar

```

### 2.2 核心模块划分

1. **Session Manager**: 管理沙箱生命周期（Create, Start, Stop, Hibernate）。
2. **Driver Adapter**: 适配底层容器技术（Docker, K8s, Firecracker）。
3. **Sidecar Proxy**: 处理与容器内部的通信（命令执行、文件传输）。
4. **Network Manager**: 负责端口动态分配、VNC 流量代理。

---

## 3. 核心抽象与接口设计 (Core Abstractions)

为了保证“可扩展”和“接入简单”，我们使用 TypeScript 接口定义核心契约。

### 3.1 沙箱配置接口 (SandboxProfile)

定义一个沙箱“长什么样”。

```typescript
// types/profile.ts

export enum RuntimeType {
  CODE_EXEC = 'code_exec',      // 纯代码执行 (Python/Node)
  BROWSER_KIOSK = 'browser_kiosk' // 浏览器 GUI 模式
}

export enum IsolationLevel {
  STANDARD = 'standard', // 普通 Docker Namespace
  SECURE = 'secure'      // gVisor / Kata
}

export interface SandboxOptions {
  profileId: string;      // 基础镜像标识 (e.g., 'python-3.10-slim', 'chrome-kiosk')
  runtime: RuntimeType;   
  isolation: IsolationLevel;
  enableVisual: boolean;  // 是否开启 VNC/GUI
  persistence?: {
    enabled: boolean;
    userId: string;       // 用于挂载 Volume: /data/users/{userId} -> /app/data
  };
  resources?: {
    cpu: number;          // NanoCPU
    memory: number;       // Bytes
  };
}

```

### 3.2 驱动层接口 (Driver Interface)

任何底层运行时（Docker/K8s）必须实现此接口。这使得切换底层技术时无需修改业务逻辑。

```typescript
// interfaces/driver.ts

export interface ExecutionResult {
  stdout: string;
  stderr: string;
  exitCode: number;
}

export interface ISandboxDriver {
  // 生命周期管理
  create(id: string, options: SandboxOptions): Promise<void>;
  start(id: string): Promise<void>;
  stop(id: string): Promise<void>;
  destroy(id: string): Promise<void>;

  // 信息查询
  getNetworkInfo(id: string): Promise<{ ip: string; ports: Record<string, number> }>;
  
  // 资源检查
  isAlive(id: string): Promise<boolean>;
}

```

### 3.3 容器交互接口 (Agent Protocol)

这是上层 Agent 与沙箱沟通的标准化协议。

```typescript
// interfaces/agent-protocol.ts

export interface ISandboxClient {
  // 命令执行
  exec(cmd: string, timeout?: number): Promise<ExecutionResult>;
  
  // 文件操作
  writeFile(path: string, content: string): Promise<void>;
  readFile(path: string): Promise<string>;
  
  // 视觉/浏览器能力 (如果启用)
  getVncStreamUrl(): string; 
  getCdpEndpoint(): string; // Chrome DevTools Protocol WebSocket URL
}

```

---

## 4. 详细实现规范 (Implementation Specs)

### 4.1 目录结构

```text
src/
├── config/              # 全局配置 (Docker Host, Ports Range)
├── core/
│   ├── driver/          # 驱动实现 (DockerDriver.ts)
│   ├── session/         # Session 状态管理
│   └── pool/            # (可选) 预热容器池
├── api/                 # REST/GraphQL 控制层
├── sidecar/             # 注入到容器内的 Python/Go 代码
│   ├── server.py        # 内部 RPC 服务
│   └── entrypoint.sh    # 启动脚本
└── templates/           # Dockerfile 模板
    ├── python-base/
    └── chrome-kiosk/

```

### 4.2 关键技术实现细节

#### A. 容器内部 Sidecar 设计 (The "Trojan Horse")

* **语言**: Python 3 (兼容性最好) 或 Golang (单文件部署)。
* **通信协议**: HTTP (简单) 或 JSON-RPC over TCP (高效)。
* **功能**:

1. 接收 `/exec` 请求，调用 `subprocess.run`。
2. 接收 `/file` 请求，读写本地文件系统。

* **安全**: Sidecar 仅监听 `0.0.0.0:8000`，宿主机通过端口映射访问。

#### B. gVisor 集成 (Security)

* **配置方式**: 在 `DockerDriver.ts` 中，根据 `IsolationLevel.SECURE` 动态注入参数。
* **代码逻辑**:

```typescript
const hostConfig = {
  // ...其他配置
  Runtime: options.isolation === IsolationLevel.SECURE ? 'runsc' : 'runc'
};

```

* **前置条件**: 宿主机需安装 `gVisor` 并配置 Docker `daemon.json`。

#### C. 可视化 (VNC/noVNC) 实现

* **架构**:
* 容器内运行 `Xvfb` (虚拟显卡) + `Fluxbox` (窗口管理) + `x11vnc`。
* **优化**: 为了方便前端接入，容器内直接运行 `websockify`，暴露 WebSocket 端口 (如 6080)。

* **外部接入**:
* OmniBox 返回 `vncUrl: http://sandbox-ip:mapped-port/vnc.html`。
* 上层 Agent 的前端直接 iframe 嵌入即可。

#### D. 持久化 (Persistence)

* **策略**: Host Path Mounting (最简单有效)。
* **路径规范**: `HOST_ROOT/sessions/{userId}/chrome_data` -> 挂载到容器内 `~/.config/google-chrome`。
* **权限管理**: 确保宿主机目录权限与容器内 UID (通常是 1000) 匹配。

---

## 5. 开发路线图 (Coding Agent Instructions)

请按照以下阶段让 Coding Agent 生成代码：

### Phase 1: 基础骨架 (The Skeleton)

1. 搭建 Node.js (TypeScript) 项目，引入 `dockerode`。
2. 实现 `SandboxOptions` 和 `ISandboxDriver` 接口定义。
3. 实现 `DockerDriver` 的基础版：支持 `create` 和 `destroy` 一个标准的 Ubuntu 容器。

### Phase 2: Sidecar 通信 (The Brain)

1. 编写 `sidecar/server.py` (FastAPI/Flask)，实现 `/exec` 接口。
2. 完善 `DockerDriver`，使其在启动容器时注入 Sidecar 代码（通过 COPY 或 Volume）。
3. 实现 `ISandboxClient`，让 Node.js 可以发送命令给容器内的 Sidecar 并获取结果。

### Phase 3: GUI 与持久化 (The Eyes & Memory)

1. 创建 `Dockerfile.browser`，集成 Chrome, Xvfb, Fluxbox, noVNC。
2. 升级 `DockerDriver`，支持 `enableVisual` 参数，配置端口映射 (6080, 9222)。
3. 实现 `persistence` 逻辑，处理 Host Volume 挂载。

### Phase 4: 安全与加固 (The Shield)

1. 添加 `gVisor` 支持逻辑。
2. 添加资源限制 (CPU/Memory)。
3. 实现容器心跳检测与僵尸容器清理。

---

## 6. 示例代码片段 (For Coding Agent Reference)

**Docker Driver - Create Method Example:**

```typescript
async create(id: string, options: SandboxOptions): Promise<void> {
    const portBindings: any = {
        '8000/tcp': [{ HostPort: '0' }] // RPC Port
    };

    if (options.enableVisual) {
        portBindings['6080/tcp'] = [{ HostPort: '0' }]; // VNC
        portBindings['9222/tcp'] = [{ HostPort: '0' }]; // CDP
    }

    const volumeBinds = [];
    if (options.persistence?.enabled) {
        const hostPath = path.join(process.env.DATA_ROOT, options.persistence.userId);
        ensureDirSync(hostPath); // Ensure host dir exists
        volumeBinds.push(`${hostPath}:/data/user_profile`);
    }

    await this.docker.createContainer({
        Image: this.getImageName(options.runtime),
        name: `omnibox-${id}`,
        HostConfig: {
            PortBindings: portBindings,
            Binds: volumeBinds,
            Runtime: options.isolation === 'secure' ? 'runsc' : 'runc',
            Memory: options.resources?.memory || 1024 * 1024 * 1024,
            NanoCpus: options.resources?.cpu || 1000000000,
        },
        Env: [
            `VNC_ENABLED=${options.enableVisual}`,
            `SANDBOX_ID=${id}`
        ]
    });
}

```

---

## 7. 补充规范 (Implementation Addendums)

### 7.1 Sidecar 认证机制（可选）

在生产环境中，建议为 Sidecar 服务添加认证：

```python
# server.py
from fastapi import Header, HTTPException

async def verify_token(x_auth_token: str = Header(...)):
    if x_auth_token != os.environ.get('SIDECAR_TOKEN'):
        raise HTTPException(status_code=401, detail="Invalid token")

@app.post("/exec", dependencies=[Depends(verify_token)])
async def execute_command(req: ExecRequest):
    ...
```

### 7.2 优雅关闭机制

确保系统在关闭时清理所有资源：

```typescript
async cleanup(): Promise<void> {
  // 停止心跳监控
  this.stopHeartbeat();

  // 清理所有会话
  const destroyPromises = Array.from(this.sessions.keys()).map(id =>
    this.destroySession(id).catch(err =>
      console.error(`Failed to destroy ${id}:`, err)
    )
  );
  await Promise.allSettled(destroyPromises);
}

process.on('SIGTERM', async () => {
  await sessionManager.cleanup();
  process.exit(0);
});
```

### 7.3 Windows 兼容性

Windows Docker Desktop 使用 named pipe 而非 Unix socket：

```typescript
const socketPath = process.platform === 'win32'
  ? '\\\\.\\pipe\\docker_engine'
  : '/var/run/docker.sock';
```

### 7.4 故障排查

**问题**: `Error: connect ENOENT \\\\.\\pipe\\docker_engine`
- **原因**: Docker Desktop 未运行
- **解决**: 启动 Docker Desktop

**问题**: 镜像构建失败
- **原因**: 网络问题或依赖包不可用
- **解决**: 检查网络连接，重试构建

**调试技巧**:
```bash
# 启用详细日志
LOG_LEVEL=debug pnpm tsx examples/01-code-execution-sandbox.ts

# 检查容器状态
docker ps -a | grep omnibox
docker logs omnibox-<id>
```