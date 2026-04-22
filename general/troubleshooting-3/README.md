# Troubleshooting

> Step-by-step solutions for every known issue.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting

Step-by-step solutions for every known issue. Each problem includes the symptom, cause, and fix.

> **Quick diagnosis:** Use Ctrl+F (Cmd+F on Mac) to search for the error message you're seeing.
> **Don't know a term?** Check the [Glossary](GLOSSARY.md).

---

## How to Diagnose Problems

Before looking for specific errors, try these diagnostic steps:

```bash
# 1. Check your tools are installed and recent enough
node --version    # Need v18+
bun --version     # Any version
git --version     # Any version

# 2. Check you're in the right directory
pwd               # Should end with /bnb-chain-toolkit

# 3. Check dependencies are installed
ls node_modules/  # Should not be empty

# 4. Check the build ran successfully
ls public/index.json  # Should exist and not be empty
```

If any of these fail, the fix is in the relevant section below.

---

## Installation Issues

### `bun: command not found`

**Cause:** bun is not installed.

**Fix:**
```bash
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc  # or restart your terminal
```

### `bun install` fails with permission errors

**Fix:** Don't use `sudo`. Instead:
```bash
# Remove existing node_modules
rm -rf node_modules

# Try again
bun install
```

### Node.js version too old

**Symptom:** Errors about unsupported syntax or missing features.

**Fix:**
```bash
# Check your version
node --version

# If below 18, update via nvm:
nvm install 18
nvm use 18
```

---

## MCP Server Issues

### Server won't start

**Checklist:**
1. Are you in the right directory? (`cd mcp-servers/<server-name>`)
2. Did you run `bun install`?
3. Are required environment variables set?
4. Is the port already in use? (`lsof -i :3000`)

**Quick fix:**
```bash
cd mcp-servers/<server-name>
rm -rf node_modules
bun install
bun start
```

### Claude Desktop doesn't show MCP tools

**Checklist:**
1. Is the server running? Check with `ps aux | grep mcp`
2. Is `claude_desktop_config.json` valid JSON? Use `jq . claude_desktop_con

*[truncated — see source for full prompt]*