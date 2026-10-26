# 投递：policy optimization 与 RL 系统（2026-10-26 daily）

> 巡检通道：arXiv API（export.arxiv.org）。本批 4 篇 v1 提交日期 2026-10-22~23（周五公告批次），判重后均未见于 `Sources/`，属上一轮（2026-10-25）运行后首次入库。原件 2 份存 `Sources/00-rl/.inbox/originals/`。

## E1 · KnitTrans：rollout→train 轨迹传输降低架构级陈旧度

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32389>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.32389-knittrans-trajectory-transfer.pdf`
- 适用范围：preprint，未经同行评议；覆盖解耦式（disaggregated）LLM RL 训练中 rollout 到 train 的轨迹准入与传输路径（含多模态负载）；不覆盖 colocated 单进程训练与纯算法侧策略更新。
- 证据等级：A
- 可提炼要点：
  1. 提出「架构级陈旧度（architectural staleness）」概念：解耦流水线相对 colocated 执行带来的额外参数版本差，即使 staleness 控制设置相同也存在，并降低学习质量。
  2. 三个设计：约束保留的 mini-batch 准入（提前放行但校验剩余配额容量）、按需轨迹数据访问、大 payload 传输路径协调。
  3. 原文实验口径：相比 train-batch 准入，架构级陈旧度最多降低 93%；多模态负载传输延迟降低约两个数量级，端到端加速最高 5 倍（预印本数据，未复现）。
- 关闭条件：缺第三方复现与开源代码核对；会议版录用或公开系统代码仓库后可关。

## E2 · MS-TTRL：多次解测试时 RL 的频率冲突

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32234>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.32234-ms-ttrl-frequency-conflict.pdf`
- 适用范围：preprint，未经同行评议；覆盖无标注测试实例上多次有效解的测试时强化学习（TTRL）；不覆盖有标注奖励模型场景与单解数学任务。
- 证据等级：A
- 可提炼要点：
  1. 定义「Frequency Conflict」：生成频率同时服务于正确性估计（偏向高频结果）与结果多样性（偏向低频结果）两个相反目标。
  2. 方法：Outcome-Level Self-Verification 提供频率无关的正确性估计，生成频率只保留给多样性；配 Three-State Outcome Cache 与 Candidate State 复用验证结果。
  3. 原文实验口径：两个基准、四个多解任务、三个 backbone、各 5 个随机种子上 Recovery Rate 平均提升 19%+；TTRL-CoCoV 相对 TTRL 不稳定提升，说明轨迹级多样性不等于结果级多样性（预印本数据，未复现）。
- 关闭条件：缺第三方复现；需确认 19% 提升的口径（相对哪个 baseline、哪个任务加权）。

## E3 · PPO-DAZ3：动作置信度与归一化优势双信号自适应裁剪

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32194>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖经典控制基准（LunarLanding 等三项）上 PPO 裁剪阈值自适应化；不覆盖 LLM/RLHF 规模训练与离散大动作空间。
- 证据等级：A
- 可提炼要点：
  1. 核心主张：固定裁剪阈值对所有样本给同一信赖域宽度，与样本对应的策略更新可靠程度无关。
  2. PPO-DAZ3 用两个信号逐样本设定裁剪区间：action confidence（当前策略下所选动作概率）与 update confidence（归一化优势幅度），其余 PPO 管线不变。
  3. 属对既有 adaptive clipping 变体的系统化对比与统一视角，可与本域 policy-optimization 箱内 retry/trust-region 块互相引用。
- 关闭条件：无 LLM 规模实验；需补经典控制之外的实证（如 RLHF/RLVR 迁移）或第三方复现。

## E4 · 条件流模型做离线最大熵 RL 的软最优 Q 估计

- 获取日期：2026-10-26
- 来源 URL：<https://arxiv.org/abs/2610.32125>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖离线数据上最大熵 RL 的软最优 action-value（Q*）估计，环境建模与价值学习分离；不覆盖在线交互与模型无关的策略梯度主线。
- 证据等级：A
- 可提炼要点：
  1. 问题定位：soft optimal Bellman 算子因奖励分布与转移核未知而不可直接评估，估计 Q* 需同时处理环境建模与价值学习。
  2. 方法：用基于 probability flow ODE 的条件扩散模型分别估计条件奖励分布与转移核，得到数据驱动的软最优 Bellman 算子近似，再在深度网络类上最小化经验 Bellman 残差。
  3. 与 offline RL 主线（IQL/CQL 系）处于「模型学习层次」，与既有箱「算法层次」不同层，建议合箱时单独标注。
- 关闭条件：摘要级证据，未取原件与实验数值；需补下载原件或在下一轮巡检中验证实验基准后才可提炼定量结论。
