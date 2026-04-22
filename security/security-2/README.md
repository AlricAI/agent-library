# SECURITY

> > Authentication security model for the ERC-8004 agent toolkit components.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security — ERC-8004 Agent Creator

> Authentication security model for the ERC-8004 agent toolkit components.

## Overview

ERC-8004 Agent Creator provides three components that handle cryptographic key material:

| Component | Auth Methods | Key Storage |
|-----------|-------------|-------------|
| **VS Code Extension** | Private key, Keystore import | VS Code SecretStorage (OS-level encrypted) |
| **MCP Server** | `PRIVATE_KEY` env var, `KEYSTORE_FILE` + `KEYSTORE_PASSWORD` env vars | Environment variables (runtime only) |
| **CLI** | Encrypted keystore in config, `--key` flag (deprecated), `ERC8004_PRIVATE_KEY` env var | `~/.erc8004/config.json` (0o600 permissions) |

---

## Wallet Authentication Methods

### 1. Encrypted Keystore (Recommended)

All three components support [Ethereum V3 Keystore](https://ethereum.org/en/developers/docs/data-structures-and-encoding/#keystore) files — the industry standard for encrypted key storage.

- **Encryption**: scrypt KDF + AES-128-CTR cipher
- **At rest**: Private key is encrypted; password is required to decrypt
- **In transit**: Keystore JSON can be safely copied between machines (password-protected)

**Security properties:**
- Private key never stored in plaintext on disk
- Password is used transiently (only during decrypt) and then discarded
- Keystore files use `chmod 600` (owner read/write only)

### 2. Raw Private Key (Legacy / CI)

Supported for backward compatibility and CI/CD pipelines.

- **VS Code**: Stored in SecretStorage (encrypted by the OS keyring)
- **MCP Server**: Passed via `PRIVATE_KEY` environment variable (runtime only)
- **CLI**: Deprecated `--key` flag prints a warning; old plaintext config is auto-migrated

### 3. Environment Variables (CI/CD)

For automated pipelines where interactive password entry is not possible:

- `PRIVATE_KEY` — hex-encoded private key with `0x` prefix
- `KEYSTORE_FILE` + `KEYSTORE_PASSWORD` — path to keystore + password
- `ERC8004_PRIVATE_KEY` (CLI only) — overrides stor

*[truncated — see source for full prompt]*