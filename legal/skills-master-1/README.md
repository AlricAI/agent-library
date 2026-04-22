# SKILLS MASTER

> > 全仓库技能选型单一参考：统一呈现两来源、Baoyu 全表归类与使用场景，并索引各管线技能文档。各管线技能列表与安装方式见各管线 README 与 CLAWHUB-SKILLS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 总技能文档（ClawHub + skills.sh + Baoyu 归类）

> 全仓库技能选型单一参考：统一呈现两来源、Baoyu 全表归类与使用场景，并索引各管线技能文档。各管线技能列表与安装方式见各管线 README 与 CLAWHUB-SKILLS.md（见 §3），本文档做汇总与索引。

## 1. 技能来源与选型

| 来源 | 搜索方式 | 安装命令 | 选型约定 |
|------|----------|----------|----------|
| **ClawHub** | [clawhub.ai/skills](https://clawhub.ai/skills)，按渠道搜如 `xiaohongshu`、`zhihu`、`toutiao` | `clawhub install <slug>` | **优先**选用；各管线见对应 CLAWHUB-SKILLS.md |
| **skills.sh** | [skills.sh](https://skills.sh/)，如 `?q=jimliu`、`?q=baoyu`、`?q=xiaohongshu` | `npx skills add <owner/repo> --skill <技能名>` | ClawHub 未覆盖时**后补**；Baoyu 完整列表见下节 |

- 安装后技能目录名需与 openclaw 配置中 `agents.list[].skills` 一致。
- **勿在 TOOLS.md 存凭证。**

### 1.1 SkillHub 国内镜像（可选）

通过 SkillHub 国内镜像加速安装，下载速度更快更稳定。

**第一步：安装 SkillHub CLI**

```bash
curl -fsSL https://skillhub-1251783334.cos.ap-guangzhou.myqcloud.com/install/install.sh | bash
```

**第二步：安装技能**

```bash
skillhub install <slug>
```

其中 `<slug>` 与 ClawHub 技能名一致（如 `self-improving-agent`、`xiaohongshu-mcp` 等）。安装后技能目录名同样需与 openclaw 配置中 `agents.list[].skills` 一致。

### 1.2 OpenClaw 技能安装目录

OpenClaw 的技能（Skills）安装目录取决于当前环境：

| 类型 | 路径 |
|------|------|
| **全局技能** | `~/.openclaw/skills/` |
| **工作区技能** | `<workspace>/.openclaw/skills/` |

示例：若当前工作区为 `workspace-openclaw-assistant`（路径 `/root/.openclaw/workspace-openclaw-assistant`），则该工作区内的技能目录为：

```
/root/.openclaw/workspace-openclaw-assistant/.openclaw/skills/
```

**确认本机路径**：可在本机执行以下命令查看实际配置：

```bash
openclaw status
```

或查看配置中的技能相关项：

```bash
cat ~/.openclaw/openclaw.json | grep skills
```

安装或复制技能时，请放入上述对应目录，且子目录名与配置中 `agents.list[].skills` 一致。

### 1.3 npx skills 与 OpenClaw 技能目录一致

**问题**：OpenClaw 从 [§1.2](#12-openclaw-技能安装目录) 所述目录（全局 `~/.openclaw/skills/` 或工作区 `<workspace>/.openclaw/skills/`）加载技能；`npx skills add` 默认安装到 **`./.agent/skills/`** 或 **`~/.agent/skills/`**，二者不一致，OpenClaw 无法直接使用 npx 安装的技能。

**解决办法（任选其一）：**

1. **优先用 ClawHub / SkillHub 安装**  
   使用 `clawhub install <slug>` 或 [SkillHub 国内镜像](#11-skillhub-国内镜像可选) 的 `skillhub install <slug>`，会安装到 OpenClaw 使用的技能目

*[truncated — see source for full prompt]*