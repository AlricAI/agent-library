# DISTRIBUTION GUIDE

> Esta guía te ayuda a crear paquetes de distribución de Remembrances-MCP con librerías optimizadas para diferentes GPUs.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Guía de Distribución de Binarios

Esta guía te ayuda a crear paquetes de distribución de Remembrances-MCP con librerías optimizadas para diferentes GPUs.

## Resumen Rápido

```bash
# 1. Compilar todas las variantes disponibles
make build-libs-all-variants

# 2. Empaquetar para distribución
make package-libs-all

# 3. Los paquetes están en dist/libs/
ls -lh dist/libs/
```

## Estructura de Paquetes

Cada paquete incluye:

```
llama-cpp-{variant}-{platform}-{arch}.tar.gz
├── libllama.so (o .dylib)
├── libggml.so
├── libggml-base.so
├── libggml-{variant}.so  ← Librería específica de GPU
└── BUILD_INFO.txt        ← Metadata de compilación
```

## Compilar para Distribución

### En Linux (Máquina con NVIDIA GPU)

```bash
# Compilar variantes Linux
make build-libs-cpu        # Para usuarios sin GPU
make build-libs-cuda       # Para usuarios con NVIDIA
make build-libs-openblas   # Para CPUs optimizados (opcional)

# Empaquetar
make package-libs-all
```

Genera:
- `llama-cpp-cpu-linux-x86_64.tar.gz` (5-10 MB)
- `llama-cpp-cuda-linux-x86_64.tar.gz` (50-100 MB)
- `llama-cpp-openblas-linux-x86_64.tar.gz` (5-10 MB)

### En Linux (Máquina con AMD GPU)

```bash
# Compilar variantes AMD
make build-libs-cpu
make build-libs-hipblas    # Para usuarios con AMD Radeon

# Empaquetar
make package-libs-all
```

Genera:
- `llama-cpp-cpu-linux-x86_64.tar.gz`
- `llama-cpp-hipblas-linux-x86_64.tar.gz` (50-100 MB)

### En macOS (Apple Silicon)

```bash
# Compilar variantes macOS
make build-libs-cpu
make build-libs-metal      # Para M1/M2/M3

# Empaquetar
make package-libs-all
```

Genera:
- `llama-cpp-cpu-darwin-arm64.tar.gz`
- `llama-cpp-metal-darwin-arm64.tar.gz`

## Instrucciones para Usuarios Finales

### Instalación con GPU NVIDIA

```bash
# 1. Descargar binario principal y librerías CUDA
wget https://github.com/tu-repo/releases/download/v1.0/remembrances-mcp-linux-amd64
wget https://github.com/tu-repo/releases/download/v1.0/llama-cpp-cuda-linux-x86_64.tar.gz

# 2. Extraer librerías
mk

*[truncated — see source for full prompt]*