---
name: Train
description: ```shell
pip install modelscope
modelscope download --dataset dukguo/WenetSpeech4TTS Premium/WenetSpeech4TTS_Premium_0.tar.gz --local_dir ./dir

cd di
model: claude-sonnet-4-5
---
## 1. 准备数据集
```shell
pip install modelscope
modelscope download --dataset dukguo/WenetSpeech4TTS Premium/WenetSpeech4TTS_Premium_0.tar.gz --local_dir ./dir

cd dir && tar -zxf Premium/WenetSpeech4TTS_Premium_0.tar.gz

# 0.准备数据集
# 将 wavs 和 txts 移动到 dataset/ 下
mv ./dir/Premium/WenetSpeech4TTS_Premium_0/* ./dataset/

# 生成 labels.txt
python extract_WenetSpeech4TTS.py


# 1.生成音素词汇表
python build_phoneme_vocab.py

# 2.训练 K-Means 生成 kmeans_*.joblib
python train_kmeans.py

# 3.预处理生成 dataset/processed/ 下的 .pt 文件
python preprocess.py

# 4.训练 GPT
python train_pipeline.py gpt

# 5.训练 Vocoder
python train_pipeline.py vocoder

# 推理
python inference.py


cd gpt-vits 
python build_phoneme_vocab.py && python train_kmeans.py && python preprocess.py && python train_pipeline.py gpt && python train_pipeline.py vocoder && python inference.py
```