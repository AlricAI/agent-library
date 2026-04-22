# ARCHITECTURE

> Welcome to your ultimate full-stack React Native / API template!

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🏗️ Full-Stack Expo + Hono + oRPC Monorepo Template

Welcome to your ultimate full-stack React Native / API template! This codebase is designed to be highly scalable, 100% type-safe from database to mobile app, and built on the most modern edge-ready technologies.

This document serves as your "Source of Truth" for how the architecture works, why certain technologies were chosen, and how to replicate or build upon this template for future projects.

---

## 🛠️ The Tech Stack

### Monorepo & Tooling
- **[pnpm workspaces](https://pnpm.io/workspaces)**: Manages dependencies efficiently across multiple packages via hoisting.
- **[Turborepo](https://turbo.build/)**: Orchestrates tasks (`pnpm dev`, `pnpm build`) with advanced caching. It ensures that when you run `dev`, both the frontend and backend boot up simultaneously.

### The Backend (`apps/server`)
- **[Hono](https://hono.dev/)**: An ultra-fast, lightweight web framework designed for the Edge (Vercel, Cloudflare, Bun) and Node.js. It replaces traditional Express.
- **[oRPC](https://orpc.dev/) (Server)**: A contract-first RPC framework. Instead of manually maintaining API types, oRPC ensures your server strictly implements a predefined contract, and the client inherently knows exactly what to expect.

### The Frontend (`apps/mobile`)
- **[Expo](https://expo.dev/) & React Native**: The universal React framework for native apps.
- **[Expo Router](https://docs.expo.dev/router/introduction/)**: File-based routing for React Native.
- **[oRPC](https://orpc.dev/) (Client) + TanStack Query**: Automatically generates React Query hooks (`useQuery`, `useMutation`) directly from your backend contract. You never have to manually type a `fetch` request again.
- **[HeroUI Native](https://heroui.com/) / Tailwind v4**: Modern, utility-first styling tailored for React Native.

**Mobile-only deep dives** (Share Quick, cache/sync, feed, workspace `dist/`): see [docs/mobile/README.md](./mobile/README.md).

### The Data Layer
- **[Dri

*[truncated — see source for full prompt]*