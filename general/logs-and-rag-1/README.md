# Logs And Rag

> ## Logs and outputs (Electron-friendly storage)

Agent and workflow **outputs** are stored in the `executions` table (`output` column). **Run logs** (

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Logs, outputs, and RAG

## Logs and outputs (Electron-friendly storage)

Agent and workflow **outputs** are stored in the `executions` table (`output` column). **Run logs** (per-step or streaming logs) are stored in the `run_logs` table.

**Database choice for Electron:** We use **SQLite** for both. SQLite is the standard choice for desktop apps:

- **Single file** – no separate server; bundles with the app.
- **No setup** – works out of the box in Electron (e.g. via `better-sqlite3`).
- **ACID** – safe for concurrent writes and app restarts.
- **Portable** – the `.data/agentron.sqlite` file can be backed up or moved.

Alternatives like **LevelDB** (key-value, good for append-heavy logs) are also easy to bundle with Electron, but SQLite keeps one database for runs, logs, and the rest of the app, which simplifies backups and tooling.

**APIs:**

- `PATCH /api/runs/{id}` – set `status`, `output`, `finishedAt` when a run completes.
- `GET /api/runs/{id}/logs` – list log entries for a run.
- `POST /api/runs/{id}/logs` – append log entries (e.g. from the executor).

---

## RAG (retrieval-augmented generation)

RAG is supported at two levels:

- **Per-agent** – a collection scoped to one agent (`scope: "agent"`, `agentId` set).
- **Deployment-wide** – a shared collection (`scope: "deployment"`, `agentId` null).

### Embedding endpoints (Settings)

Configure embedding endpoints once in **Settings → Embedding** (`/api/rag/embedding-providers`). Supported types:

- **Local (Ollama)** – base URL (e.g. `http://localhost:11434`), no API key. Use with models such as `nomic-embed-text`, `all-minilm`.
- **OpenAI** – API key (or ref), optional endpoint override.
- **OpenRouter** – API key.
- **Hugging Face** – API key for inference API.
- **Custom HTTP** – base URL and optional API key for OpenAI-compatible `/embeddings` endpoints.

Then in **Knowledge**, when creating an **encoding config**, you choose one of these embedding providers and the **model** (and dimensions). Encodin

*[truncated — see source for full prompt]*