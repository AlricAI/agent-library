# Db Migrations

> **When to use:** Any schema or data change.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DB migrations (Alembic)
**When to use:** Any schema or data change.  
**Principle:** Forward-only in prod; rollbacks are for local/dev.

## SOP: Changing database schema 
1) Create, modify, or delete SQLAlchemy models.
- DO NOT DO: plan/create raw SQL to execute to make the changes.
2) Create revision: Autogen (ORM): Run the makefile goals to do `alembic revision --autogenerate -m "xyz"` and 
`alembic upgrade head` either all DBs at once, or 1 DB at a time. The makefile commands follow the pattern, `migrate-*`,
e.g. `migrate-demo`, and there is a `migrate-all` command. There are some comments written directly above those 
commands;  Bgive them a read as well.
- DO NOT DO: Manual (SQL): `alembic revision -m "xyz"`
3) Optional (Probably for humans only; agents can skip this): Review and edit the new script under 
`alembic/versions/*.py` (write `downgrade()` only for safe, local use).
4CI/CD: run migrations during deploy (if applicable); use one DB per env.

### Special considerations
Always start by syncing with main, then run `PYTHONPATH=. alembic heads` (or `alembic history --verbose | tail`) to 
confirm there is exactly one head and note its revision id. If more than one head appears, stop and reconcile before 
creating anything new.

Make sure your target database is on that same head with `alembic current` (or `alembic current -n <name>` for each DSN 
you maintain). Upgrade or downgrade until everything reports the single head revision.

Generate new migrations with Alembic’s CLI (`alembic revision --autogenerate -m "<message>"`). The tool automatically 
sets`down_revision` to the sole current head. Avoid hand-copying the template unless you have to; if you do, paste the 
revision id you saw from `alembic heads` into the `down_revision` field instead of reusing an older value.

After the new file is created, re-run `alembic heads`. You should again see only one head (the new revision). If you see 
two, the `down_revision` was wrong—fix it before proceeding.

Ru

*[truncated — see source for full prompt]*