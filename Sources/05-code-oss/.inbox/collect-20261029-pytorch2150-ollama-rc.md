# 投递：PyTorch 2.15.0 正式发布与 ollama v0.40.13 RC（2026-10-29 daily）

> 巡检通道：GitHub REST API releases + release tag 详情。vllm、huggingface/transformers、run-llama/llama_index、openai/openai-agents-python 窗口内无新 release（复查无增量）。

## E1 · PyTorch 2.15.0：重写版 NCCL 后端转正为默认，一侧传输与 FP8/FP4 多点落地

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/pytorch/pytorch/releases/tag/v2.15.0>
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-pytorch-v2.15.0-release-notes-2026-10-28.md`
- 适用范围：官方发布（A 级，release notes 原文已存原件）；覆盖 2.15.0 的 highlights 与向后不兼容声明；不覆盖基准测试数值复现与跨版本性能回归验证。
- 证据等级：A
- 可提炼要点：
  1. 分布式主线：重写版 NCCL 后端成为默认，附 flight recorder（挂死时 dump），回滚路径为 `TORCH_DIST_USE_NCCL2=0` 或 `nccl-legacy`——发布即带显式降级开关。
  2. 传输能力：`torch.distributed` 新增一侧（one-sided）传输，NIXL 后端，且传输可被 CUDA graph 捕获。
  3. FSDP2/pipelining：精度敏感参数可选 fp32、梯度累积可 CUDA graph 捕获、梯度规约与计算重叠。
  4. 推理效率：Blackwell 上 NVFP4 LLM 解码提速（NVGEMM 更少、更好重叠的 kernel launch）；Apple Silicon 获得 `float8_e4m3fn` 与 `_scaled_mm`、新 `grouped_mm` 带解码快路径（官方口径 MoE decode 1.32–1.34x tokens/s）、公开 `torch.mps.Stream` API。
  5. 平台扩展：AMD 侧 FlyDSL kernel 等（详单见原件 Backwards Incompatible/Improvements 各节）。
- 关闭条件：官方数值（如 1.32–1.34x）为发布方口径，未第三方复现；引用进正文时须写「官方 release notes 数据」。破坏性变更清单已含在原件内，人工提炼时逐项核对后关。

## E2 · ollama v0.40.13-rc1：LFM3 GGUF 修复、llama-server 语音与 llama.cpp b11963

- 获取日期：2026-10-29
- 来源 URL：<https://github.com/ollama/ollama/releases/tag/v0.40.13-rc1>
- 本地原件：—
- 适用范围：官方 pre-release（A 级）；覆盖 v0.40.13 迭代周期首个 RC 的变更清单（PR #19344、#19360，compare 基线 v0.40.12...v0.40.13-rc0）；不覆盖正式版行为与 RC 后续增量。
- 证据等级：A
- 可提炼要点：
  1. 内容：LFM3 GGUF 修复 + llama-server 语音能力（dhiltgen）；llama.cpp 升级至 b11963。
  2. 节奏：延续「RC→稳定版」双日级节奏（v0.40.12 稳定版 2026-10-28 已登记，见 `inference-stack-releases` 箱），本块为该线下一节点。
- 关闭条件：v0.40.13 正式版未发布；转正或 RC 迭代停滞时在既有箱追加而不另开箱，本块随之可关。

## 台账登记

- 顺延：langchain-core==1.7.1（2026-10-28T15:00Z 补丁版，信息量低，并入 `agent-framework-releases` 节奏线时以 1.7.0→1.7.1 一行处理）。
- 复查无增量：vllm-project/vllm、huggingface/transformers、run-llama/llama_index、openai/openai-agents-python（窗口内无 release）；npm/pypi 侧 llamacpp 相关包未巡（配额）。
