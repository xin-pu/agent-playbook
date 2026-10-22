# 投递：agent 评测新基准窗内三题（CrashGym、GenXR-Bench、VeeReview）（2026-10-22 daily）

## E1 · CrashGym：把「实验价值」测为可避免决策损失的 agent 模拟器

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29245
- 本地原件：`Sources/04-benchmarks/.inbox/originals/arxiv-2610.29245-crashgym-agent-experimentation.pdf`
- 适用范围：preprint，未经同行评议；覆盖 LLM agent 在确定性可回放限价订单簿市场中的实验-决策评测；不覆盖真实市场因果结论。
- 证据等级：A
- 可提炼要点：
  1. 评测对象不是答对率而是「实验的决策价值」：agent 先在实验室 realization 查询干预实验，再在独立种子的目标 realization 上被打分，regret 通过直接模拟所有备选干预计算，无人类或模型裁判。
  2. 放大通道（持续价格冲击、流动性撤退、保证金强平、策略组合演化）做成可逐级开关的显式机制，模拟细节由它支撑的决策质量来评判。
  3. 定量口径（预印本数据，未复现）：24 个新采样 world 的前瞻研究中，实验室访问使唯一有完整记录部署（Luna）的平均 regret 从 8.878 降到 3.785，配对降幅 5.092（world-bootstrap 名义 95% 区间 1.028–9.507），约为 OBSERVEONLY 均值的 57.4%。
  4. 策略组合内生演化的实验室相对固定组合实验室未确立优势；另两个部署的前瞻比较不完整（作者自述）。
  5. Columbia/Cornell/NYU/Hithink RoyalFlush 合作（Lu、Cheng 等）。
- 关闭条件：前瞻研究仅 1/3 部署完整，需作者补完或第三方复现；补齐另两个部署的 prospective 结果后可关。

## E2 · GenXR-Bench：面向交互式 XR 开发的 coding agent 基准

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29014
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 coding agent 在 3D 动态环境（用户运动、空间输入、环境感知耦合）下的端到端 XR 应用开发评测；不覆盖传统 Web/后端编码能力对比。
- 证据等级：A
- 可提炼要点：
  1. 定位为首个 XR 端到端 coding agent 基准：112 个专家编写任务，跨 24 类特性实现（摘要截断处的口径）。
  2. 评测动机：runtime 鲁棒性同时依赖连续用户运动、空间输入与环境感知，超出单文件/仓库级静态评测的维度。
  3. 与既有 SWE-bench 系（`collect-20261020-benchmark-integrity-coding`）互补：把「可交互运行时」纳入被测面。
- 关闭条件：未读全文，任务分布/评分器细节/参评模型成绩未采集；补 PDF 原件后关。

## E3 · VeeReview：用 V-Model build-verify 配对度量 agent PR 的验证证据

- 获取日期：2026-10-22
- 来源 URL：https://arxiv.org/abs/2610.29143
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 agent 生成 pull request 与人类 PR 的「构建-验证配对」测量方法；不覆盖合并后缺陷率追踪。
- 证据等级：A
- 可提炼要点：
  1. 主张现有 coding agent 基准与 PR 结果研究没有直接评估「验证证据是否针对所提变更」，提出以 V-Model 的四类 build-verify 对作为测量单元。
  2. 方法混合确定性信号与 LM judge：三类配对用确定性信号约束模型判断，Module Design 配对由 diff 与仓库树规则决定——可作为「降低 judge 漂移」的方法学样本。
  3. 支持 agent-authored 与 human-authored 变更的对比口径，属评测方法论（openbox）谱系。
- 关闭条件：未读全文，四类配分的实测分布与判准一致性数据未采集；补 PDF 原件后关。

## 台账登记（本轮窗内 04-benchmarks 未开箱项）

- 2610.29189 Reasoning-Search-Augmented LLMs（操作性综述+基准分析，综述件与一手基准不同层次，来源单一暂不建块）：https://arxiv.org/abs/2610.29189
