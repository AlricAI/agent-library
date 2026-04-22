# Spec

> ## 1. 系统概述 (Overview)

**OmniBox** 是一个用于管理 AI Agent 运行时环境的高性能、安全、可扩展的沙箱编排系统。它旨在为上层 Agent（如 Coding Agent, Browser Agent）提供统一的、标准化的计算环境。

### 核心目标


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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

export interface SandboxOptio

*[truncated — see source for full prompt]*