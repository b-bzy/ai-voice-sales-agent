# GPT-Realtime-2 原始数据审计索引

生成时间：2026-05-13

本目录用于审计 `gpt_realtime_2_raw_20260513` 中 `gpt-realtime-2` 真人评测数据，目标是把 4 位真实 tester 的正式样本、排除样本、数字听写规范化结果和问题样本拆开，方便复查。

## 来源

- 原始目录：`docs/research/benson/eval_runs/gpt_realtime_2_raw_20260513`
- 原始 manifest：`../manifest.json`
- 全量 responses：`../responses_flat.csv`
- 原始数字听写：`../number_dictation.csv`
- 原始完整 tester 汇总：`../real_testers_summary.csv`

## 过滤口径

纳入 4 位真实测试者，每人 32 条正式作答：

- `vi_native_6b992f17af`
- `vi_native_99971e1db8`
- `vi_native_e7b6bade49`
- `vi_native_91ae486eaf`

排除 1 位完整但不计入真实 tester 口径的数据，以及 3 位未完成或测试残留 tester：

- `vi_native_07ae9ece1b`：32 条作答，完整但不计入真实 tester 统计口径；具体排除原因未随原始导出记录，需数据负责人补充确认
- `vi_native_8332c4a2cd`：4 条作答
- `vi_native_b4cd6af120`：4 条作答
- `vi_native_899dd707c8`：1 条作答

## 文件说明

| 文件 | 用途 |
|---|---|
| `summary.json` | 本次审计导出的机器可读摘要，包括纳入 tester、排除 tester、响应数和数字匹配数。 |
| `responses_real_complete.csv` | 4 位真实 tester 的 128 条正式作答。 |
| `real_testers_summary.csv` | 4 位真实 tester 的元数据、平均分和明显问题数。 |
| `number_dictation_audit.csv` | 32 条真实 tester 数字听写，补充规范化字段，便于区分格式差异和真实漏听。 |
| `issue_samples.csv` | 2 条被标记为明显问题的样本。 |
| `excluded_testers.csv` | 被排除 tester 的响应数、起止时间和排除原因。 |

## 数字规范化字段

`number_dictation_audit.csv` 在原始字段后补充：

- `expected_normalized`：期望值规范化结果，例如 `date:2026-05-12`、`amount:1250000`、`digits:482906`。
- `heard_normalized`：测试者听写值规范化结果。
- `normalized_exact_match`：规范化后是否完整匹配，`1` 表示信息层面一致。
- `audit_note`：
  - `strict_exact`：原始严格匹配已正确。
  - `normalized_exact_only`：原始字符串不一致，但规范化后信息一致。
  - `mismatch`：规范化后仍不一致，属于真实漏听或信息错误。

## 快速结论

- 完整正式作答：128 条。
- 数字听写：32 条。
- 严格数字正确：17 条，正确率 53.1%。
- 规范化数字正确：30 条，正确率 93.8%。
- 规范化后仍错误：2 条，分别是验证码少听 `0`、手机号少听前缀 `091`。
- `manifest.json` 已按 STS backend 口径修正；`voice`、`instructions_hash`、`input_mode` 当前均为 `not_recorded`，下一轮必须记录。
- 两条真实数字误听录音已归档到 `../../gpt_realtime_2_raw_20260514/misheard_number_audio_20260514`，并在该目录的 `manifest.csv` 中索引；两条语速 / 机器感 issue 样本仍只有服务端音频路径，复听仍待补。
