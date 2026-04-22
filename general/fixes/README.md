# FIXES

> ## 修复概述
已修复导致推理音频全是噪音的 **5 个关键问题**

---

## ✅ 修复清单

### 1. 音素映射问题 (P0 - 最严重)
**问题**: `ord(p[0]) % 300` 导致 94% 的文本信息丢失
**修复**:
- 新增 `build_phoneme_voca

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
- [ ] Demo 音频从"白噪音"逐渐变

*[truncated — see source for full prompt]*