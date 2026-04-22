# Scaling Laws

> > **概述**：本文档详细解析了 Chinchilla 论文的缩放定律实验，包括参数计算、FLOPs 估算和计算最优模型分析。适用于想要深入了解 LLM 训练成本和模型优化决策的工程师。

## 📋 目录

1. [参数计算 (Parameter Counting)](#参数计算-paramet

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GPT 模型缩放定律详解 (Scaling Laws) - nanoGPT 实现

> **概述**：本文档详细解析了 Chinchilla 论文的缩放定律实验，包括参数计算、FLOPs 估算和计算最优模型分析。适用于想要深入了解 LLM 训练成本和模型优化决策的工程师。

## 📋 目录

1. [参数计算 (Parameter Counting)](#参数计算-parameter-counting)
2. [FLOPs 估算 (FLOPs Estimation)](#flops-估算-flops-estimation)
3. [缩放定律方法 3 (Approach 3)](#缩放定律方法-3-approach-3)
4. [缩放定律方法 2 (Approach 2)](#缩放定律方法-2-approach-2)
5. [核心洞见与工程启示](#核心洞见与工程启示)
6. [实战应用指南](#实战应用指南)

---

## 🧮 参数计算 (Parameter Counting)

### GPT 架构参数计算

#### **核心架构解析**

```python
def gpt_params(seq_len, vocab_size, d_model, num_heads, num_layers):
    """给定 GPT 配置计算总参数数量"""
    ffw_size = 4 * d_model  # GPT 中中间特征数总是 4*d_model

    # token 和位置嵌入
    embeddings = d_model * vocab_size + d_model * seq_len

    # Transformer 块
    attention = 3*d_model**2 + 3*d_model  # 权重和偏置
    attproj = d_model**2 + d_model
    ffw = d_model*ffw_size + ffw_size
    ffwproj = ffw_size*d_model + d_model
    layernorms = 2*2*d_model

    # 输出层
    ln_f = 2*d_model
    dense = d_model*vocab_size  # 注意：这里没有偏置

    # 注意：嵌入通常不计入参数计数！
    total_params = num_layers*(attention + attproj + ffw + ffwproj + layernorms) + ln_f + dense
    return total_params
```

#### **张量流跟踪 (Tensor Shape Tracking)**

1. **Q/K/V 投影**：`(B, T, C) -> (B, T, 3*C)`，需要 `3*C*C` 参数
2. **注意力输出投影**：`(B, T, C) -> (B, T, C)`，需要 `C*C` 参数
3. **FFN 第一层**：`(B, T, C) -> (B, T, 4*C)`，需要 `C*4*C + 4*C` 参数
4. **FFN 第二层**：`(B, T, 4*C) -> (B, T, C)`，需要 `4*C*C + C` 参数

#### **为什么 `bias=False`？**

现代 LLM 实践中通常省略偏置项，原因：
- **正则化效果**：减少参数量，降低过拟合风险
- **批量归一化**：LayerNorm 已经提供了中心化功能
- **训练稳定性**：简化梯度流动

### Chinchilla 架构参数计算

```python
def chinchilla_params(seq_len, vocab_size, d_model, num_heads, num_layers, ffw_size):
    """ Chinchilla 模型的参数计算。与 GPT 不同，它们使用相对位置嵌入。"""
    # 只有 token 嵌入
    embeddings = d_model * vocab_size

    # Transformer 块
    attention = 3*d_model**2 + 3*d_model  # 权重和偏置
    relative_pos = d_model**2 + 2*d_model  # 相对键、内容偏置、相对偏置
    attproj = d_model**2 + d_model
    ffw = d_model*ffw_size + ffw_size
    ffwpro

*[truncated — see source for full prompt]*