---
name: SURREALDB EMBEDDED
description: ## Descripción

Este proyecto ahora soporta **SurrealDB embebido** usando RocksDB como backend de almacenamiento, eliminando la necesidad de un servid
model: claude-sonnet-4-5
---
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
4. Copia las shared libraries necesarias al directorio `build/`

### Compilar solo surrealdb-embedded

```bash
make surrealdb-embedded
```

## Estructura de Archivos

```
~/www/MCP/remembrances-mcp/
├── internal/storage/
│   ├── surrealdb.go                    # Lógica principal con soporte dual
│   ├── surrealdb_query_helper.go      # Helpers para queries en ambos backends
│   ├── surrealdb_vectors.go           # Operaciones de vectores
│   ├── surrealdb_facts.go             # Operaciones de facts
│   ├── surrealdb_documents.go         # Operaciones de documentos
│   ├── surrealdb_entities.go          # Operaciones de entidades y grafos
│   └── surrealdb_stats.go             # Estadísticas
├── build/
│   ├── remembrances-mcp               # Binario principal
│   ├── libsurrealdb_embedded_rs.so    # Librería SurrealDB embedded
│   └── lib*.so                        # Otras shared libraries (llama.cpp)
└── go.mod                             # Dependencias actualizadas
```

## Implementación Técnica

### Backend Dual

El `SurrealDBStorage` ahora mantiene dos backends:

```go
type SurrealDBStorage struct {
    db         *surrealdb.DB        // Backend remoto (SDK oficial)
    embeddedDB *embedded.DB         // Backend embedded (nueva implementación)
    config     *ConnectionConfig
    useEmbedded bool                // Flag para determinar qué backend usar
}
```

### Métodos Helper

Se han creado métodos helper que abstraen las diferencias entre backends:

- `query(ctx, query, params)` - Ejecuta queries en el backend apropiado
- `create(ctx, resource, data)` - Crea registros
- `update(ctx, resource, data)` - Actualiza registros
- `delete(ctx, resource)` - Elimina registros

### Conversión de Resultados

El método `queryEmbedded` convierte los resultados de la librería embedded al formato esperado por el código existente:

```go
type QueryResult struct {
    Status string                   `json:"status"`
    Time   string                   `json:"time,omitempty"`
    Result []map[string]interface{} `json:"result"`
}
```

## Ventajas del Modo Embedded

1. **Sin dependencias externas**: No requiere servidor SurrealDB separado
2. **Mejor rendimiento**: Acceso directo a RocksDB sin overhead de red
3. **Portabilidad**: Un solo binario con todas las dependencias
4. **Desarrollo local**: Más fácil de configurar para desarrollo
5. **Persistencia**: Datos almacenados en disco usando RocksDB

## Testing

Para probar el modo embedded:

```bash
# Limpiar cualquier base de datos previa
rm -rf ./data/remembrances.db

# Ejecutar con modo embedded
./build/remembrances-mcp --db-path ./data/remembrances.db

# Verificar los logs para confirmar:
# "Connecting to embedded SurrealDB at ./data/remembrances.db"
# "Successfully connected to embedded SurrealDB"
```

## Troubleshooting

### Error: "libsurrealdb_embedded_rs.so not found"

Asegúrate de que la librería compartida esté en el PATH o en el mismo directorio que el binario:

```bash
# Opción 1: Añadir al PATH
export LD_LIBRARY_PATH=~/www/MCP/Remembrances/surrealdb-embedded:$LD_LIBRARY_PATH

# Opción 2: Copiar al directorio build (ya se hace automáticamente con make build)
cp ~/www/MCP/Remembrances/surrealdb-embedded/libsurrealdb_embedded_rs.so ./build/
```

### Error de compilación con CGO

Verifica que las variables CGO estén configuradas correctamente:

```bash
# Ejecutar desde el Makefile
make build

# O configurar manualmente
export CGO_ENABLED=1
export CGO_LDFLAGS="-L~/www/MCP/Remembrances/surrealdb-embedded -lsurrealdb_embedded_rs"
```

## Compatibilidad

- ✅ Todas las operaciones de storage (vectors, facts, documents, entities, stats)
- ✅ Queries SurrealQL estándar
- ✅ Migraciones de esquema (con soporte completo para ambos backends)
- ✅ Transacciones y consistencia
- ✅ Inicialización automática de esquema en modo embedded
- ✅ Tracking de versiones de migración

## Migraciones de Esquema

El sistema de migraciones funciona de manera transparente con ambos backends:

### Modo Remoto
- Usa el sistema de migraciones estructurado con clases `Migration`
- Ejecuta migraciones a través del SDK oficial de SurrealDB
- Soporte completo para verificación de esquema existente

### Modo Embedded
- Ejecuta migraciones mediante SurrealQL directo
- Utiliza el método `applyMigrationEmbedded()` que genera las mismas estructuras
- Detección automática de elementos ya existentes
- Migraciones V3, V4, V5 son no-op porque V1 ya incluye todas las mejoras

### Versiones de Migración

1. **V1**: Schema inicial completo (tablas: kv_memories, vector_memories, knowledge_base, entities)
2. **V2**: Tabla user_stats para estadísticas
3. **V3**: Correcciones de tipos en user_stats (aplicado en V1 para embedded)
4. **V4**: Campos user_id en todas las tablas (incluido en V1 para embedded)
5. **V5**: Metadata/properties flexibles (incluido en V1 para embedded)

## Referencias

- [surrealdb-embedded](https://github.com/madeindigio/surrealdb-embedded-golang) - Librería Rust para SurrealDB embedded
- [SurrealDB Official](https://surrealdb.com/) - Documentación oficial de SurrealDB