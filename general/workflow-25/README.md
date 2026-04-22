# WORKFLOW

> > 本文档描述 OMK 项目的全部工作流：从需求到交付的完整路径、各技能的运转逻辑、状态机流转规则，以及扩展指南。

---

## 目录

- [总览](#总览)
- [核心工作流：三段式开发链](#核心工作流三段式开发链)
  - [Stage 1 — `$deep-interview` 需求访

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# oh-my-kimi 工作流手册

> 本文档描述 OMK 项目的全部工作流：从需求到交付的完整路径、各技能的运转逻辑、状态机流转规则，以及扩展指南。

---

## 目录

- [总览](#总览)
- [核心工作流：三段式开发链](#核心工作流三段式开发链)
  - [Stage 1 — `$deep-interview` 需求访谈](#stage-1--deep-interview-需求访谈)
  - [Stage 2 — `$ralplan` 架构规划](#stage-2--ralplan-架构规划)
  - [Stage 3 — `$ralph` 持久执行](#stage-3--ralph-持久执行)
- [辅助工作流](#辅助工作流)
  - [`$analyze` 深度分析](#analyze-深度分析)
  - [`$code-review` 代码审查](#code-review-代码审查)
  - [`$build-fix` 构建修复](#build-fix-构建修复)
  - [`$plan` 轻量规划](#plan-轻量规划)
  - [`$note` 笔记记录](#note-笔记记录)
  - [`$team` 多智能体协作](#team-多智能体协作)
  - [`$cancel` 中断取消](#cancel-中断取消)
- [状态机](#状态机)
- [钩子协议](#钩子协议)
- [文件系统约定](#文件系统约定)
- [工作流扩展指南](#工作流扩展指南)

---

## 总览

OMK 以 **Kimi CLI 的 Hook 机制**为基础，在用户提示词提交时拦截 `$命令`，激活对应的 Skill 并注入结构化上下文，从而让 Kimi 遵循预定工作流自主完成任务。

```
用户输入 $command
      │
      ▼
 OMK Hook (handler.js)
      │  检测关键词
      ▼
 KeywordRegistry
      │  命中技能
      ▼
 State Manager         ←→  .omk/state/
      │  写入激活状态
      ▼
 SKILL.md 注入 Kimi 上下文
      │
      ▼
 Kimi 按工作流执行
```

---

## 核心工作流：三段式开发链

这是 OMK 的**规范开发路径**，适用于任何有一定复杂度的功能开发。

```
$deep-interview  ──▶  $ralplan  ──▶  $ralph
   [需求澄清]         [架构规划]      [执行交付]
```

---

### Stage 1 — `$deep-interview` 需求访谈

**目标**：在写任何一行代码之前，确保需求是清晰的、边界是对齐的。

**触发**：
```
$deep-interview "我想做一个用户认证系统"
```

**工作流**：

```
Phase 1: Intent Clarification（意图澄清）
  ├── 目标是什么？成功标准？
  ├── 终端用户是谁？
  └── 关键约束条件？

Phase 2: Deep Dive（深度追问）
  ├── 技术限制？现有依赖？
  ├── 不在范围内的是什么？
  └── 潜在风险？

Phase 3: Synthesis（综合输出）
  └── 输出 Context Snapshot
      保存至 .omk/context/{slug}-{timestamp}.md
```

**输出产物**：

```markdown
## Context Snapshot

**Task**: 用户认证系统
**Goal**: 支持邮箱+密码登录，含找回密码
**Scope**:
  - In: 注册、登录、找回密码
  - Out: OAuth 三方登录、多因素认证
**Constraints**: Node.js 20+，不依赖外部 Auth 服务
**Risks**: Token 安全性，暴力破解防护
**Next Steps**: $ralplan 进行架构设计
```

**状态**：
| 时机 | phase |
|------|-------|
| 启动 | `intent-first` |
| 完成 | `complete` |

**衔接**：完成后推荐直接执行 `$ralplan`。

---

### Stage 2 — `$ralplan` 架构规划

**目标**：在编码前输出一份经用户审批的 PRD，确保技术方案对齐。

**触发**：
``

*[truncated — see source for full prompt]*