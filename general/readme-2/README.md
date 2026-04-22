# README

> 本目录包含了 Sperax Agents 项目的所有脚本工具，经过重新组织和优化，使功能更加清晰，更容易维护。

## 📁 目录结构

```
scripts/
├── core/                    # 核心配置和模型
│   ├── constants.ts         

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scripts 目录结构说明

本目录包含了 Sperax Agents 项目的所有脚本工具，经过重新组织和优化，使功能更加清晰，更容易维护。

## 📁 目录结构

```
scripts/
├── core/                    # 核心配置和模型
│   ├── constants.ts         # 项目常量配置
│   └── model.ts            # AI 模型配置
├── utils/                   # 工具函数
│   ├── file.ts             # 文件操作工具
│   ├── common.ts           # 通用工具函数
│   └── logger.ts           # 自定义日志系统
├── parsers/                 # 解析器模块
│   └── agent-parser.ts     # Agent 文件解析器
├── processors/              # 处理器模块
│   ├── category-processor.ts # 分类处理器
│   └── i18n-processor.ts   # 国际化处理器
├── validators/              # 验证器模块
│   ├── agent-validator.ts  # Agent 验证器
│   └── language-validator.ts # 语言验证器
├── builders/                # 构建器模块
│   └── agent-builder.ts    # Agent 构建器
├── formatters/              # 格式化器模块
│   └── agent-formatter.ts  # Agent 格式化器
├── commands/                # 命令行工具
│   ├── build.ts            # 构建命令
│   ├── format.ts           # 格式化命令
│   ├── test.ts             # 测试命令
│   ├── test-locale.ts      # 本地化测试命令
│   ├── validate-language.ts # 语言验证命令
│   ├── update-awesome.ts   # 更新 README 命令
│   └── auto-submit.ts      # 自动提交命令
├── schema/                  # 数据结构定义
│   ├── agentMeta.ts        # Agent 元数据 Schema
│   └── llm.ts              # LLM 相关 Schema
└── README.md               # 本说明文件
```

## 🚀 主要功能模块

### 核心模块 (core/)

- **constants.ts**: 包含所有项目常量，如路径配置、分类列表、翻译字段选择器等
- **model.ts**: OpenAI 模型配置和初始化

### 工具模块 (utils/)

- **file.ts**: 文件操作相关工具函数，如文件读写、目录管理等
- **common.ts**: 通用工具函数，如字符串处理、数组操作等
- **logger.ts**: 自定义日志系统，提供结构化、彩色输出，支持进度条、统计信息等

### 解析器模块 (parsers/)

- **agent-parser.ts**: 解析 Agent 配置文件，提取 ID、语言代码和内容

### 处理器模块 (processors/)

- **category-processor.ts**: 使用 AI 自动为 Agent 分配分类
- **i18n-processor.ts**: 处理多语言翻译，支持 OpenAI API 调用

### 验证器模块 (validators/)

- **agent-validator.ts**: 验证 Agent 配置格式和数据完整性
- **language-validator.ts**: 使用 @yutengjing/eld 库验证翻译文件的语言准确性

### 构建器模块 (builders/)

- **agent-builder.ts**: 构建所有语言版本的 Agent 文件和索引

### 格式化器模块 (formatters/)

- **agent-formatter

*[truncated — see source for full prompt]*