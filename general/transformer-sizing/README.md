# Transformer Sizing

> > **概述**：本文档详细分析了 Transformer 模型的各项性能指标，包括参数数量、FLOPs 计算、内存占用、训练时间估算等核心指标的计算方法和实际测量结果。

## 📋 目录

1. [模型参数计算](#模型参数计算)
2. [检查点大小与 GPU 内存分析](#检查点大小与-gpu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Transformer 模型理论分析 - 参数、FLOPs 与内存估算

> **概述**：本文档详细分析了 Transformer 模型的各项性能指标，包括参数数量、FLOPs 计算、内存占用、训练时间估算等核心指标的计算方法和实际测量结果。

## 📋 目录

1. [模型参数计算](#模型参数计算)
2. [检查点大小与 GPU 内存分析](#检查点大小与-gpu-内存分析)
3. [FLOPs 计算分析](#flops-计算分析)
4. [硬件利用率分析](#硬件利用率分析)
5. [训练时间估算](#训练时间估算)
6. [工程实践建议](#工程实践建议)

---

## 🧮 模型参数计算

### **配置参数**

```python
# GPT-2 Small 配置
block_size = 1024    # 序列长度
vocab_size = 50257   # 词汇表大小
n_layer = 12         # Transformer 层数
n_head = 12          # 注意力头数
n_embd = 768         # 嵌入维度
bias = False         # 简化假设，不使用偏置
```

### **详细参数计算**

```python
def params():
    """估算模型中的参数数量"""
    out = OrderedDict()

    # token 和位置嵌入
    out['emebedding/position'] = n_embd * block_size    # 位置嵌入
    out['embedding/token'] = n_embd * vocab_size        # token 嵌入
    out['embedding'] = out['emebedding/position'] + out['embedding/token']

    # 注意力块
    out['attention/ln'] = n_embd                        # LayerNorm 参数 (bias=False)
    out['attention/kqv'] = n_embd * 3*n_embd           # Q,K,V 投影
    out['attention/proj'] = n_embd**2                   # 注意力输出投影
    out['attention'] = out['attention/ln'] + out['attention/kqv'] + out['attention/proj']

    # MLP 块
    ffw_size = 4*n_embd                                 # 前馈网络中间维度
    out['mlp/ln'] = n_embd                              # LayerNorm
    out['mlp/ffw'] = n_embd * ffw_size                 # 第一个线性层
    out['mlp/proj'] = ffw_size * n_embd                 # 第二个线性层
    out['mlp'] = out['mlp/ln'] + out['mlp/ffw'] + out['mlp/proj']

    # Transformer 模块
    out['block'] = out['attention'] + out['mlp']       # 单个 Transformer 块
    out['transformer'] = n_layer * out['block']         # 所有 Transformer 块
    out['ln_f'] = n_embd                                # 最终 LayerNorm
    out['dense'] = 0                                    # 输出层 (与嵌入层参数共享)

    # 总参数数
    out['total'] = out['embedding'] + out['transformer'] + out['ln_f'] + out['dense']

    return out
```

### **参数分布分析**

| 组件 | 参数数量 | 占比 | 工程意义 |
|------|----

*[truncated — see source for full prompt]*