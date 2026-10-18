# 评测数据

> 本文件夹存放评测的**汇总报告 + 原始数据集**（选型期的模型层评测 + 真人盲测）。
> 均为脱敏口径：无客户数据、无真实客户通话录音、无模型权重；tester 使用匿名 hash ID，
> 内部机器路径已替换为 `<internal-src>` 占位。

## 目录结构

```
评测数据/
├── LLM评测/       # LLM 选型 benchmark 报告 + 汇总 CSV
├── STT评测/       # 语音识别 benchmark 报告（WER / RTF）
├── TTS评测/       # 语音合成 benchmark 汇总 + 盲听打分卡
├── 真人评测/      # 母语者盲测完整报告
└── 原始数据/      # ★ 完整评测数据集（逐条原始记录，轻脱敏）
    ├── llm/       # 912 条 LLM 评测样本（11 模型 × 32 run）
    ├── stt/       # 200 条 STT 评测样本（4 模型）
    ├── tts/       # 50 条盲听音频 + 各模型 summary（5 模型）
    └── human/     # 1511 条真人评分记录 + 数字听写 + 测试人表
```

## 各子目录说明

### LLM评测/
- `latest_llm_benchmark_report.md` —— 本地 LLM 选型实测对比报告，4 条决策轨道
  （Strict JSON / 采样稳定性 / Stream / Long-Context），结论：gemma-4-E2B-it 综合最优。
- `latest_llm_benchmark_report.csv` —— 同一份数据的机器可读版（每模型一行的聚合指标）。

### STT评测/
- 4 份模型 report（`sherpa_vi_int8` / `sherpa_vi` / `phowhisper` / `parakeet_vi`），
  电话 8k 音质档，指标：Full/Stream WER、RTF、首字延迟、分块延迟。

### TTS评测/
- `pt_br_tts_human_eval_scorecard.csv` —— 母语者盲听打分卡。
- 5 份 `{模型}_summary.json`（kokoro / cosyvoice / fish-speech / indextts2 / qwen3-tts），
  指标：total_synth_time_ms、stream_first_chunk_ms、RTF。

### 真人评测/
- `GPT-REALTIME-2-HUMAN-EVAL-REAL-REPORT.md` —— 端到端实时链路真人盲测报告。
- `VI-TTS-HUMAN-EVAL-REAL-REPORT.md` —— 越南语 TTS 真人盲测报告。

## 原始数据集（`原始数据/`）

完整评测数据集，保留原始目录结构、逐条记录未删改（仅替换内部路径）。

| 数据集 | 规模 | 单条记录内容 |
|---|---|---|
| `llm/` LLM 评测集 | 912 条 / 11 模型 / 32 run | 输入（system prompt + 葡语电销对话 + 强制 JSON schema）+ 输出 + 逐条评分（合法率/匹配/延迟/吞吐） |
| `stt/` STT 评测集 | 200 条 / 4 模型 | 真值转写 `ref_text` + 模型输出 `pred_text` + WER / RTF / 延迟 |
| `tts/` TTS 评测集 | 50 条盲听音频 / 5 模型 | 合成音频 `blind_XX.wav` + summary（合成耗时 / RTF） |
| `human/` 真人评测集 | 1511 条评分 / 4 位测试人 | 逐人逐样本 6 维打分 + issue 类型 + 评语 + 数字听写 |

## 数据口径说明

| 项 | 口径 |
|---|---|
| 测试人 | 授权母语者（native speaker），匿名 hash ID 标识（如 `vi_native_<hash>`） |
| 音频来源 | STT 用开源语音集（FLEURS，仅存转录不存音频）；TTS 盲听音频为模型合成输出 |
| 脱敏处理 | 内部机器绝对路径 → `<internal-src>` 占位；不含真实客户数据（合规红线） |
| 结构保真 | 只替换路径，**未改动任何字段 / schema / 数据行**——原始数据结构原样保留 |

> 评测数据集可复现：`原始数据/llm` 的 `utterances.jsonl` 带 `text_id` 编号与真值 schema，
> 换新模型可对同一套题库重跑。
