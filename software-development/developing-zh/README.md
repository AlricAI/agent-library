# DEVELOPING Zh

> ## 快速开始

UOPC 可在本地开发，无需手动配置 PostgreSQL。

## 前置要求

- Node.js 20+
- pnpm 9+

## 开发模式

### 自动数据库（推荐）

不设置 DATABASE_URL，使用嵌入式 PGlite：

```bash
# 自动创建 pgli

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# UOPC 开发指南

## 快速开始

UOPC 可在本地开发，无需手动配置 PostgreSQL。

## 前置要求

- Node.js 20+
- pnpm 9+

## 开发模式

### 自动数据库（推荐）

不设置 DATABASE_URL，使用嵌入式 PGlite：

```bash
# 自动创建 pglite 数据库
pnpm dev
```

### PostgreSQL 模式

需要外部 PostgreSQL：

```bash
# 设置数据库 URL
export DATABASE_URL="postgresql://user:pass@localhost:5432/paperclip"

# 启动开发
pnpm dev
```

## 常用命令

```bash
pnpm dev              # 完整开发模式 (API + UI, watch模式)
pnpm dev:once        # 完整开发模式（不监听文件）
pnpm dev:server      # 仅服务器
pnpm build           # 构建所有
pnpm typecheck       # 类型检查
pnpm test:run        # 运行测试
pnpm db:generate     # 生成数据库迁移
pnpm db:migrate     # 应用迁移
```

## API 地址

- 本地 API: http://localhost:3100
- 本地 UI: http://localhost:3100 (开发模式)

## 技术栈

| 层 | 技术 |
|---|------|
| 前端 | React + Vite |
| 后端 | Express + Node.js |
| 数据库 | PostgreSQL / PGlite |
| ORM | Drizzle |
| 部署 | Docker |

## 目录结构

```
UOPC/
├── server/          # Express REST API
├── ui/             # React 前端
├── packages/       # 核心包
│   ├── db/        # Drizzle schema
│   ├── shared/    # 共享类型
│   ├── adapters/  # Agent 适配器
│   └── plugins/   # 插件系统
├── companies/     # 公司模板库
└── doc/          # 文档
```

## 开发注意事项

- 不要提交 pnpm-lock.yaml 到 PR
- PR CI 会在 manifest 变化时验证依赖
- 推送到 master 会自动更新 lockfile

## 测试

```bash
# 运行所有测试
pnpm test:run

# 运行 UI 测试
pnpm ui:test

# 运行服务器测试
pnpm server:test
```

## 许可证

MIT © 2026 UOPC