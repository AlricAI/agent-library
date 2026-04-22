# Dependency Inventory

> This inventory compares the legacy flat `requirements.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dependency Inventory and Role Separation

This inventory compares the legacy flat `requirements.txt` package list against the current Python import graph under `src/` and maps each dependency to a clearer role.

## Survey method

- Parsed direct Python imports in `src/`.
- Compared imported top-level modules to the packages previously listed in the root `requirements.txt`.
- Kept runtime packages only where there is a verifiable import or where the package is required to support declared runtime configuration loading.

## Required runtime

These packages are imported by the canonical runtime path and are now kept in `requirements/base.txt` and `requirements/runtime.txt`.

| Package | Evidence from `src/` | Role |
| --- | --- | --- |
| `fastapi` | API / WebSocket ingress in `src/backend/main.py` | HTTP + WebSocket ingress |
| `uvicorn` | Runtime launcher imports in `src/backend/main.py` | ASGI serving |
| `pydantic` | Envelope, entropy, and model schemas across `src/backend/genesis_core/` | Schema validation |
| `pydantic-settings` | `src/backend/core/config.py` | Environment-driven config |
| `python-dotenv` | Required by `SettingsConfigDict(env_file=".env")` local env loading path | Local `.env` support |
| `requests` | Marketing/search adapters | Sync HTTP client |
| `httpx` | Auth/provider and service HTTP clients | Async/sync HTTP client |
| `itsdangerous` | Session/auth signing | Signing primitives |
| `pyzmq` | `src/backend/genesis_core/bus/tachyon.py` | Internal ZeroMQ Tachyon transport |
| `websockets` | `src/backend/genesis_core/bus/tachyon.py` | External bridge client/server support |
| `uvloop` | Runtime event loop optimization | Event loop acceleration |
| `msgpack` | Bus serialization in `src/backend/genesis_core/bus/base.py` | Canonical binary codec |
| `orjson` | Bus serialization in `src/backend/genesis_core/bus/base.py` | Fast JSON codec |
| `numpy` | Presentation / visual processing paths | Numeric runtime utility |

## Optional ML / visual depen

*[truncated — see source for full prompt]*