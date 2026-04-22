# Cycodgr Redesign Spec

> ## Overview - What We're Doing

**Redesigning cycodgr to match cycodmd's pattern:**

- **Remove** `repo` and `code` verbs
- **Add** content filter fla

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# cycodgr Redesign Spec: Verb-Based → Flag-Based (Symmetry with cycodmd)

## Overview - What We're Doing

**Redesigning cycodgr to match cycodmd's pattern:**

- **Remove** `repo` and `code` verbs
- **Add** content filter flags: `--contains`, `--file-contains`, `--repo-contains`, `--EXT-file-contains`
- **Add** positional repo patterns (like cycodmd's file patterns)
- **Keep** all existing filtering/output options
- **Create** single unified SearchCommand (default command)

**The Symmetry:**

| Tool | Positional Args | Content Filters | Result |
|------|----------------|-----------------|--------|
| **cycodmd** | File patterns (`**/*.cs`) | `--contains`, `--cs-file-contains` | Files with content |
| **cycodgr** | Repo patterns (`owner/repo`) | `--contains`, `--repo-contains`, `--cs-file-contains` | Repos/code with content |

---

## Option-by-Option Analysis

### Search Target Options

#### Positional Arguments

**CURRENT:**
```bash
cycodgr repo jwt auth              # Keywords for repo search
cycodgr code "AddJwtBearer"        # Keywords for code search
```
- Positional args = search keywords
- Verb determines if searching repos or code

**PROPOSED:**
```bash
cycodgr microsoft/vscode dotnet/aspire    # Repo patterns (where to search)
cycodgr @my-repos.txt                     # Repo list from file
cycodgr --contains "jwt"                   # No repos = search all of GitHub
```
- Positional args = repository patterns (where to search)
- Content flags determine what to search for

**CHANGE:** YES - Fundamental shift from keywords to repo patterns

---

#### --contains (NEW)

**CURRENT:** Doesn't exist

**PROPOSED:**
```bash
cycodgr --contains "jwt auth"                    # Search BOTH repo metadata AND code
cycodgr owner/repo --contains "authentication"   # Search both in specific repo
```
- Searches in: repo name, description, topics, README, AND code files
- Shows: Mixed results (repos + code matches)
- Default format: repos section, then code section

**CHANGE:** A

*[truncated — see source for full prompt]*