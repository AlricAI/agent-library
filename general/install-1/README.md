# INSTALL

> ## 🚀 一键安装（推荐）

### 方案 1：使用 requirements.txt（避免版本冲突）

```bash
# 进入目录
cd z-image

# 创建虚拟环境（推荐）
python -m venv venv
source venv/bin/activate  

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Z-Image Turbo 快速安装指南

## 🚀 一键安装（推荐）

### 方案 1：使用 requirements.txt（避免版本冲突）

```bash
# 进入目录
cd z-image

# 创建虚拟环境（推荐）
python -m venv venv
source venv/bin/activate  # Linux/Mac
# 或
venv\Scripts\activate  # Windows

# 安装依赖
pip install -r requirements.txt
```

### 方案 2：PyTorch 官方 CUDA 版本（显存优化）

```bash
# 卸载旧版本
pip uninstall torch torchvision torchaudio -y

# 安装 CUDA 12.1 版本（根据你的 GPU 选择）
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# 安装其他依赖
pip install -r requirements.txt
```

---

## 🔧 常见问题修复

### 问题 1：NumPy/SciPy 二进制不兼容

```bash
# 完整卸载冲突包
pip uninstall numpy scipy diffusers transformers accelerate -y

# 按顺序重装（重要！）
pip install --upgrade --force-reinstall "numpy<2.0" "scipy>=1.10,<1.13"
pip install --upgrade --force-reinstall diffusers transformers accelerate
```

### 问题 2：pynvml 弃用警告

```bash
pip uninstall pynvml -y
pip install nvidia-ml-py
```

### 问题 3：模型下载失败

```bash
# 使用 HF-Mirror 加速
export HF_ENDPOINT=https://hf-mirror.com

# 或使用 ModelScope 镜像
export HF_ENDPOINT=https://huggingface.org.mirror.al
```

---

## 💻 硬件要求

### 最低配置
- GPU：NVIDIA GTX 1080 (8GB VRAM)
- RAM：16GB
- 存储：20GB（模型缓存）

### 推荐配置
- GPU：RTX 4090 / A100 (24GB VRAM)
- RAM：32GB+
- 存储：50GB+ SSD

### 显存优化技巧

```bash
# 低显存模式（<8GB）
python z_image.py --width 512 --height 512 --steps 4

# 标准模式（8-12GB）
python z_image.py --width 1024 --height 1024 --steps 10

# 高质量模式（16GB+）
python z_image.py --width 1536 --height 1536 --steps 20
```

---

## 📝 使用示例

### 本地生成（z_image.py）

```bash
# 单个提示词
python z_image.py --prompt "A beautiful landscape"

# 批量生成
python z_image.py --prompt-file prompt_list.txt --num 10

# 高清 + upscale
python z_image.py --prompt "Portrait" --width 1536 --height 1536 --enable-upscale --upscale-scale 2
```

### ModelScope API 生成（z_image_modelscope.py）

```bash
# API 模式（无需本地 GPU）
python z_image_modelscope.py --loops 10 --concurrency 3

# 

*[truncated — see source for full prompt]*