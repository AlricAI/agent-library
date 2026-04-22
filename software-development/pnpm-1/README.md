# PNPM

> This project has been migrated from npm to pnpm to improve dependency management and developer experience.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Migration to pnpm

This project has been migrated from npm to pnpm to improve dependency management and developer experience.

## Why pnpm?

- **Faster installation**: pnpm is significantly faster than npm and yarn
- **Disk space savings**: pnpm uses a content-addressable store to avoid duplication
- **Phantom dependency prevention**: pnpm creates a strict node_modules structure
- **Native workspaces support**: simplified monorepo management

## How to use pnpm

### Installation

```bash
# Global installation of pnpm
npm install -g pnpm@10.8.1

# Or with corepack (available with Node.js 22+)
corepack enable
corepack prepare pnpm@10.8.1 --activate
```

### Common commands

| npm command     | pnpm equivalent  |
| --------------- | ---------------- |
| `npm install`   | `pnpm install`   |
| `npm run build` | `pnpm run build` |
| `npm test`      | `pnpm test`      |
| `npm run lint`  | `pnpm run lint`  |

### Workspace-specific commands

| Action                                     | Command                                  |
| ------------------------------------------ | ---------------------------------------- |
| Run a command in a specific package        | `pnpm --filter @openai/codex run build`  |
| Install a dependency in a specific package | `pnpm --filter @openai/codex add lodash` |
| Run a command in all packages              | `pnpm -r run test`                       |

## Monorepo structure

```
codex/
├── pnpm-workspace.yaml    # Workspace configuration
├── .npmrc                 # pnpm configuration
├── package.json           # Root dependencies and scripts
├── codex-cli/             # Main package
│   └── package.json       # codex-cli specific dependencies
└── docs/                  # Documentation (future package)
```

## Configuration files

- **pnpm-workspace.yaml**: Defines the packages included in the monorepo
- **.npmrc**: Configures pnpm behavior
- **Root package.json**: Contains shared scripts and dependencies

## CI/CD

CI/CD workflows have be

*[truncated — see source for full prompt]*