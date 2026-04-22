# MULTI VARIANT BUILD

> Esta guía explica cómo compilar múltiples variantes de las librerías llama.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Compilación Multi-Variante de Librerías llama.cpp

Esta guía explica cómo compilar múltiples variantes de las librerías llama.cpp para diferentes GPUs y distribuirlas en formato binario.

## Índice

- [Visión General](#visión-general)
- [Estructura de Directorios](#estructura-de-directorios)
- [Compilar Variantes Individuales](#compilar-variantes-individuales)
- [Compilar Todas las Variantes](#compilar-todas-las-variantes)
- [Empaquetar para Distribución](#empaquetar-para-distribución)
- [Usar una Variante Específica](#usar-una-variante-específica)

## Visión General

El sistema de compilación multi-variante te permite:

1. **Compilar librerías para diferentes GPUs** sin interferir entre sí
2. **Organizar librerías en subdirectorios** separados por tipo
3. **Distribuir binarios** para diferentes plataformas
4. **Cambiar fácilmente** entre variantes sin recompilar

### Variantes Disponibles

| Variante | Plataforma | Descripción | Directorio |
|----------|-----------|-------------|-----------|
| `cpu` | Todas | CPU solamente (sin GPU) | `build/libs/cpu/` |
| `cuda` | Linux | NVIDIA CUDA (RTX, GTX, etc.) | `build/libs/cuda/` |
| `hipblas` | Linux | AMD ROCm (Radeon RX, MI) | `build/libs/hipblas/` |
| `metal` | macOS | Apple Metal (M1, M2, M3) | `build/libs/metal/` |
| `openblas` | Todas | OpenBLAS (CPU optimizado) | `build/libs/openblas/` |
| `openvino` | Linux | Intel GPU / NPU (OpenVINO) | `build/libs/openvino/` |

## Estructura de Directorios

Después de compilar variantes, tendrás:

```
build/
├── libs/
│   ├── cpu/
│   │   ├── libllama.so
│   │   ├── libggml.so
│   │   ├── libggml-base.so
│   │   ├── libggml-cpu.so
│   │   └── BUILD_INFO.txt
│   ├── cuda/
│   │   ├── libllama.so
│   │   ├── libggml.so
│   │   ├── libggml-base.so
│   │   ├── libggml-cpu.so
│   │   ├── libggml-cuda.so          ← Específico CUDA
│   │   └── BUILD_INFO.txt
│   ├── hipblas/
│   │   ├── libllama.so
│   │   ├── libggml.so
│   │   ├── libggml-rocm.so          ← Específico ROCm
│   │   

*[truncated — see source for full prompt]*