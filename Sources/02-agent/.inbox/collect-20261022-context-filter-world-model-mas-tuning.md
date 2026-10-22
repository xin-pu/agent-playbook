# 投递：agent 上下文筛选、世界模型引导与 MAS 自动调优（2026-10-22 daily）

## E1 · Signals & Queries：免逐轮 LLM 调用的策略相关性前置过滤

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29326
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖面向用户 agent 的策略（policy）库相关性筛选，为 Parlant 4.0 的第一级过滤器；不覆盖完整记忆写入/淘汰链路。
- 证据等级：A
- 可提炼要点：
  1. 逐轮用 LLM 评估全部候选策略代价高；S&Q 为每个策略离线生成激活样例与 hard negatives。
  2. 用嵌入上的独立 logistic 分类器（仅向量点积）预测相关性，保证高召回前提下先剔除至少 30% 候选策略，再做下游 LLM 评估（预印本数据，未复现）。
  3. 定位是把昂贵的 relevance 评估前移为便宜的静态分类，属 agent 记忆/上下文组装谱系，可并入 `agent-memory-assembly` 相关箱。
- 关闭条件：未读全文，召回率具体数字与策略库规模未知；补 PDF 原件后关。

## E2 · Pitfall Anticipation World Model：黑箱 LLM agent 的环境引导

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29139
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖黑箱 LLM agent 缺乏特定环境内部动力学知识的问题与 world model 引导方案；不覆盖白箱干预或权重级方法。
- 证据等级：A
- 可提炼要点：
  1. 先前 agent world model 主要逐步预测 next observation，成本高且信息量低——多数观测对任务决策无指导性。
  2. 提出以「陷阱预判（pitfall anticipation）」为抽象层的世界模型：预测动作将落入的失败模式而非完整观测，用以 steering 黑箱 agent。
  3. 与 00-rl 侧环境建模证据不同层：这里面向部署期推理时引导，不改策略参数。
- 关闭条件：未读全文，基准环境、成功率增益数字未采集；补 PDF 原件后关。

## E3 · Bayesian Evolutionary Optimization：MAS 拓扑的自动设计与调优

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29276
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖任务特定多 agent 系统拓扑的自动搜索（BigCodeBench 代码生成等评估）；不覆盖运行时动态重编排。
- 证据等级：A
- 可提炼要点：
  1. 框架组合进化算子（生成多样 workflow 图）与贝叶斯优化（把昂贵的评估集中在有希望的候选上）。
  2. 与 LLM 直接选候选的做法不同：用 graph-aware Gaussian Process 加 Expected Improvement 给出显式选择准则。
  3. 属 MAS 设计方法论层，与 `multi-agent orchestration` 既有线索互补，建议人工合箱时评估归属。
- 关闭条件：未读全文，第二评估域（摘要截断处为 "and on"）与预算效率数字未知；补 PDF 原件后关。

## 台账登记（本轮窗内 02-agent 未开箱项）

- 2610.29456 RegoMender（Rego 策略修复多 agent 框架，应用域偏安全策略语言）：https://arxiv.org/abs/2610.29456
- 2610.29330 AgentMonopoly（行为模式与 persona 控制，主题与既有箱层次差异不足）：https://arxiv.org/abs/2610.29330
- 2610.29292 Credit Where Credit Is Due（MAS 归因拓扑搜索；与 00-rl credit assignment 线索交叉，待人工定主箱）：https://arxiv.org/abs/2610.29292
