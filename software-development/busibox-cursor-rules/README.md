# Busibox Cursor Rules

> Busibox Cursor Rules # Overview Busibox is a local LLM infrastructure platform running on Docker or Proxmox LXC containers.

## Tags
`postgres` `redis` `docker` `claude`

## System Prompt
# Busibox Cursor Rules

## Overview

Busibox is a local LLM infrastructure platform running on Docker or Proxmox LXC containers.
See `CLAUDE.md` for full project documentation.

## ⚠️ CRITICAL: Service Operations

**NEVER run `docker compose`, `docker`, or `ansible-playbook` commands directly.**

```bash
# ❌ WRONG - bypasses secrets injection
docker compose up -d authz-api
docker restart prod-authz-api
ansible-playbook -i inventory/docker docker.yml --tags authz

# ✅ CORRECT for AI agents - use make with vault password
make install SERVICE=authz
make manage SERVICE=authz ACTION=restart
```

**Why**: Secrets are injected from Ansible Vault at runtime. Direct commands skip this and cause authentication failures.

**Vault password**: Most `make` targets require `ANSIBLE_VAULT_PASSWORD` env var or a vault password file (`~/.busibox-vault-pass-*`). If neither is available, ask the user for the vault password. Prefer `mcp-admin` MCP tools when available — they handle SSH and targeting.

**Humans use the Busibox CLI** (`busibox`), not `make` targets. The CLI handles vault decryption interactively.

**Quick Reference**:
- Deploy: `make install SERVICE=authz`
- Restart: `make manage SERVICE=authz ACTION=restart`
- Logs: `make manage SERVICE=authz ACTION=logs`
- Status: `make manage SERVICE=authz ACTION=status`
- Redeploy: `make manage SERVICE=authz ACTION=redeploy`
- Rebuild manager: `make build-manager`
- Skip manager: `make install SERVICE=authz USE_MANAGER=0`

See `.cursor/rules/010-make-commands.md` for complete reference and `docs/developers/reference/mcp-and-make-internals.md` for vault password flow.

## Critical: Organization Rules

**ALWAYS** follow these rules when creating or moving files:

### Documentation Organization

Read: `.cursor/rules/001-documentation-organization.md`

**Quick Reference (organized by audience):**
- Deployment/config/operations → `docs/administrators/`
- Architecture/API guides/reference → `docs/developers/`
- End-user platform guides → `d

*[truncated — see source for full prompt]*