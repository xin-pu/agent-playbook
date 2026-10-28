# 投递：知识工作审计基准、GUI 点击判分重定义与交接连续性（2026-10-28 daily）

> 巡检通道：arXiv API（benchmark+agent 查询）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：2610.36405 / 2610.36831 / 2610.36523 均未见于 `Sources/`。原件情况：kw-bench PDF 两次下载均在尾部截断（缺 trailer dictionary，无法 pdftotext），按「失败两次即跳过」放弃，本文件实际 0 原件落盘；候选 31 项中 SO-101/CogArena/ETC-Bench 等降级台账（每域至多 6 来源与全轮 25 块上限）。

## E1 · kw-bench：真实审计/尽调场景考倒前沿 harness，判分不用 LLM judge

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36405>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 coding-agent harness 在「调查型知识工作」（审计、税务、尽调、监管申报、理赔）上的评测——答案已存在但藏在跨系统的不完整不一致证据中，须精确复原；不覆盖创意生成型任务，不覆盖生产系统选型结论。
- 证据等级：A
- 可提炼要点：
  1. 任务构造：首个任务族是跨三代 SAP（遗留 ECC、S/4HANA 迁移中、顾问重设计）的五年 VAT 重建，交付形态为原始系统导出（表头、本地数字格式、部分链接表、零文档）——把「知识工作最贵的部分（调查取证）」做成基准，判分确定性、无 LLM judge。
  2. 结果口径（预印本数据，未复现）：四个 harness（Claude Code、Codex、OpenCode、micro-cc）同一模型 DeepSeek v4.1 Flash、两小时限时——两个独立、模型无关的 harness 交付更高（OpenCode 0.542、micro-cc 0.528），两个大厂 harness 落后（截断处之外，数字未采）。
  3. 主题坐标：与 10-26 agent-science-benchmark-wave、02-agent 域 harness 证据线（E2 of `collect-20261028-agent-errors-harness-attrition-attacks.md`）互指——「harness 差异 ≥ 模型差异」在评测侧与机理侧同时出现。
- 关闭条件：原件两次截断，本地无 PDF；大厂 harness 具体分数与失败模式分类未采——下轮重下补件后才能提升任何定量口径。

## E2 · Right Click, Wrong Box：GUI grounding 按「点击后果」而非「框内命中」判分

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36831>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 ScreenSpot-v2 饱和（头部 grounders 93~96%，新旧模型差距约 1 分）之后 GUI grounding 判分规则的重定义与自动执行判官；不覆盖非 web GUI（原生应用）与坐标级鲁棒性数字。
- 证据等级：A
- 可提炼要点：
  1. 问题：基准只在单个标注框内判点击正确，而界面常把一个动作暴露在多个元素上（重复链接、复选框标签、logo 旁标题）——「框没错，规则不完整」，剩余 1 个百分点的误差结构才是现在有用的信息。
  2. 方法：把「执行该点击与点击标注目标产生相同后果」定义为正确；探针每页执行并指纹化约一千次点击，生成 outcome maps 与面向 live web 应用的 execution judge。
  3. 主题坐标：与本域 10-19 ms-eval-mobile-agent、02-agent 域 10-23 GUI-world-traces 投递同线；判分规则重定义可作「评测完整性」箱（10-20 benchmark-integrity-coding）的方法学证据。
- 关闭条件：无原件；execution judge 的误判率与成本未核，引用「旧规则系统性低估」前须回原文实验节。

## E3 · HSC-Bench：agent 交接后的任务接管——证据恢复与状态延续双维评测

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36523>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖长任务中模型间责任移交（handoff）后接收方对先前决策/观察/动作的继承质量评测；不覆盖多 agent 协作的整体编排收益，不覆盖记忆写入策略。
- 证据等级：A
- 可提炼要点：
  1. 缺口界定：任务成功率与记忆保留分数都无法把「交接时保留了什么信息」与「接收方怎么继续工作」连接起来——需要专门测 task takeover。
  2. 构造（原文口径）：HSC-Bench 共 1,039 个任务，两个互补维度：恢复相关仓库证据（repository evidence）+ 从既有会话/工具/文件工作状态继续推进（预印本数据，未复现）。
  3. 主题坐标：与本域 10-25 interaction-longitudinal-bench（纵向交互）及 02-agent agent-memory 线互补——交接是纵向评测的离散切片；模型无关性未核。
- 关闭条件：无原件；任务构建流程与污染风险未核；引用维度得分前须回原文。

## 台账登记（未过开箱门槛或配额所限，暂不建块）

- SO-101 Bench: Accessible Spatial Manipulation（2610.36420，published 2026-10-27）<https://arxiv.org/abs/2610.36420>
- CogArena: Benchmarking Multimodal Agents on Interactive Behavioral Experiments（2610.36484，published 2026-10-27）<https://arxiv.org/abs/2610.36484>
- ETC-Bench: Multilingual Evaluation-Side Transcript Canonicalization（2610.36527，published 2026-10-27）<https://arxiv.org/abs/2610.36527>
- InfraDev: Can Coding Agents Develop AI Infrastructure（2610.36589，published 2026-10-27）<https://arxiv.org/abs/2610.36589>
- Benchmarking LLM Agents for Behaviorally Adequate Test Generation（2610.36584，published 2026-10-27）<https://arxiv.org/abs/2610.36584>
