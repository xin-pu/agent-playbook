# 投递：ollama v0.40.12 转正与 langchain-anthropic 1.7.7（2026-10-28 daily）

> 巡检通道：GitHub API releases（8 仓逐条顺序）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：`langchain-anthropic==1.7.7` 与 v0.40.12 stable 条目未见于 `Sources/`；vllm（最新 v0.32.0，10-18，已登记）、pytorch（v2.14.1，09-30）、transformers（v5.21，昨日已投）、python-sdk（v2.3.0，10-02）、typescript-sdk（v2.4.0，10-23）窗口内无新增。ollama v0.40.12-rc0 本体已由昨日 `collect-20261027-oss-release-wave.md` E2 登记，本文件只投「RC→stable 转正」增量。

## E1 · ollama v0.40.12 stable：LFM3 家族入仓，昨日 RC 条目按关闭条件转正

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/ollama/ollama/releases/tag/v0.40.12>
- 本地原件：—
- 适用范围：官方 stable release（prerelease=false，tag created 2026-10-27T15:47Z；GitHub published_at 字段保留 RC 起草时刻 00:07Z，两字段并记）；覆盖 stable 发布说明首节（Liquid AI LFM3 家族）；RC 条目里的 MLX 清单是否并入 stable 正文未逐条核对，不覆盖模型性能数字。
- 证据等级：A
- 可提炼要点：
  1. 模型面（原文口径）：收录 Liquid AI LFM3 家族，定位「本地 agent、tool calling、结构化输出」，基于 Liquid 新三混合（tri-hybrid）架构——lfm3（1.7B 文本、256K 上下文）、lfm3-vl（图像理解）、lfm3-audio（18 语种语音识别/翻译/TTS）、lfm3-omni（图文音频）。
  2. 流程证据：直接回答昨日 E2 的关闭条件——stable v0.40.12 已发布，该 RC 引用应替换为本条目；且发布说明首节与 RC 清单不同（stable 主打 LFM3、RC 主打 MLX 修复），说明 RC→stable 期间正文被重写合并，引用 changelog 时不能把两者当同一文本。
  3. 节奏：延续 v0.40.11（10-24）→ RC（10-27 晨）→ stable（10-27 深夜 UTC）的同日转正，比既有「约 3 天 RC 周期」更快，单样本不足以改口径，合箱时标注。
- 关闭条件：stable 正文是否含 RC 四条 MLX 变更未逐条核对；引用具体 PR 号前需拉全 body 比对。

## E2 · langchain-anthropic 1.7.7：reasoning effort 可观测性与 partner 包依赖治理

- 获取日期：2026-10-28
- 来源 URL：<https://github.com/langchain-ai/langchain/releases/tag/langchain-anthropic%3D%3D1.7.7>
- 本地原件：—
- 适用范围：官方 release changelog（2026-10-27T23:48Z 发布，标题即 tag）；覆盖 1.7.6 以来 5 条变更清单；无 breaking change 条目，不覆盖行为语义细节（需读 PR diff）。
- 证据等级：A
- 可提炼要点：
  1. 可观测性线索：`fix(anthropic): trace resolved reasoning effort`（#41536）——把「解析后的 reasoning effort」纳入 trace，与本域既有 agent 运行时控制线（LangSmith Gateway，10-22 已投）同族：推理档位成为一等可追踪参数。
  2. 依赖治理：放宽第三方依赖上界（#41407）+ 修复部分 partner 包依赖（#41266）+ certifi 升至 2026.10.19（#41391）——延续 langchain-openai 1.7.3（昨日 E3）的 partner 包高频小步修补节奏。
  3. 阈值口径：本轮命中「new API」不足、「breaking change」无，仅按「release」要素登记进 agent-framework-releases 既有箱线。
- 关闭条件：reasoning effort trace 的字段名与 LangSmith 呈现层未核对；引用前查 #41536 diff。
