# Getting Started

> A step-by-step guide from zero to running.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started

A step-by-step guide from zero to running. No prior blockchain experience needed.

> **Estimated time:** 10-15 minutes for basic setup, 5 more for your first MCP server.

---

## Before You Start

### What You'll Need

You need three tools installed on your computer. If you already have them, skip ahead to [Step 1](#step-1-download-the-toolkit).

| Tool | What It Does | How to Check | Install Link |
|------|-------------|-------------|--------------|
| **Git** | Downloads the project | `git --version` → any version is fine | [git-scm.com](https://git-scm.com/) |
| **Node.js 18+** | Runs JavaScript code | `node --version` → should show v18 or higher | [nodejs.org](https://nodejs.org/) |
| **bun** | Fast package manager and runner | `bun --version` → any version is fine | [bun.sh](https://bun.sh/) |

<details>
<summary><b>How to install bun (MacOS / Linux / WSL)</b></summary>

Open your terminal and run:
```bash
curl -fsSL https://bun.sh/install | bash
```

Then restart your terminal (close and reopen it) so the `bun` command becomes available.

**Verify it worked:**
```bash
bun --version
# Should print something like 1.x.x
```

</details>

<details>
<summary><b>How to install bun on Windows</b></summary>

Open PowerShell and run:
```powershell
powershell -c "irm bun.sh/install.ps1 | iex"
```

Or if you have npm already: `npm install -g bun`

Then restart your terminal.

</details>

<details>
<summary><b>What if I don't want to install bun?</b></summary>

No problem — you can use `npm` or `yarn` instead. Anywhere this guide says `bun install`, use `npm install`. Anywhere it says `bun run build`, use `npm run build`. Everything works the same way.

</details>

### What You Won't Need (Yet)

You do **not** need:
- A crypto wallet (unless you want to execute on-chain transactions)
- Any cryptocurrency or tokens
- API keys (basic features work without them)
- Docker (optional, for deployment only)

---

## Step 1: Download the Toolkit

Open your termina

*[truncated — see source for full prompt]*