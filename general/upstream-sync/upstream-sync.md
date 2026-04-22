---
name: UPSTREAM SYNC
description: 本文档说明如何将上游 Paperclip 项目的更新同步到 UOPC。

## 什么是上游？

- **上游（Upstream）**：原始的 Paperclip 项目 https://github.com/paperclipai/paperclip
- **UOPC**：本项目，基于 Papercl
model: claude-sonnet-4-5
---
# GitHub 上游同步指南

本文档说明如何将上游 Paperclip 项目的更新同步到 UOPC。

## 什么是上游？

- **上游（Upstream）**：原始的 Paperclip 项目 https://github.com/paperclipai/paperclip
- **UOPC**：本项目，基于 Paperclip 改造的中文版

## 为什么要同步上游？

- 获取最新功能和安全修复
- 保持与开源社区同步
- 享受 Paperclip 团队的开发成果

## 同步步骤

### 方式一：手动合并（推荐）

```bash
# 1. 确保已添加上游 remote（只需执行一次）
git remote add upstream https://github.com/paperclipai/paperclip.git

# 2. 获取上游最新代码
git fetch upstream

# 3. 查看上游有哪些更新
git log --oneline upstream/main -10

# 4. 合并上游更新到你的分支
git merge upstream/main

# 5. 如果有冲突，手动解决后提交
# git add .
# git commit -m "Merge upstream changes"
```

### 方式二：定期Rebase

```bash
# 定期用 rebase 保持线性历史
git fetch upstream
git rebase upstream/main
```

## 同步后的关键检查

同步完成后，必须检查以下文件是否完好：

### 1. 检查 i18n 文件是否存在

```bash
ls -la ui/src/i18n/locales/
# 应该看到: en.json  zh-CN.json
```

### 2. 检查 main.tsx 是否引入 i18n

```bash
grep "i18n" ui/src/main.tsx
# 应该看到: import "./i18n";
```

### 3. 检查 Sidebar 是否有语言切换器

```bash
grep "LanguageSwitcher" ui/src/components/Sidebar.tsx
# 应该看到: import { LanguageSwitcher } from "@/i18n/LanguageSwitcher";
```

### 4. 检查 package.json 依赖

```bash
grep "i18next" ui/package.json
# 应该看到 i18next 和 react-i18next
```

## 如果文件被覆盖了怎么办

### 恢复中文翻译文件

```bash
# 如果 zh-CN.json 丢失，从备份恢复
# 或者手动重建 ui/src/i18n/locales/zh-CN.json
```

### 重新添加 i18n 到 main.tsx

在 `ui/src/main.tsx` 末尾添加：
```tsx
import "./i18n";
```

### 重新添加语言切换器到 Sidebar

在 `ui/src/components/Sidebar.tsx` 中：

1. 添加导入：
```tsx
import { LanguageSwitcher } from "@/i18n/LanguageSwitcher";
import { Globe } from "lucide-react";
```

2. 在 Company 区域末尾添加：
```tsx
<div className="flex items-center gap-2 px-3 py-2 border-t border-border mt-2">
  <Globe className="w-4 h-4 text-muted-foreground" />
  <LanguageSwitcher />
</div>
```

## 备份建议

在每次同步前，建议备份核心文件：

```bash
# 备份中文翻译
cp ui/src/i18n/locales/zh-CN.json ./zh-CN.json.backup

# 同步后检查
if [ ! -f ui/src/i18n/locales/zh-CN.json ]; then
  cp ./zh-CN.json.backup ui/src/i18n/locales/zh-CN.json
fi
```

## 常见问题

**Q: 合并冲突太多怎么办？**
A: 可以只 cherry-pick 特定提交，或者暂时跳过冲突文件，只合并不冲突的部分。

**Q: 不想每次都手动检查怎么办？**
A: 可以创建脚本自动检查并修复，或者只在必要时手动同步。

**Q: 能否自动同步？**
A: 不推荐，自动合并可能导致生产问题。建议手动审查后再合并。

## 联系方式

如有问题，请提交 Issue 或联系维护者。