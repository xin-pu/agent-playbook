# 投递：提示注入的注意力门控防线、用户压力下的认知警觉与 agent 记忆（2026-10-29 daily）

> 巡检通道：arXiv API（10-27 UTC 批次）+ `www.langchain.com/blog/rss.xml`（RSS pubDate 为批次页刷新时间，条目时间以列表卡与页面正文口径交叉确认）。

## E1 · Heads of Security：学习型 per-head 注意力门控提升提示注入鲁棒性

- 获取日期：2026-10-29
- 来源 URL：<https://arxiv.org/abs/2610.37657>
- 本地原件：`Sources/02-agent/.inbox/originals/arxiv-2610.37657-hos-prompt-injection-gates.pdf`
- 适用范围：preprint，未经同行评议；开放权重模型（Llama-3.3-70B-Instruct、GPT-OSS-20B）的间接提示注入防御；架构内指令-数据分离路线；不覆盖闭源前沿模型与多模态注入面。
- 证据等级：A
- 可提炼要点：
  1. 机制：少量可学习的 per-head 注意力门控，规定各头在受信/不受信 token 间重分配注意力，使模型能对不可信内容推理而不执行其中指令。
  2. 对抗指标：黑盒 RL-Hammer 对 GPT-OSS-20B 达 97% ASR、对 SecAlign 85%，对 HoS 仅 10%；白盒 Claudini（经 autoresearch 强化）在 HoS 上达到同等 ASR 需约 3× FLOPs。
  3. 效用保持：标准多选基准保持基座效用；SecAlign 与 ASIDE 在 few-shot 退化；ASIDE 在 agentic 工具使用上仅约 10% 效用。
  4. 与 `2610.36108`（MCP 注入攻击，2026-10-28 投递）构成「攻击面 vs 架构防御」配对，合箱互引。
- 关闭条件：预印本定量结论未复现；防御对自适应攻击的长期稳定性存疑（原文自述 prompt injection 仍 largely unsolved）；需第三方红队复现或会议版后关。

## E2 · 更正还是操纵：测量用户压力下 LLM agent 的认知警觉

- 获取日期：2026-10-29
- 来源 URL：<https://arxiv.org/abs/2610.36453>
- 本地原件：—
- 适用范围：preprint，未经同行评议；用户反驳场景下 agent 的坚持/改口决策；覆盖「改口倾向 vs 辨别能力」的度量问题；不覆盖多轮长任务中的累积操纵与安全事件。
- 证据等级：A
- 可提炼要点：
  1. 问题定位：既有工作显示模型被用户质疑时频繁放弃正确答案，但分不清它是「无法区分更正与操纵」还是仅「改口倾向不同」。
  2. 框架：把用户分歧建模为两类（真更正 / 操纵企图），测量 agent 的认知警觉（epistemic vigilance）（方法细节在正文）。
  3. 同批次邻近工作 `2610.36435`（用户在场改变谈判 agent 行为，PRESENT 受控评测）主题相邻，未入选本轮配额，见台账。
- 关闭条件：摘要级掌握；需补读正文核对度量定义与基线，或下一轮补原件后关。

## E3 · Proactive Memory：事件驱动 agent 的行为规律验证与适用性评估

- 获取日期：2026-10-29
- 来源 URL：<https://arxiv.org/abs/2610.36967>
- 本地原件：—
- 适用范围：preprint，未经同行评议；主动式（proactive）LLM agent 的记忆组织：近期事件 + 累积行为规律；不覆盖跨会话长期个性化与隐私治理场景。
- 证据等级：A
- 可提炼要点：
  1. 批评口径：现有方法偏重近期上下文或相关记忆检索，对「反复出现的行为规律是否已被验证、是否适用于当前事件」支持有限。
  2. 方法：ProactMem 把历史组织为近期事件与规律两层，显式做规律验证与当前事件适用性评估（机制细节在正文）。
  3. 归属：并入本域 `agent-memory-*` 主线（2026-10-20/21/25 多篇投递），与 `2610.36652`（DiscernMem，缺陷感知记忆修正，见台账）互补。
- 关闭条件：摘要截断，未取得实验数值；补读正文后关。

## E4 · LangChain 官方：用 OpenWiki 与图谱构建证据落地的 agent 记忆层

- 获取日期：2026-10-29
- 来源 URL：<https://www.langchain.com/blog/building-agent-memory-openwiki-graphs>
- 本地原件：—
- 适用范围：官方博客实践文（B 级；列表页标注 2026-10-28，RSS pubDate 为批次刷新时间不可作精确判据）；覆盖银行/保险等「政策频繁修订/取代」场景下以 wiki 作持久记忆层的测试；不覆盖通用记忆评测基准与量化对比。
- 证据等级：B
- 可提炼要点：
  1. 定位：持久记忆层保存知识与关系供跨任务复用；缺失时 agent 每个问题都要重建理解，昂贵且易错。
  2. 组件：OpenWiki（开源 wiki 编译器）被作为该记忆层测试；在「需要跨来源连接」的问题上 wiki 改善了表现（数值在正文，页内未取到摘要级数字）。
  3. 通道口径：与 `collect-20261027-langchain-company-harness.md` 头注的 RSS 时间警示一致，本轮继续以列表卡日期 + 正文双口径登记。
- 关闭条件：厂商自述、无第三方验证；若需支撑「记忆层」结论，需补 A 级评测证据（可与 `2610.36967`、`2610.36652` 交叉），本块仅作工程实践参考。

## 台账登记

- 配额受限顺延（下轮候选）：`2610.36435`（PRESENT：用户在场对谈判 agent 行为的受控评测）、`2610.36652`（DiscernMem：多-agent 记忆缺陷修正与时机学习）、`2610.37624`（CrossProfile：群体决策记忆压缩失败诊断，60 模板基准）、`2610.37055`（Blindfold：审计币保密性）、`2610.37405`（Clearing the FoG：KG agent 证据追溯）、`2610.37242`（流程感知知识图谱调用企业 API）、`2610.36660`（population-centered agent evolution）、`2610.37649`（LongChang：自由探索发现物理定律）、`2610.36713`（EvoSpeakerMem）、`2610.37319`（AnalogScout）、`2610.36444`（RouteDRAG）。
- `www.langchain.com/blog/proactive-agents`（How to Build Proactive, Always-On Agents，cron 驱动的常驻 agent，列表卡日期 10-27/10-28 两种配对冲突未能精确判日）与 `own-your-intelligence`（10-27，观点文）：判日存疑，暂记台账，下轮以条目页复核后再决定是否落块。
- `blog.langchain.dev/rss/` 仍 302 到 Webflow HTML 列表页（无 `<item>`），继续建议人工主流程回写 `web-sources.md` 用 `www.langchain.com/blog/rss.xml`，本代理不改。
