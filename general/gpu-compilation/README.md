# GPU COMPILATION

> Esta guía te ayudará a compilar llama.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Guía de Compilación con Soporte GPU

Esta guía te ayudará a compilar llama.cpp con soporte GPU para acelerar significativamente la inferencia de modelos GGUF.

## Índice

- [Requisitos Previos](#requisitos-previos)
- [Compilación para NVIDIA GPU (CUDA)](#compilación-para-nvidia-gpu-cuda)
- [Compilación Rápida con Script](#compilación-rápida-con-script)
- [Configuración y Uso](#configuración-y-uso)
- [Troubleshooting](#troubleshooting)
- [Rendimiento Esperado](#rendimiento-esperado)

## Requisitos Previos

### Para NVIDIA GPU (CUDA)

1. **GPU NVIDIA compatible** (Compute Capability 3.5+)
   - Verifica tu GPU: `nvidia-smi`
   - Para RTX 3060: 6GB VRAM, ~32 capas GPU recomendadas

2. **NVIDIA Drivers actualizados**
   ```bash
   nvidia-smi  # Debe mostrar tu GPU
   ```

3. **CUDA Toolkit** (11.0 o superior)
   ```bash
   nvcc --version  # Debe mostrar la versión de CUDA
   ```

   Si no tienes CUDA instalado:
   ```bash
   # Ubuntu/Debian
   wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb
   sudo dpkg -i cuda-keyring_1.0-1_all.deb
   sudo apt-get update
   sudo apt-get install cuda
   
   # Añadir a ~/.bashrc
   export PATH=/usr/local/cuda/bin:$PATH
   export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
   ```

4. **CMake** (3.14 o superior)
   ```bash
   cmake --version
   # Si no está instalado:
   sudo apt-get install cmake  # Ubuntu/Debian
   ```

5. **Compilador C/C++**
   ```bash
   gcc --version
   g++ --version
   # Si no están instalados:
   sudo apt-get install build-essential
   ```

### Para AMD GPU (ROCm)

1. **GPU AMD compatible**
2. **ROCm 5.0+** instalado
3. Consulta: https://rocmdocs.amd.com/

### Para Apple Silicon (Metal)

El soporte Metal se compila automáticamente en macOS con Apple Silicon.

## Compilación para NVIDIA GPU (CUDA)

### Opción 1: Script Automático (Recomendado)

Hemos creado un script que automatiza todo el proceso:

```bash
# Ejecutar el script de compilación CUD

*[truncated — see source for full prompt]*