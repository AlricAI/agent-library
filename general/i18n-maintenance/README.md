# I18N MAINTENANCE

> ## 概述

本项目已集成 `i18next` + `react-i18next` 实现国际化支持。语言文件位于 `ui/src/i18n/locales/` 目录。

## 文件结构

```
ui/src/i18n/
├── index.ts              # i18n 初始化配置


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 中文语言包维护指南

## 概述

本项目已集成 `i18next` + `react-i18next` 实现国际化支持。语言文件位于 `ui/src/i18n/locales/` 目录。

## 文件结构

```
ui/src/i18n/
├── index.ts              # i18n 初始化配置
├── useLanguageSwitcher.ts  # 语言切换 hook
├── LanguageSwitcher.tsx   # 语言切换组件
└── locales/
    ├── en.json           # 英文翻译
    └── zh-CN.json        # 中文翻译
```

## GitHub 同步策略

### 风险分析

当你从上游 GitHub 拉取更新时，以下文件可能被覆盖：

1. `ui/package.json` - 依赖变更
2. `ui/src/main.tsx` - 入口文件变更
3. `ui/src/components/Sidebar.tsx` - 侧边栏修改
4. `ui/src/**/*.{ts,tsx}` - 任何 UI 组件

### 保护措施

#### 1. 关键文件锁定清单

以下文件包含中文支持的核心代码，同步时需要手动合并：

- `ui/src/i18n/index.ts` - i18n 配置
- `ui/src/i18n/LanguageSwitcher.tsx` - 语言切换器
- `ui/src/i18n/useLanguageSwitcher.ts` - 切换 hook
- `ui/src/i18n/locales/zh-CN.json` - **中文翻译（最重要）**

#### 2. 同步后检查清单

```bash
# 检查 i18n 目录是否完整
ls -la ui/src/i18n/

# 检查语言文件
cat ui/src/i18n/locales/zh-CN.json | head -20

# 验证依赖
grep -E "i18next|react-i18next" ui/package.json

# 验证 main.tsx 引入
grep "i18n" ui/src/main.tsx
```

#### 3. 如果 main.tsx 被覆盖

重新添加 import：

```tsx
// 在 ui/src/main.tsx 文件末尾添加：
import "./i18n";
```

#### 4. 如果 Sidebar.tsx 被覆盖

重新添加 LanguageSwitcher：

```tsx
// 导入
import { LanguageSwitcher } from "@/i18n/LanguageSwitcher";
import { Globe } from "lucide-react";

// 在 Company Section 末尾添加：
<div className="flex items-center gap-2 px-3 py-2 border-t border-border mt-2">
  <Globe className="w-4 h-4 text-muted-foreground" />
  <LanguageSwitcher />
</div>
```

## 开发工作流

### 添加新翻译

1. 在 `zh-CN.json` 中添加 key
2. 使用 `t('key.path')` 在组件中调用

示例：

```tsx
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t } = useTranslation();
  return <h1>{t('dashboard.title')}</h1>;
}
```

### 批量替换建议

如果需要将现有英文 UI 批量中文化，建议：

1. 使用 VS Code 多文件搜索替换
2. 将硬编码字符串提取为 `t()` 调用
3. 逐步完善 `zh-CN.json`

## 备份建议

建议将以下文件加入 Git 忽略或单独备份：

- `ui/src/i18n/locales/zh-CN.json` - 核心翻译文件

可以将其复制到项目根目录或外部位置作为备份。

## 自动化脚本（可选）

如果需要频繁同步，可创建 `scripts/sync-i18n.sh`：

```bash
#!/bin/bash
# 备份中文翻译
cp ui/src/i18n/locales/zh-CN.j

*[truncated — see source for full prompt]*