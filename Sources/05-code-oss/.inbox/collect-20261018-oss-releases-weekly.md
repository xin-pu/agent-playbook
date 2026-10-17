# 投递：开源栈周窗发布（transformers 5.20.0 · OpenAI Agents 0.24.0 · ollama 0.40.5）

> 建议合入箱：E1/E3 → `inference-stack-releases`；E2 → `agent-framework-releases`。本轮为 2026-10-18 weekly 档（窗 2026-10-11 ~ 2026-10-18）。

## E1 · transformers v5.20.0：原生支持 Meta Muse Spark Open 与 InclusionAI Ling 3.0 两个大型 MoE

- 获取日期：2026-10-18
- 来源 URL：https://github.com/huggingface/transformers/releases/tag/v5.20.0
- 本地原件：—
- 适用范围：官方 GitHub release 页（发布 2026-10-15T18:05:36Z）；覆盖该 minor 版新增模型与文档链接；不覆盖 patch 版 v5.20.1（已由 2026-10-17 daily 登记，两页不重复提炼）。
- 证据等级：A
- 可提炼要点：
  1. 新增 Meta Muse Spark Open：多模态 MoE，文本/图像/音频/视频输入、文本输出，816B 总参（每 token 激活 42B），跨模态共享上下文上限 1,048,576 token，面向 agentic coding（多文件编辑、调试、工具调用）训练，checkpoint 提供 BF16 与 NVFP4 两种格式。
  2. 新增 InclusionAI Ling 3.0 Flash（`BailingHybridForCausalLM`，原生支持、免 `trust_remote_code`）：混合 MoE，解码器按 5 层 Kimi Delta Attention（KDA）+ 1 层 MLA 分组，MLA 块用交错 rotary 与 head-wise 输出门，FFN 为路由+共享专家组合——KDA×MLA 分层混合已是可复用的架构配方。
  3. 发布节奏：v5.20.0（10-15）→ v5.20.1（10-16）间隔一天，minor 带新模型、patch 紧跟修稳定性的双节拍。
- 关闭条件：模型能力定量口径在 HF blog/模型卡（本轮按通道规则不整篇搬运）；需要架构级结论时以 `01-dl` 域论文证据为准。

## E2 · openai-agents-python v0.24.0：MCP 注解透传与 run 级工具异常格式化

- 获取日期：2026-10-18
- 来源 URL：https://github.com/openai/openai-agents-python/releases/tag/v0.24.0
- 本地原件：—
- 适用范围：官方 GitHub release 页（发布 2026-10-15T02:20:12Z，changelog 格式）；仅覆盖 0.23.1 → 0.24.0 增量；不覆盖未列变更。
- 证据等级：A
- 可提炼要点：
  1. 特性：转换后的 MCP 工具现在暴露 annotations（#5356）——框架层首次把 MCP 工具注解带入 agents 运行时，与 03-mcp 域「工具注解/发现」线索互为生态证据。
  2. 特性：支持 run 级工具异常格式化（#5326）；缺陷修复：OpenAI conversation session 写入按 API 限额批处理（#5334）——会话持久化开始受服务端写限约束。
- 关闭条件：annotations 语义范围需对照 MCP 规范工具注解条款确认；确认前不写成协议结论。

## E3 · ollama v0.40.5：上架 NVIDIA Nemotron 3.5（混合 Mamba-2/Transformer MoE）与 decision model 云端化

- 获取日期：2026-10-18
- 来源 URL：https://github.com/ollama/ollama/releases/tag/v0.40.5
- 本地原件：—
- 适用范围：官方 GitHub release 页（发布 2026-10-14T19:45:22Z）；仅覆盖 v0.40.4 → v0.40.5 增量；v0.40.6 已由 2026-10-17 daily 登记，不重复。
- 证据等级：A
- 可提炼要点：
  1. 模型侧：NVIDIA Nemotron 3.5 Super 上架——120B 混合 Mamba-2/Transformer MoE（每 token 激活 12B）+ C-RADIO 视觉编码器，支持工具调用、思考开关、上下文至 1M token；紧凑版 Bolt 74B（激活 9B）配 drafter 做投机解码，目标 24GB 单卡。线性/递归混合架构进入桌面推理发行线，可与 `01-dl` 的 attention-architectures 候选主题交叉引用。
  2. 平台侧：decision model 支持云端运行（`clef:cloud` / `clef-flash:cloud`）——与本轮 arXiv 的 JevAgentHarness/System1-Arena「决策模型分担 LLM」线索同向；OpenAI 兼容 Responses 会话含自定义工具调用时续聊不再报错（协议兼容性修复）。
- 关闭条件：Nemotron 3.5 参数与能力口径以 NVIDIA 技术报告为准（本轮未采到原件）；引用具体分数前需回补。

## 台账登记（本轮巡检流水，不产生证据块）

- langchain 系：`langchain==1.4.5`（10-12）、`1.4.6`（10-14）、`langchain-openai==1.7.1/1.7.2`（10-12/14）、`langchain-core==1.6.11`（10-15）在窗，均 patch/minor 无破坏性变更声明；core 线已由 daily 登记 1.6.12，节奏结论并入 E 块引用即可，不单独立块。
- vllm：最新 release v0.31.0（10-05，窗外）；pytorch v2.14.1（09-30，窗外）；llama-index v0.14.25（09-21，窗外）。
- MCP python-sdk v2.3.0（10-02，窗外）；typescript-sdk v2.3.1（10-05，窗外，见 03-mcp 台账）。
- `blog.langchain.dev/rss/`：302 → 营销站 HTML（217KB，非 RSS），沿用 2026-10-17 daily 结论，不作条目源。
