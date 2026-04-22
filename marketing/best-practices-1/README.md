# Best Practices

> Practical patterns for deploying Remarq, configuring content selectors, integrating AI agents, running multi-reviewer workflows, and managing document lifecycles.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Best Practices Guide

Practical patterns for deploying Remarq, configuring content selectors, integrating AI agents, running multi-reviewer workflows, and managing document lifecycles.

---

## Table of Contents

1. [Deployment](#deployment)
2. [Content Selector Strategies](#content-selector-strategies)
3. [Agent Integration Patterns](#agent-integration-patterns)
4. [Multi-Reviewer Workflows](#multi-reviewer-workflows)
5. [Document Lifecycle Management](#document-lifecycle-management)

---

## Deployment

### Solo use: npx

For individual users or quick evaluation, run the server directly with npx. You'll need a running PostgreSQL instance.

```bash
# Start with an existing Postgres
export DATABASE_URL=postgres://user:pass@localhost:5432/remarq
npx @csalvato/remarq-server
```

Or install and run manually:

```bash
npm install --prefix server
DATABASE_URL=postgres://user:pass@localhost:5432/remarq node server/index.js
```

This is ideal for local development or solo pair-writing with your AI agent.

### Team / production: Docker Compose

For teams or production deployments, Docker Compose bundles Postgres and the Remarq server together.

```bash
git clone https://github.com/cass-clearly/remarq.git
cd remarq
echo "POSTGRES_PASSWORD=a-strong-random-password" > .env
docker compose -f docker-compose.remarq.yml up --build -d
```

The `.env` file is read automatically by Docker Compose. Use a strong, random password — not `remarq`.

### Environment variables

| Variable            | Default                                    | Description                                 |
| ------------------- | ------------------------------------------ | ------------------------------------------- |
| `DATABASE_URL`      | `postgresql://postgres@localhost/postgres` | PostgreSQL connection string                |
| `PORT`              | `3333`                                     | Port the server listens on                  |
| `POSTGRES_PASSWORD` | _(required in Docker)_               

*[truncated — see source for full prompt]*