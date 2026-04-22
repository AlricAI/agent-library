---
name: FIXES
description: ## 修复概述
已修复导致推理音频全是噪音的 **5 个关键问题**

---

## ✅ 修复清单

### 1. 音素映射问题 (P0 - 最严重)
**问题**: `ord(p[0]) % 300` 导致 94% 的文本信息丢失
**修复**:
- 新增 `build_phoneme_voca
model: claude-sonnet-4-5
---
# 🐛 Bug 修复完成报告

## 修复概述
已修复导致推理音频全是噪音的 **5 个关键问题**

---

## ✅ 修复清单

### 1. 音素映射问题 (P0 - 最严重)
**问题**: `ord(p[0]) % 300` 导致 94% 的文本信息丢失
**修复**:
- 新增 `build_phoneme_vocab.py` - 构建稳定的音素词汇表
- 修改 `preprocess.py` - 使用 phoneme_vocab.json 映射
- 影响: GPT 现在能正确学习文本到语义的映射

### 2. GPT 训练因果对齐错误 (P0 - 最严重)
**问题**: `sem_tgt = sem[:, :]` 导致自回归训练错位
**修复**: `train_pipeline.py:92`
```python
# 修复前
sem_tgt = sem[:, :]  # ❌ 错误

# 修复后
sem_tgt = sem[:, 1:]  # ✅ 正确：去掉第一个 token
```

### 3. 位置编码越界保护 (P1)
**问题**: 长序列可能导致 pos_emb 索引越界
**修复**: `models.py:49-56` 添加边界检查和详细错误提示

### 4. 统一切片长度配置 (P1)
**问题**: GPT (200) 和 Vocoder (64) 切片长度不一致
**修复**:
- `config.py:45-46` 新增统一配置
- `train_pipeline.py:33` 使用 `Config.gpt_segment_len = 128`
- `train_s2a.py:67` 使用 `Config.vocoder_segment_len = 64`

### 5. 改进推理采样策略 (P2)
**问题**: 纯 argmax 导致输出缺乏多样性
**修复**: `inference.py:9-54` 新增温度采样、Top-K、Top-P

---

## 🔄 重新训练指南

### 第一步: 重新生成音素词汇表
```bash
cd gpt-vits
python build_phoneme_vocab.py
```
**输出**: `phoneme_vocab.json` (约 400+ 个拼音音素)

### 第二步: 重新预处理数据
```bash
# 如果已有 processed/ 目录，建议删除后重新生成
rm -rf dataset/processed/
python preprocess.py
```
**说明**: 会使用新的音素映射重新生成 .pt 文件

### 第三步: 重新训练 GPT
```bash
python train_pipeline.py gpt
```
**关键变化**:
- Loss 计算现在正确对齐 `sem[:, 1:]`
- 使用 128-token 切片长度
- 训练数据使用稳定的音素映射

**预期**:
- Loss 应该稳定下降 (如果训练正常，约 50 epochs 后 loss < 2.0)
- 如果 loss 不下降，检查数据预处理是否正确

### 第四步: 重新训练 Vocoder
```bash
python train_pipeline.py vocoder
```
**关键变化**:
- 使用 64-token 切片长度
- 与 GPT 训练数据使用相同的 hop_length (320)

**预期**:
- Loss 应该稳定下降
- 在 `logs_s2a/` 目录下生成的 demo 音频质量逐步提升

### 第五步: 推理测试
```bash
python inference.py
```
**新参数**:
```python
# 可在代码中调整采样策略
run_inference(
    text="你好，这是一次真实的千小时数据训练测试。",
    temperature=0.8,  # 0.5-1.0，越低越确定
    top_k=50,         # 从概率最高的 50 个 token 中采样
    top_p=0.9         # Nucleus sampling 阈值
)
```

---

## 📊 诊断检查点

### GPT 训练正常的表现
- [ ] Loss 稳定下降 (不出现 NaN 或突然飙升)
- [ ] 生成的 semantic token 范围在 [0, 1023] 内
- [ ] Token 有一定多样性（不是全部相同）

### Vocoder 训练正常的表现
- [ ] Loss 稳定下降
- [ ] Demo 音频从"白噪音"逐渐变成"可辨认的声音"
- [ ] 波形 RMS > 0.01（能量正常）

### 推理正常的指标
```
✓ 波形 shape: [1, T]
  波形范围: max≈0.5-1.0, min≈-0.5~-1.0
  波形 RMS: > 0.05
```

如果 `RMS < 0.01`，说明波形能量过低，可能是：
1. Vocoder 训练不足
2. GPT 生成的语义 token 质量差
3. 数据预处理问题

---

## 🧪 快速验证脚本

创建一个验证脚本检查修复效果：

```bash
# 检查音素词汇表
python -c "import json; v=json.load(open('phoneme_vocab.json')); print(f'音素词汇量: {len(v)}')"

# 检查预处理数据
python -c "
import torch, glob, os
files = glob.glob('dataset/processed/*.pt')[:5]
for f in files:
    d = torch.load(f, map_location='cpu')
    print(f'{os.path.basename(f)}: phonemes={d[\"phonemes\"].shape}, semantic={d[\"semantic\"].shape}')
"

# 检查 GPT 模型
python -c "
from models import Text2SemanticGPT
from config import Config
m = Text2SemanticGPT()
print(f'✓ GPT 参数量: {sum(p.numel() for p in m.parameters()) / 1e6:.2f}M')
print(f'✓ 位置编码最大长度: {m.pos_emb.num_embeddings}')
"

# 检查 Vocoder 模型
python -c "
from models import HiFiGANGenerator
from config import Config
m = HiFiGANGenerator()
print(f'✓ Vocoder 参数量: {sum(p.numel() for p in m.parameters()) / 1e6:.2f}M')
print(f'✓ 上采样倍数: 8 x 8 x 5 = 320')
"
```

---

## ⚠️ 常见问题

### Q1: 训练后仍然是噪音？
**排查步骤**:
1. 检查 GPT loss 是否收敛
2. 检查推理时 semantic token 的分布 (`inference.py` 已有诊断)
3. 尝试降低 `temperature` (0.5 或 0.3)
4. 检查 `logs_s2a/` 中的 demo 音频质量

### Q2: GPT loss 不下降？
**可能原因**:
1. 学习率过大/过小 (当前 1e-4)
2. 数据预处理问题（检查 phoneme_vocab.json 是否加载）
3. 模型结构问题（检查 loss 计算的对齐）

### Q3: Vocoder 训练很慢？
**优化建议**:
1. 增大 `batch_size` (当前 `batch_size*4`)
2. 减少 `segment_sem_len` (当前 64，可降到 32)
3. 使用混合精度训练 (`torch.cuda.amp`)

---

## 📈 预期训练时间 (5000 样本)

| 阶段 | Epochs | 预计时间 (V100) |
|------|--------|----------------|
| K-Means | 1 pass | ~30 min |
| 预处理 | - | ~1 hour |
| GPT | 50 epochs | ~2-3 hours |
| Vocoder | 100 epochs | ~4-6 hours |

**总计**: ~8-10 小时

---

## 🎯 下一步行动

1. **立即执行**: 运行 `build_phoneme_vocab.py`
2. **重新预处理**: 删除 `dataset/processed/` 并运行 `preprocess.py`
3. **开始训练**: GPT → Vocoder
4. **监控训练**: 关注 loss 曲线和 demo 音频质量

祝训练顺利！🚀