# 投递：ollama v0.40.7-rc0 预发布（2026-10-18）

> 建议合入箱：`inference-stack-releases`（窗内 05 域唯一新增 release；transformers/langchain 线均窗外或已登记）。本轮为 2026-10-18 daily 档（窗 2026-10-17T01:00Z ~ 2026-10-18T01:00Z，bash+curl）。

## E1 · ollama v0.40.7-rc0：Responses effort 参数放开非思考模型、llama-server 自动推断 draft 投机类型、MLX 支持 PPLX Decider v1.2

- 获取日期：2026-10-18
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.7-rc0
- 本地原件：`Sources/05-code-oss/.inbox/originals/github-ollama-release-v0.40.7-rc0-2026-10-18.json`
- 适用范围：官方 GitHub 预发布（prerelease=true，发布于 2026-10-18T00:28:57Z）；仅覆盖 v0.40.6 → v0.40.7-rc0 增量（3 个 PR）；预发布不计入稳定版结论，正式版发布后对照升级。
- 证据等级：A
- 可提炼要点：
  1. OpenAI 兼容层：Responses API 的 effort 参数允许用于非思考模型（#19010）——Responses 协议兼容面继续收敛，与 02-agent 域「推理档位开关」工具语义口径相关。
  2. llama-server：可自行推断 draft 模型的投机解码类型（#19064）——投机解码的部署负担从手工配置转向服务端自动协商。
  3. MLX 后端新增 Apple PPLX Decider v1.2 支持（#19072）——Apple 侧草稿/决策模型进入桌面发行线的节奏与 v0.40.5 登记的 decision model 云端化（`clef:cloud`）同向。
- 关闭条件：rc 非终版；待 v0.40.7 stable 发布，与本 JSON 原件对照 changelog 一致后即可关块。

## 台账登记（本轮巡检流水，不产生证据块）

- GitHub releases 逐仓核查（窗内命中仅上述 1 条）：vllm 最新 v0.31.0（10-05，窗外）；transformers 最新 v5.20.1（10-16T13:02Z，窗外且 weekly 已登记）；pytorch v2.14.1（09-30，窗外）；langchain 包 `langchain==1.4.6`（10-14，窗外）、`langchain-core 1.6.12` weekly 已登记；llama_index、openai-agents-python、mcp typescript-sdk 窗内无发布。
- 03-mcp 全域窗内无新增：specification 最新 release 仍为 `2026-07-28`（仓名已迁移，API 走 301，下轮引用 `modelcontextprotocol/modelcontextprotocol` 或直接 repository id）；servers 与 ext-skills 窗内 0 commits；A2A 最新 release v1.0.1（2026-05-28）；SDK 发布节奏：ruby v1.8.0 发布于 10-16T07:02Z（早于窗起点约 18h，不立块），csharp/rust/python 窗内仅代码推送无 release；npm `@modelcontextprotocol/sdk` latest 1.32.1（10-05）、pypi `mcp` 2.3.0（10-02）均窗外。csharp/ruby/rust/python-sdk 的窗内 pushed_at 为例行合并噪音，判不满足开箱门槛。
- 00-rl 全域窗内无新增：arXiv 周末公示空窗（6 组查询 0 条，详见 01-dl 投递台账），机构侧 anthropic research/news 列表最新 10-15，窗外。
- 06-news：`anthropic.com/news` 列表时间戳最新 Oct 15（窗外）；`newsletter.semianalysis.com/feed` 最新 10-15 已登记；`qbitai.com/feed` 最新为 10-16T12:54Z（早于窗起点，且 503880/503865/503861 等周五晚篇目属 weekly 窗而非 daily 窗，留给合箱判断）；`openai.com/news` 仍 403（登记不可达，一次即跳）；机器之心仍 JS 渲染不作条目源。
- 04-benchmarks：arXiv 窗内空窗；`tau-bench.com` 本轮实测 HTTP 200（此前可达性表未覆盖该域名），但页面为 JS 渲染、静态抓取无日期化榜单条目，暂不立块，`automation/check-egress.sh` 下轮复测后回写；`swebench.com` 未复查（weekly 已覆盖）；gaia DNS 失败结论沿用。
