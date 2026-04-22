# Add New Doc Guide Zh

> 本文面向维护者或贡献者，介绍如何把“新的上游文档”纳入本仓库的自动同步与翻译流程，或在现有专题中新增页面并正确出现在站点侧边栏中。

适用读者：
- 想要新增一个要跟踪的开源项目文档仓库（如某库的官网文档）；
- 想在现有专题中增加/修复某些页面，并让流水线自动翻译；
- 想在本地运行翻译流水线进行

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 添加新的文档翻译指南

本文面向维护者或贡献者，介绍如何把“新的上游文档”纳入本仓库的自动同步与翻译流程，或在现有专题中新增页面并正确出现在站点侧边栏中。

适用读者：
- 想要新增一个要跟踪的开源项目文档仓库（如某库的官网文档）；
- 想在现有专题中增加/修复某些页面，并让流水线自动翻译；
- 想在本地运行翻译流水线进行验证。

---

## 一、关键概念速览

- docType（文档类型）：站点中每个专题的“类型”标识，如 `kotlin`、`kmp`、`ktor`、`sqldelight`、`koog`、`coil` 等。它决定了输出目录、侧边栏文件名等。
- REPOS 配置：位于 `.github/scripts/docs-repo-config.mjs`，定义要跟踪的上游仓库、分支、文档目录、资源目录以及处理策略（strategy）。
- strategy（策略）：位于 `.github/scripts/strategy-*.mjs`，定义如何发现需要处理的文档文件（glob pattern）、在不同阶段（同步/检测/翻译）做自定义处理（如 Writerside 的 `.topic` 转换、侧边栏生成、资源拷贝等）。
- Sidebar 与 Locale：侧边栏 JSON 写在 `docs/.vitepress/sidebar/{docType}.sidebar.json`，多语言文案写在 `docs/.vitepress/locales/*.json`，由 `SidebarProcessor.mjs` 自动生成/增量更新。
- 输出目录结构：
    - 简体中文（默认）：`docs/{docType}/...`
    - 其它语言：`docs/{lang}/{docType}/...`（如 `docs/ja/kotlin/...`）。

---

## 二、准备工作

- Node 20+，pnpm 已安装
- 拉取本项目代码并安装依赖：
  ```bash
  pnpm i
  ```

---

## 三、新增一个“上游文档仓库/新专题”

当你希望把一个全新的开源项目文档纳入本项目并自动翻译时，按以下步骤：

1) 增加 strategy（若可复用现有策略，可跳过）
- 根据上游站点技术栈选择相近策略：
    - Writerside 示例：`kotlinStrategy`、`kmpStrategy`（处理 `.topic`、生成 Writerside 侧边栏）。
    - MkDocs 示例：`koogStrategy`、`coilStrategy`（从 `mkdocs.yml` 生成侧边栏）。
    - Docusaurus 示例：`koinStrategy`（一般是纯 Markdown 目录结构）。
- 如需自定义，复制一个最接近的策略文件，新建例如 `.github/scripts/strategy-xxx.mjs`：
  ```js
  import { defaultStrategy } from "./strategy.mjs";
  import path from "path";
  import fs from "fs-extra";
  import { generateSidebar } from "./SidebarProcessor.mjs";

  export const myLibStrategy = {
    ...defaultStrategy,
    // 1) 指定需要处理的文档文件匹配模式（相对上游仓库根目录）
    getDocPatterns: () => ["docs/**/*.md"],

    // 2) 如需：拉取后做预处理（可为空）
    postSync: async (repoPath) => {},

    // 3) 检测阶段：生成侧边栏（按上游类型择一）
    postDetect: async (repoConfig, task) => {
      const repoPath = repoConfig.path;
      const sidebarPath = path.join(repoPath, "docs/mkdocs.yml"); // 若是 MkDocs
      const docType = repoPath.replace("-repo", "");
      if (await fs.pathExists(sidebarPath)) {
        await generateSidebar(sidebarPath, docType);
      }
    },

 

*[truncated — see source for full prompt]*