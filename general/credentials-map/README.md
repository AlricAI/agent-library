# Credentials Map

> **Last Updated**: 2026-03-21
**RULE**: This file stores PATHS to credentials, NEVER the values themselves. Values stay in vault files only.
**CHAIN NO

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CREDENTIALS MAP — WHERE KEYS LIVE (PATHS ONLY)

**Last Updated**: 2026-03-21
**RULE**: This file stores PATHS to credentials, NEVER the values themselves. Values stay in vault files only.
**CHAIN NOTE**: any on-chain wallet rows below are historical address references only; do not infer current multisig status or current LLC operating doctrine from this file alone.

## Vaults

| Vault | Path | Contains |
|-------|------|----------|
| Runtime .env | C:\ANTIGRAVITY\.env | Active runtime secrets (gitignored) |
| Master vault | briefings/MASTER-UNIVERSAL-ENV-TROLLZ1004.env | All keys (gitignored) |
| Fallback vault | E:\WHEN OPUS FORGETS\ | Emergency backup (never push) |
| Hidden local | C:\Users\joshl\.antigravity\master.env | Local copy |
| Cloud backup | OneDrive\...\MASTER-UNIVERSAL-ENV-TROLLZ1004.env | Cloud sync |
| Imported node/GCR bundle | C:\Users\joshl\OneDrive\Personal Vault-Sabretooth\GLOBALNODE-CREDENTIALS-2026-03-21.env | Separate holding file for imported node, GCR admin, and Codex service credentials |
| GitHub Secrets | Trollz1004/ANTIGRAVITY | 88 secrets |
| GitHub Variables | Trollz1004/ANTIGRAVITY | 58 readable vars |

## Claude / Anthropic

| Credential | Location |
|------------|----------|
| Claude Code OAuth | C:\Users\joshl\.claude\.credentials.json |
| Subscription | Max (rateLimitTier: default_claude_max_20x) |
| Admin Key | Vault file → ANTHROPIC_ADMIN_KEY |
| API Key | Vault file → ANTHROPIC_API_KEY |

## Google / Gemini

| Credential | Location |
|------------|----------|
| Gemini API Key | .env → GEMINI_API_KEY (rotate if exposed) |
| GCP Service Account | E:\.claude\*.json |
| Imported GCR/Admin env bundle | C:\Users\joshl\OneDrive\Personal Vault-Sabretooth\GLOBALNODE-CREDENTIALS-2026-03-21.env |
| GCP Project | ai-collab4kids |

## Telegram Bot

| Credential | Location |
|------------|----------|
| Primary Bot | Sabretooth local OpenClaw config / local env only |
| Backup Bot | T5500 local OpenClaw config only |
| Bot Tokens | Local 

*[truncated — see source for full prompt]*