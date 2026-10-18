# 越南语 STT benchmark 报告

- 评测时间: 2026-04-24T15:54:28
- 数据集: `<internal-src>/stt/speech_asr_fleurs_vi_vn_dev.csv`
- 样本数: `50`
- chunk 秒数: `0.72`
- 音频 profile: `telephone8k`

| Profile | 模型 | 成功/总数 | Full WER | Stream WER | Full RTF | Stream RTF | 首字延迟(ms) | 分块延迟(ms) |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| telephone8k | sherpa-onnx-zipformer-vi | 50/50 | 0.0939 | 0.0939 | 0.025 | 0.238 | 95.6 | 146.3 |
