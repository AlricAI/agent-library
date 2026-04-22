# CONFIGURATION

> Sistema de configuración dinámica para habilitar/deshabilitar componentes de memoria y RAG en tiempo de ejecución.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dynamic Configuration System

Sistema de configuración dinámica para habilitar/deshabilitar componentes de memoria y RAG en tiempo de ejecución.

## Características Principales

### 1. **Control Granular de Memoria**

Puedes habilitar/deshabilitar tipos específicos de memoria:

- **Short-term**: Buffer de conversación reciente
- **Semantic**: Extracción de hechos semánticos
- **Episodic**: Resúmenes episódicos temporales
- **Profile**: Construcción de perfil de usuario
- **Procedural**: Detección de patrones de interacción

### 2. **Control de RAG por Namespace**

- Habilitar/deshabilitar RAG completamente
- Especificar namespaces específicos a consultar
- Control de cantidad de documentos a recuperar (top_k)

### 3. **Configuración por Sesión**

- Configuraciones persistidas en base de datos
- Asociadas a `session_id`
- Cada sesión puede tener configuración diferente

### 4. **Degradación Graceful**

- Servicios retornan `None` si no están disponibles
- Warnings en lugar de errores
- Chat funciona sin memoria o RAG si están deshabilitados

## Variables de Entorno

### RAG

```bash
# Habilitar/deshabilitar RAG globalmente
ENABLE_RAG=true  # default: true

# Configuración de Pinecone (requerida si RAG está habilitado)
PINECONE_API_KEY=your_key
PINECONE_INDEX_NAME=index_name
PINECONE_CLOUD=aws
PINECONE_REGION=us-east-1
```

### Memoria

```bash
# Control global de memoria long-term
ENABLE_LONG_TERM=true  # default: true

# Tipos específicos de memoria
ENABLE_SEMANTIC_MEMORY=true  # default: true
ENABLE_EPISODIC_MEMORY=true  # default: true
ENABLE_PROFILE_MEMORY=true   # default: true
ENABLE_PROCEDURAL_MEMORY=true  # default: true

# Estrategia de almacenamiento semántico
SEMANTIC_STORAGE=hybrid  # mysql | pinecone | hybrid (default: hybrid)
```

## Referencia de API

Para documentación detallada de los endpoints de configuración y ejemplos de uso, consulta [API.md](API.md).

Los endpoints relevantes son:
- `GET /config/status`: Estado del sistema
- `GET /config/sess

*[truncated — see source for full prompt]*