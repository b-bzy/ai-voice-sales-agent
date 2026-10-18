# GPT-Realtime-2 巴西葡语原始数据审计索引

生成时间：2026-05-15

本目录用于审计 `gpt_realtime_2_raw_20260514` 中 `pt_br` / `gpt-realtime-2` 真人评测数据，目标是把 6 位完整巴西葡语 tester 的正式样本、排除样本、数字听写规范化结果和问题样本拆开，方便复查。

## 来源

- 原始目录：`docs/research/benson/eval_runs/gpt_realtime_2_raw_20260514`
- 原始 manifest：`../manifest.json`
- 审计 manifest：`manifest.audit.json`
- 全量 responses：`../responses_flat.csv`
- 完整作答 responses：`../responses_real_complete.csv`
- 原始数字听写：`../number_dictation.csv`
- 原始完整 tester 汇总：`../real_testers_summary.csv`

注意：原始 `manifest.json` 是 2026-05-14 的混合导出 manifest，包含 `vi_vn` 和 `pt_br` 数据，且仍残留上一轮三段式 / VieNeu 字段。审计和报告以 `manifest.audit.json` 为准，原始文件保留不改。

## 过滤口径

纳入 6 位完整巴西葡语测试者，每人 32 条正式作答：

- `vi_native_191a64a955`
- `vi_native_80241a5b53`
- `vi_native_9227f2ca28`
- `vi_native_bda23e7079`
- `vi_native_9be3105760`
- `vi_native_14aaf2de87`

排除 2 位巴西葡语未完成或测试残留 tester：

- `vi_native_aa8e022ecd`：1 条作答
- `vi_native_e6e9ff2454`：10 条作答

## 文件说明

| 文件 | 用途 |
|---|---|
| `manifest.audit.json` | 本次审计使用的 STS backend manifest，记录真实 pt_br 口径、缺失配置和 schema 说明。 |
| `summary.json` | 本次审计导出的机器可读摘要，包括纳入 tester、排除 tester、响应数和数字匹配数。 |
| `responses_real_complete.csv` | 6 位完整 pt_br tester 的 192 条正式作答。 |
| `real_testers_summary.csv` | 6 位完整 pt_br tester 的元数据、平均分和明显问题数。 |
| `number_dictation_audit.csv` | 48 条 pt_br 数字听写，补充规范化字段，便于区分格式差异和真实漏听。 |
| `issue_samples.csv` | 1 条被标记为明显问题的 pt_br 样本。 |
| `excluded_testers.csv` | 被排除 pt_br tester 的响应数、起止时间和排除原因。 |

## 数字规范化字段

`number_dictation_audit.csv` 在原始字段后补充：

- `expected_normalized`：期望值规范化结果，例如 `date:2026-05-12`、`amount:1250.00`、`phone_br:11912345678`、`digits:482906`。
- `heard_normalized`：测试者听写值规范化结果。
- `normalized_exact_match`：规范化后是否完整匹配，`1` 表示信息层面一致。
- `audit_note`：
  - `strict_exact`：原始严格匹配已正确。
  - `normalized_exact_only`：原始字符串不一致，但规范化后信息一致。
  - `mismatch`：规范化后仍不一致，属于真实漏听或信息错误。

## 快速结论

- 完整正式作答：192 条。
- 数字听写：48 条。
- 严格数字正确：17 条，正确率 35.4%。
- 规范化数字正确：44 条，正确率 91.7%。
- 规范化后仍错误：4 条，分别是验证码错位、金额错听、手机号数字错听或漏号。
- `voice`、`instructions_hash`、`input_mode` 当前均为 `not_recorded`，下一轮必须记录。
- 4 条真实数字误听录音已归档到 `../misheard_number_audio_20260514`，并在该目录的 `manifest.csv` 中索引；1 条语速 issue 样本仍只有服务端音频路径，复听仍待补。
