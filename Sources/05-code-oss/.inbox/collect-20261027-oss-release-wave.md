# 投递：开源发布波——transformers v5.21、ollama RC 与 langchain-openai 补丁（2026-10-27 daily）

> 巡检通道：GitHub API releases（8 仓逐条顺序）。窗口 2026-10-26 00:00Z~2026-10-27 01:00Z 命中 3 个 release：transformers v5.21.0、langchain-openai 1.7.3、ollama v0.40.12-rc0；vllm（最新 v0.32.0，10-18）、pytorch（v2.14.1，09-30）、MCP python/typescript SDK（10-02/10-23，均已登记）窗口内无新增。原件 1 份（release notes 节选）存 `Sources/05-code-oss/.inbox/originals/`。

## E1 · transformers v5.21.0：收录 MiniCPM-OCR 与 Recursive Flint 两个新模型

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/huggingface/transformers/releases/tag/v5.21>
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-transformers-v5.21-release-notes-2026-10-26.md`
- 适用范围：官方 release notes（A 级一手），覆盖 v5.21.0 新增模型条目（2026-10-26T18:17Z 发布）；不覆盖 bugfix 与向后兼容细节，具体 PR 面需查 release 全文。
- 证据等级：A
- 可提炼要点：
  1. MiniCPM-OCR：OpenBMB MiniCPM-V 家族的文档理解模型，沿用 MiniCPM-V 4.6 架构（SigLIP 视觉编码器 + window-attention merger + Qwen3.5 语言模型），面向扫描件/截图/票据/表格等文字密集图像；配套论文 arXiv 2509.18154。
  2. Flint（Recursive）：MoE 语言模型，与 Qwen3-MoE 式标准 SwiGLU MoE 的差异点（release 原文口径）——多数层用「当前 token + 前 512 token 滑窗 + RoPE」、其余层用「无位置编码全注意力」的混合注意力；仿 GPT-OSS 引入 learned attention sinks 与 per-head RMS-normalized QK；稀疏层按 sigmoid 分数路由至 256 专家中的 6 个并加 ungated shared expert。
  3. 与 10-22 投递的 ollama-flint 线（Flint 首发端）同主题：Flint 进入 transformers 主干意味着开源推理生态跟进，可并入同一 OSS 发布节奏箱追加。
- 关闭条件：Flint 架构描述目前只有 release notes 口径，缺 Recursive 官方技术报告核对；引用混合注意力细节前需回指原件（模型 config 或论文）。

## E2 · ollama v0.40.12-rc0：MLX 栈更新与 llama.cpp 版本跟进

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/ollama/ollama/releases/tag/v0.40.12-rc0>
- 本地原件：—
- 适用范围：官方 prerelease（A 级一手，2026-10-27T00:07Z 发布），覆盖 RC 变更清单四条；不覆盖 stable 行为承诺，正式发布前引用需标注 RC。
- 证据等级：A
- 可提炼要点：
  1. RC 内容（原文清单口径）：MLX 保留 compact Gemma 4 视觉塔的小图像细节（#19247）；MLX/MLX-C 版本 bump 带来 gemma/flint/laguna 的 prompt 提速（#19291）；MLX 新增 DFlash2 支持（#19149）；llama.cpp 跟进 b11901（#19311）。
  2. 节奏证据：延续 10-24 v0.40.11 → 10-27 v0.40.12-rc0 的约 3 天 RC 周期（与 inference-stack-releases 既有箱的 ollama 线合并计数）。
- 关闭条件：DFlash2 是什么组件（推测为 draft 模型方案）release notes 未展开；stable 发布后需以 v0.40.12 正式条目替换本 RC 引用。

## E3 · langchain-openai 1.7.3：model-profile 刷新与依赖修补的补丁版

- 获取日期：2026-10-27
- 来源 URL：<https://github.com/langchain-ai/langchain/releases/tag/langchain-openai%3D%3D1.7.3>
- 本地原件：—
- 适用范围：官方 release notes（A 级一手，2026-10-26T23:08Z 发布），覆盖 1.7.2→1.7.3 增量清单；无功能面变更声明，属维护性补丁。
- 证据等级：A
- 可提炼要点：
  1. 增量以依赖与元数据为主（原文口径）：openai model profile data 两次刷新（#41505/#41325）；aiohttp 3.14.3→3.14.5、certifi 2026.10.19、pytest 9.1.1 等 bump；放宽第三方依赖上界（#41407）；为保住 Python 3.10 支持单独 patch 测试侧 Pillow（#41484），且出现过一次「修补易受攻击的集成依赖」被 revert 的往返（#41473→#41481）。
  2. 该 revert 往返可作「下游安全 bump 与兼容性冲突」的工程案例登记，无定量结论。
- 关闭条件：CVE 编号与影响面未核对（revert 原因仅 PR 标题口径）；如需进正文，须查 #41473/#41481 讨论区与 advisory 原文。
