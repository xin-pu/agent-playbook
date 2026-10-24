# 投递：评测基准——agent 安全评测与离线验证的可识别性边界（2026-10-25 weekly）

建议主箱：E1 → `04-benchmarks/agent-benchmarks`；E2 → 候选新箱 `eval-methodology`（10-18 周度分析已建议开箱，与 BenchChecker/oracle 审计同族）。

## E1 · AgentPhishing：自适应说服攻击下「检出率」无法推断 agent 安全性的邮件代理基准

- 获取日期：2026-10-25
- 来源 URL：https://arxiv.org/abs/2610.31404
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.31404-agentphishing-email-agent-benchmark.pdf`
- 适用范围：preprint，未经同行评议；覆盖 LLM/VLM 邮件代理在「检出 + 是否服从恶意请求」双指标下的自适应钓鱼攻击评测（9 个 agent）；不覆盖真实邮件流量与网关部署。
- 证据等级：A
- 可提炼要点：
  1. 设定：传统钓鱼数据集为分类检测器设计，未刻画 agent 面对说服性恶意请求的服从行为；AgentPhishing 同时测「识破」与「执行恶意请求」。
  2. 攻击方法：PhishOpt 在固定基准约束+真实性约束下，针对个体 agent 优化可复用的邮件生成 skill，并按 Cialdini 说服原则归纳与失败关联的策略，再合成通用生成 skill。
  3. 定量口径（预印本，未复现）：9 个 agent 评测中 4 个对既有钓鱼邮件保持安全，但对行为自适应的攻击仍脆弱——其中 4 个 agent 的钓鱼检出率低于 10%、恶意请求服从率高于 45%。
  4. 提炼结论：不能从「检出性能」外推 agent 安全；基准应把服从行为作为独立被测面。
- 关闭条件：缺第三方复现与 agent 名单版本快照；会议版录用或公开 leaderboard 更新可关。

## E2 · Post-Audit Mirage：离线审计证据可识别性定理——安全更新与有害更新可对验证器「观测等价」

- 获取日期：2026-10-25
- 来源 URL：https://arxiv.org/abs/2610.31130
- 本地原件：—
- 适用范围：preprint，已被 NeurIPS 2026「Who Verifies the Agents?」workshop 录用（workshop 非主会评审，口径需保留 preprint）；仅摘要可得；覆盖离线验证在授权、调度、共享容量环境下的可识别性极限定理与基准构造；不覆盖在线监控的完整方案评估。
- 证据等级：A
- 可提炼要点：
  1. 定理形态：把标准观测等价/不可区分思想应用于「可执行审计边界」——构造暴露相同验证器可见证据、部署真值相反（隔离记分器记录）的匹配安全/有害生命周期，得到误差-弃权（error-abstention）权衡。
  2. 基准：Post-Audit Mirage 将该边界做成可执行环境，横跨授权（authorization）、调度（scheduling）、共享容量（shared-capacity）三类。
  3. 缓解与残留：IdentifiedRangeMonitor 用新鲜分组标注的危害结果输出 deploy/hold/cannot determine/unsupported；在条件好的场景能恢复缺失区分，但稀有组、小效应、缺观测时仍可能弃权。
  4. 关系：与 10-18 档 oracle 完整性审计（2610.16067）与 DIB-Bench（2610.21135）构成「评测可信度三镜像」——评分器缺陷、部署盲区、离线证据不可识别；这条给出理论界。
- 关闭条件：未取全文，定理假设与弃权率数字未核；workshop 版 PDF 公开后可升级为条款证据。

---

## 台账登记

- AgentVQA（2610.31494，agentic 视觉理解统一基准）与 ColaBench（2610.30989，记忆引导知识获取评测）为窗内候选，因本轮全轮 25 块配额已满且主题偏单线，仅登记标题与链接：https://arxiv.org/abs/2610.31494 、https://arxiv.org/abs/2610.30989
