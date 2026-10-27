# transformers v5.21.0 release notes（节选）

- 来源：<https://github.com/huggingface/transformers/releases/tag/v5.21>
- 抓取：2026-10-27（api.github.com releases，published_at 2026-10-26T18:17:42Z）
- 性质：官方 release notes 短摘（新增模型两节，其余 bugfix 段落略）。

## MiniCPM-OCR

MiniCPM-OCR is a document-understanding model from OpenBMB's MiniCPM-V family. It keeps the MiniCPM-V 4.6 architecture, which pairs a SigLIP vision encoder and a window-attention merger with a Qwen3.5 language model. It is specialized for reading text-dense images such as scanned pages, screenshots, receipts and tables.
Links: Documentation（model_doc/minicpm_ocr）| Paper（arXiv 2509.18154）| PR #49920

## Flint

Flint is Recursive's mixture-of-experts language model. Compared to a standard SwiGLU MoE transformer such as Qwen3-MoE, it uses hybrid attention (sliding-window attention with rotary embeddings over the current token and the previous 512 tokens in most layers, and full attention without positional encoding in the remaining layers). It also has learned attention sinks, as in GPT-OSS, with per-head RMS-normalized queries and keys. Each sparse layer routes a token to 6 of 256 experts by sigmoid score and adds an ungated shared expert.
