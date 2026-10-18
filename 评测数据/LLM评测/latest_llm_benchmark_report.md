# LLM Streaming Benchmark Report (latest per variant)

This report keeps the latest run for each model/config variant, but only `pt-BR` runs with `max_completion_tokens >= 200` and `concurrency >= 4` are treated as decision-lane evidence.

## Decision Lane: Strict JSON PT-BR (Deterministic)

| Variant | OK | JSON valid | Schema match | Field complete | P95 TTFT (ms) | Failure modes | Weights (GiB) | KV cache (GiB) | Summary |
|---|---:|---:|---:|---:|---:|---|---:|---:|---|
| google/gemma-4-E2B-it [len=8192, c=4, out=200] | 60/60 | 1.000 | 1.000 | 1.000 | 352.637 | n/a | 9.790 | 8.900 | `llm/benchmarks/gemma-4-E2B-it/20260422_164835_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0/summary.json` |
| Qwen/Qwen2.5-14B-Instruct-AWQ [c=4, out=200] | 60/60 | 0.950 | 0.950 | 0.950 | 1789.073 | non_json_text=0.05 | 9.380 | 9.710 | `llm/benchmarks/Qwen2_5-14B-Instruct-AWQ/20260422_160304_json_gate_c4_det_schema_inline_c4_r3_temp0p0/summary.json` |
| Qwen/Qwen3-4B [no_think, c=4, out=200] | 60/60 | 0.900 | 0.900 | 0.900 | 480.854 | non_json_text=0.10 | 7.560 | 11.560 | `llm/benchmarks/Qwen3-4B/20260422_161358_json_gate_c4_det_schema_inline_c4_r3_temp0p0_no_think/summary.json` |
| Qwen/Qwen2.5-7B-Instruct [c=4, out=200] | 60/60 | 0.900 | 0.900 | 0.900 | 845.020 | non_json_text=0.10 | 14.250 | 4.860 | `llm/benchmarks/Qwen2_5-7B-Instruct/20260422_161725_json_gate_c4_det_schema_inline_c4_r3_temp0p0/summary.json` |
| Qwen/Qwen3-8B [len=8192, no_think, c=4, out=200] | 60/60 | 0.900 | 0.900 | 0.900 | 936.787 | non_json_text=0.10 | 15.270 | 3.830 | `llm/benchmarks/Qwen3-8B/20260422_162233_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0_no_think/summary.json` |
| google/gemma-4-E4B-it [len=8192, c=4, out=200] | 60/60 | 1.000 | 0.850 | 1.000 | 659.229 | wrong_type=0.15 | 15.160 | 3.510 | `llm/benchmarks/gemma-4-E4B-it/20260422_165319_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0/summary.json` |
| Qwen/Qwen3.5-4B [no_think, c=4, out=200] | 60/60 | 0.583 | 0.583 | 0.583 | 1194.826 | non_json_text=0.42 | 8.610 | 9.350 | `llm/benchmarks/Qwen3_5-4B/20260422_160619_json_gate_c4_det_schema_inline_c4_r3_temp0p0_no_think/summary.json` |
| mistralai/Ministral-3-3B-Instruct-2512 [len=8192, c=4, out=200] | 60/60 | 0.000 | 0.000 | 0.789 | 280.133 | markdown_fence=1.00, wrong_type=0.68, non_json_text=0.20, missing_field=0.07 | 4.440 | 14.390 | `llm/benchmarks/Ministral-3-3B-Instruct-2512/20260422_163233_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0/summary.json` |
| mistralai/Ministral-3-8B-Instruct-2512 [len=8192, c=4, out=200] | 60/60 | 0.000 | 0.000 | 0.417 | 620.329 | markdown_fence=1.00, non_json_text=0.58, wrong_type=0.15 | 9.770 | 9.050 | `llm/benchmarks/Ministral-3-8B-Instruct-2512/20260422_163625_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0/summary.json` |
| mistralai/Ministral-3-14B-Instruct-2512 [len=8192, c=4, out=200] | 60/60 | 0.000 | 0.000 | 0.083 | 953.787 | markdown_fence=1.00, non_json_text=0.92 | 14.710 | 4.110 | `llm/benchmarks/Ministral-3-14B-Instruct-2512/20260422_164238_json_gate_c4_det_schema_inline_len8192_c4_r3_temp0p0/summary.json` |
| Qwen/Qwen3.5-9B [len=1024, eager, no_think, c=4, out=200] | 0/60 | 0.000 | 0.000 | 0.000 | n/a | empty_output=1.00 | 17.660 | 0.140 | `llm/benchmarks/Qwen3_5-9B/20260422_162920_json_gate_c4_det_schema_inline_len1024_eager_c4_r3_temp0p0_no_think/summary.json` |

## Decision Lane: Strict JSON PT-BR (Sampled Stability)

| Variant | OK | JSON valid | Schema match | Field complete | P95 TTFT (ms) | Failure modes | Weights (GiB) | KV cache (GiB) | Summary |
|---|---:|---:|---:|---:|---:|---|---:|---:|---|
| google/gemma-4-E2B-it [len=8192, c=4, temp=0.2, out=200] | 20/20 | 1.000 | 1.000 | 1.000 | 384.660 | n/a | 9.790 | 8.900 | `llm/benchmarks/gemma-4-E2B-it/20260422_172147_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2/summary.json` |
| Qwen/Qwen2.5-14B-Instruct-AWQ [c=4, temp=0.2, out=200] | 20/20 | 0.950 | 0.950 | 0.950 | 1785.754 | non_json_text=0.05 | 9.380 | 9.710 | `llm/benchmarks/Qwen2_5-14B-Instruct-AWQ/20260422_171619_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2/summary.json` |
| Qwen/Qwen2.5-7B-Instruct [c=4, temp=0.2, out=200] | 20/20 | 0.900 | 0.900 | 0.900 | 854.882 | non_json_text=0.10 | 14.250 | 4.860 | `llm/benchmarks/Qwen2_5-7B-Instruct/20260422_173258_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2/summary.json` |
| google/gemma-4-E4B-it [len=8192, c=4, temp=0.2, out=200] | 20/20 | 1.000 | 0.850 | 1.000 | 678.343 | wrong_type=0.15 | 15.160 | 3.510 | `llm/benchmarks/gemma-4-E4B-it/20260422_172454_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2/summary.json` |
| Qwen/Qwen3-4B [no_think, c=4, temp=0.2, out=200] | 20/20 | 0.850 | 0.850 | 0.850 | 544.179 | non_json_text=0.15 | 7.560 | 11.560 | `llm/benchmarks/Qwen3-4B/20260422_173001_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2_no_think/summary.json` |
| Qwen/Qwen3-8B [len=8192, no_think, c=4, temp=0.2, out=200] | 20/20 | 0.850 | 0.850 | 0.850 | 948.997 | non_json_text=0.15 | 15.270 | 3.830 | `llm/benchmarks/Qwen3-8B/20260422_173627_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2_no_think/summary.json` |
| Qwen/Qwen3.5-4B [no_think, c=4, temp=0.2, out=200] | 20/20 | 0.400 | 0.400 | 0.400 | 711.400 | non_json_text=0.60 | 8.610 | 9.350 | `llm/benchmarks/Qwen3_5-4B/20260422_171852_json_gate_c4_sampled_schema_inline_c4_r1_temp0p2_no_think/summary.json` |

## Decision Lane: Stream PT-BR

| Variant | OK | Avg input tok | P95 TTFT (ms) | Avg E2E (ms) | Tok/s | Weights (GiB) | KV cache (GiB) | Summary |
|---|---:|---:|---:|---:|---:|---:|---:|---|
| Qwen/Qwen3-4B [no_think, c=8, out=200] | 12/12 | 73.083 | 176.520 | 1868.302 | 29.171 | 7.560 | 11.560 | `llm/benchmarks/Qwen3-4B/20260422_173849_stream_c8_refresh_c8_r1_temp0p0_no_think/summary.json` |
| Qwen/Qwen2.5-7B-Instruct [c=8, out=200] | 12/12 | 73.083 | 206.537 | 3308.212 | 17.208 | 14.250 | 4.860 | `llm/benchmarks/Qwen2_5-7B-Instruct/20260422_174103_stream_c8_refresh_c8_r1_temp0p0/summary.json` |
| google/gemma-4-E2B-it [len=8192, c=8, out=200] | 12/12 | 63.667 | 223.374 | 1604.715 | 48.616 | 9.790 | 8.900 | `llm/benchmarks/gemma-4-E2B-it/20260422_174624_stream_c8_refresh_c8_r1_temp0p0/summary.json` |
| Qwen/Qwen3-8B [len=8192, no_think, c=8, out=200] | 12/12 | 73.083 | 238.861 | 4304.567 | 15.768 | 15.270 | 3.830 | `llm/benchmarks/Qwen3-8B/20260422_173947_stream_c8_refresh_c8_r1_temp0p0_no_think/summary.json` |
| Qwen/Qwen2.5-14B-Instruct-AWQ [c=8, out=200] | 12/12 | 73.083 | 273.252 | 2185.189 | 27.653 | 9.380 | 9.710 | `llm/benchmarks/Qwen2_5-14B-Instruct-AWQ/20260422_174207_stream_c8_refresh_c8_r1_temp0p0/summary.json` |
| google/gemma-4-E4B-it [len=8192, c=8, out=200] | 12/12 | 63.667 | 304.285 | 2258.506 | 25.054 | 15.160 | 3.510 | `llm/benchmarks/gemma-4-E4B-it/20260422_174916_stream_c8_refresh_c8_r1_temp0p0/summary.json` |
| Qwen/Qwen3.5-4B [no_think, c=8, out=200] | 12/12 | 64.833 | 315.735 | 2280.541 | 26.185 | 8.610 | 9.350 | `llm/benchmarks/Qwen3_5-4B/20260422_174404_stream_c8_refresh_c8_r1_temp0p0_no_think/summary.json` |

## Decision Lane: Long-Context Stream PT-BR

| Variant | OK | Avg input tok | P95 input tok | P95 TTFT (ms) | Avg E2E (ms) | Tok/s | Summary |
|---|---:|---:|---:|---:|---:|---:|---|
| google/gemma-4-E2B-it [len=8192, c=4, out=200] | 4/4 | 5189.000 | 5198.350 | 709.086 | 4376.170 | 46.234 | `llm/benchmarks/gemma-4-E2B-it/20260422_180336_stream_long_c4_refresh_c4_r1_temp0p0/summary.json` |
| Qwen/Qwen3-4B [no_think, c=4, out=200] | 4/4 | 5664.250 | 5678.300 | 1069.931 | 9082.625 | 24.947 | `llm/benchmarks/Qwen3-4B/20260422_175252_stream_long_c4_refresh_c4_r1_temp0p0_no_think/summary.json` |
| google/gemma-4-E4B-it [len=8192, c=4, out=200] | 4/4 | 5189.000 | 5198.350 | 1108.260 | 8686.636 | 23.922 | `llm/benchmarks/gemma-4-E4B-it/20260422_180625_stream_long_c4_refresh_c4_r1_temp0p0/summary.json` |
| Qwen/Qwen3.5-4B [no_think, c=4, out=200] | 4/4 | 5190.750 | 5199.500 | 1263.638 | 8877.986 | 25.917 | `llm/benchmarks/Qwen3_5-4B/20260422_180114_stream_long_c4_refresh_c4_r1_temp0p0_no_think/summary.json` |
| Qwen/Qwen2.5-7B-Instruct [c=4, out=200] | 4/4 | 5664.250 | 5678.300 | 1713.824 | 13644.193 | 16.758 | `llm/benchmarks/Qwen2_5-7B-Instruct/20260422_175656_stream_long_c4_refresh_c4_r1_temp0p0/summary.json` |
| Qwen/Qwen3-8B [len=8192, no_think, c=4, out=200] | 4/4 | 5664.250 | 5678.300 | 1889.500 | 15332.959 | 14.446 | `llm/benchmarks/Qwen3-8B/20260422_175428_stream_long_c4_refresh_c4_r1_temp0p0_no_think/summary.json` |
| Qwen/Qwen2.5-14B-Instruct-AWQ [c=4, out=200] | 4/4 | 5664.250 | 5678.300 | 3898.999 | 12437.613 | 22.559 | `llm/benchmarks/Qwen2_5-14B-Instruct-AWQ/20260422_175911_stream_long_c4_refresh_c4_r1_temp0p0/summary.json` |

## Legacy Or Non-Gating Runs

| Variant | Why Non-Gating | Groups | pt-BR share | out | c | JSON valid | Summary |
|---|---|---|---:|---:|---:|---:|---|
| google/gemma-4-E2B-it [len=8192, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/gemma-4-E2B-it/summary.json` |
| Qwen/Qwen2.5-3B-Instruct [out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen2_5-3B-Instruct/summary.json` |
| google/gemma-3-4b-it [len=8192, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/gemma-3-4b-it/summary.json` |
| Qwen/Qwen3-4B [len=16384, no_think, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen3-4B/summary.json` |
| Qwen/Qwen2.5-14B-Instruct-AWQ [quant=awq_marlin, len=8192, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen2_5-14B-Instruct-AWQ/summary.json` |
| google/gemma-3n-E4B-it [len=8192, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/gemma-3n-E4B-it/summary.json` |
| google/gemma-4-E4B-it [len=8192, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/gemma-4-E4B-it/summary.json` |
| Qwen/Qwen3.5-4B [len=8192, no_think, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen3_5-4B/summary.json` |
| Qwen/Qwen2.5-7B-Instruct [out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen2_5-7B-Instruct/summary.json` |
| Qwen/Qwen3-8B [len=16384, no_think, out=64] | mixed/non-primary language set, out<200, c<4 | quick_stream_pt_br, quick_stream_vi_vn, zh_ops_quickcheck | 0.400 | 64 | 1 | n/a | `llm/benchmarks/Qwen3-8B/summary.json` |
| Qwen/Qwen3.5-4B [no_think, c=1, out=200] | c<4, smoke/sample-trimmed | quick_stream_pt_br_primary | 1.000 | 200 | 1 | n/a | `llm/benchmarks/Qwen3_5-4B/20260422_141923_smoke_qwen35_4b_vllmvenv_c1_r1_temp0p0_no_think/summary.json` |

## Notes

- `Qwen3/Qwen3.5` non-thinking runs should be read from `disable_thinking=true`; prompt-level `/no_think` is not the intended control path.
- `json_valid_rate`, `schema_match_rate`, and `field_completeness` are the primary gate metrics for the dialogue LLM lane.
- The sampled JSON lane is for stability drift only; primary admission should still be based on the deterministic JSON gate first.
- `TTFT` should be compared primarily on the `stream` lane and the `long-context` lane; strict JSON rows answer the `3B/4B versus 8B/9B` reliability gate.
- `peak_gpu_used_mb_max` remains a CSV hint only. Capacity planning should use `model_weights_gib` and `kv_cache_gib`.
- Current cross-model conclusions are relative comparisons between each vendor's most practical local variant, not a same-quantization apples-to-apples bakeoff.
- Quantized variants are kept separate from default-precision runs because they materially change throughput and memory behavior.
