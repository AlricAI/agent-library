# Work Order Submission Guide

> Standard preferences for submitting work orders via the AgentGate API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Work Order Submission Guide

Standard preferences for submitting work orders via the AgentGate API.

## Standard Submission Template

```bash
curl -X POST http://localhost:3001/api/v1/work-orders \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <your-api-key>" \
  -d '{
    "taskPrompt": "<task description>",
    "workspaceSource": {
      "type": "github",
      "repo": "fl-sean03/AgentGate"
    },
    "agentType": "claude-code-subscription",
    "maxIterations": 10,
    "harness": {
      "verification": {
        "waitForCI": true,
        "skipLevels": []
      }
    }
  }'
```

## Preferred Settings

| Setting | Value | Reason |
|---------|-------|--------|
| `workspaceSource.type` | `github` | Clone from GitHub, create PRs |
| `workspaceSource.owner` | `fl-sean03` | Default GitHub owner |
| `workspaceSource.repo` | `AgentGate` | Target repository |
| `agentType` | `claude-code-subscription` | Uses Claude Code with subscription |
| `maxIterations` | `10` | Enough iterations for complex tasks |
| `waitForCI` | `true` | Wait for GitHub Actions to pass |
| `skipLevels` | `[]` | Run ALL verification levels (L0-L3) |

---

## All Available Types

### Workspace Source Types

| Type | Description | Required Fields |
|------|-------------|-----------------|
| `local` | Use existing local directory | `path` |
| `github` | Clone existing GitHub repo | `owner`, `repo`, `branch?` |
| `github-new` | Create new GitHub repo | `owner`, `repoName`, `private?`, `template?` |
| `git` | Clone from git URL (deprecated) | `url`, `branch?` |
| `fresh` | Create new local workspace (deprecated) | `destPath`, `template?` |

**Example - Local:**
```json
{
  "type": "local",
  "path": "/home/user/my-project"
}
```

**Example - GitHub (preferred):**
```json
{
  "type": "github",
  "repo": "fl-sean03/AgentGate",
  "branch": "main"
}
```

> **Note:** Due to a current API bug, use `repo: "owner/repo"` format instead of separate `owner` and `repo` fields. This will be fi

*[truncated — see source for full prompt]*