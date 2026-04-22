# SURREALDB EMBEDDED

> ## Descripción

Este proyecto ahora soporta **SurrealDB embebido** usando RocksDB como backend de almacenamiento, eliminando la necesidad de un servid

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SurrealDB Embedded Integration

## Descripción

Este proyecto ahora soporta **SurrealDB embebido** usando RocksDB como backend de almacenamiento, eliminando la necesidad de un servidor SurrealDB externo cuando se ejecuta en modo local.

## Características

- **Modo Embedded**: Almacenamiento local usando RocksDB a través de la librería `surrealdb-embedded`
- **Modo Remoto**: Conexión a un servidor SurrealDB externo (comportamiento anterior)
- **Prioridad automática**: Si se especifica `db-path`, se usa el modo embedded; si se especifica `surrealdb-url`, se usa el modo remoto

## Configuración

### Usando variables de entorno

```bash
# Modo Embedded (prioridad)
export DB_PATH="./data/remembrances.db"
export SURREALDB_NAMESPACE="test"
export SURREALDB_DATABASE="test"

# Modo Remoto
export SURREALDB_URL="ws://localhost:8000"
export SURREALDB_USER="root"
export SURREALDB_PASS="root"
export SURREALDB_NAMESPACE="test"
export SURREALDB_DATABASE="test"
```

### Usando flags de línea de comandos

```bash
# Modo Embedded
./remembrances-mcp --db-path ./data/remembrances.db

# Modo Remoto
./remembrances-mcp --surrealdb-url ws://localhost:8000 \
                   --surrealdb-user root \
                   --surrealdb-pass root
```

### Usando archivo de configuración YAML

```yaml
# config.yaml
db-path: "./data/remembrances.db"  # Modo Embedded
# surrealdb-url: "ws://localhost:8000"  # Modo Remoto
surrealdb-namespace: "test"
surrealdb-database: "test"
```

## Prioridad de Configuración

1. **Modo Embedded**: Si `db-path` está configurado y `surrealdb-url` NO está configurado
2. **Modo Remoto**: Si `surrealdb-url` está configurado

## Compilación

El proyecto ahora requiere la librería `surrealdb-embedded` que debe estar compilada en:
```
~/www/MCP/Remembrances/surrealdb-embedded
```

### Compilar el proyecto

```bash
make build
```

Este comando:
1. Compila llama.cpp (para embeddings GGUF)
2. Verifica que surrealdb-embedded esté compilado
3. Compila el binario principal
4. C

*[truncated — see source for full prompt]*