# Db

> Genonaut uses PostgreSQL with a multi-database architecture supporting development, demo, and test environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Database Documentation

Genonaut uses PostgreSQL with a multi-database architecture supporting development, demo, and test environments.

## Database Architecture

### Multi-Database Environment Support

| Environment | Database Name | Purpose | Access Pattern |
|-------------|---------------|---------|----------------|
| **Development** | `genonaut` | Main development database | Default for local development |
| **Demo** | `genonaut_demo` | Demo data and testing | Stable demo environment |
| **Test** | `genonaut_test` | Automated testing | Isolated test environment |

### Three-Tier User System

Genonaut uses a three-tier database user system for security:

- **Admin User** (`genonaut_admin`): Full privileges for database initialization, schema creation, and administration
- **Read/Write User** (`genonaut_rw`): Can insert, update, and delete data but cannot modify database structure
- **Read-Only User** (`genonaut_ro`): Can only read data, useful for reporting and analytics

## Environment Variables

### Required Variables

| Variable            | Description                                      | Example               | Default |
|---------------------|--------------------------------------------------|-----------------------|---------|
| `DB_PASSWORD_ADMIN` | Admin user password (full database privileges)   | `your_admin_password` | None    |
| `DB_PASSWORD_RW`    | Read/write user password (data operations only)  | `your_rw_password`    | None    |
| `DB_PASSWORD_RO`    | Read-only user password (select operations only) | `your_ro_password`    | None    |

### Optional Variables

| Variable                  | Description                                                     | Example                                                          | Default     |
|---------------------------|-----------------------------------------------------------------|------------------------------------------------------------------|-------------|
| `DATABASE_URL`            | Com

*[truncated — see source for full prompt]*