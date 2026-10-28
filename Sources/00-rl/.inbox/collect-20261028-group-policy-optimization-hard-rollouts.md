# 投递：组相对策略优化与难题 rollout 信号（2026-10-28 daily）

> 巡检通道：arXiv API（cat:cs.LG+RL / RLHF+GRPO / policy optimization 三查询顺序抓取，首轮限流后降频重发成功）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z（daily 档，覆盖昨日投递后的公告批次；arXiv 按 published ≥ 2026-10-26 圈定候选，再逐 ID 判重）。判重：2610.36807 / 2610.36849 / 2610.34951 及本轮全部 2610.36x ID 均未见于 `Sources/`。原件 2 份存 `.inbox/originals/`（2610.36807 首次下载截断，重下后 `%%EOF` 与 pdftotext 校验通过）。

## E1 · SetGRPO：把 grader 随机性纳入组归一化的集合式校准

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36807>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.36807-setgrpo-calibration.pdf`
- 适用范围：preprint，未经同行评议；覆盖 rubric 评分下开放式任务 GRPO 训练里「评分器随机性扰动整组训练系数」的校准方法；不覆盖可验证二值奖励（RLVR）主线，也不覆盖部署期评分器选型。
- 证据等级：A
- 可提炼要点：
  1. 机制分析：GRPO 在组内联合归一化奖励再组合 response 级梯度，因此评分偏差会移动整组训练系数、产生「policy-dependent」的更新改变，单看分数差异不足以刻画；选择性执行还会改变被保留更新的方向反转风险。
  2. 方法三模块（原文口径）：Joint Reward Set Calibration 构造训练系数的联合不确定集；Geometry-Guided Safe Recovery 把候选系数映射进当前策略局部更新几何、求每组最大安全恢复比；Selective Risk-Gated Optimization 用独立风险标定选全局阈值，控制被接受更新的条件方向反转风险同时保留 GRPO 原目标。
  3. 理论与实验：交换性假设下给出联合系数集的有限样本边际覆盖与跨阈值同步风险控制；在三个领域共十个开放式基准上评测（定量数值见原文，预印本数据，未复现）。
- 关闭条件：缺第三方复现与代码/权重公开；同组会议版录用或公开复现后可关。

## E2 · PICO：全部 rollout 失败时的策略兼容联合解码

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36849>
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.36849-joint-decoding-hard-rollouts.pdf`
- 适用范围：preprint，未经同行评议（封面标注 "Preprint. Under review."，作者 USTC/腾讯/上海AI实验室）；覆盖 RLVR 在超出模型能力难题上的「学习悬崖」（全失败组优势坍缩为 0）与专家轨迹注入；不覆盖多模态与在线部署场景。
- 证据等级：A
- 可提炼要点：
  1. 问题界定：当一组 rollout 全失败时，GRPO/RLOO 等组相对估计器把更新坍缩为零优势；直接混入专家轨迹则因其落在学生低概率区，存活更新要求大幅参数偏移并退化为表面模仿——学习信号必须同时「可验证正确」且「与当前策略足够兼容」。
  2. 方法（PICO，Policy-Compatible RL）：分布约束的联合解码——教师（以专家数据为条件）与学生的高概率 token 取交集构造候选集，按学生相对概率采样保留自身偏好；动态 top-k 机制把联合采样分布约束在有限散度预算内。
  3. 实验：数学与通用推理基准上稳定优于标准 RLVR 与既有专家引导基线，另在 agentic 任务上验证泛化（预印本数据，未复现；消融确认 rollout 质量与学生策略兼容度的权衡需显式控制）。
- 关闭条件：缺第三方复现；与 10-19 投递的 credit-distillation、10-23 mixpolicy 线是否同构需人工比对方法节。

## E3 · Rollout 一致性作为正确轨迹质量信号：低一致链伪推理更多

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.34951>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 GRPO 训练模型同一问题「正确但一致性不同」的推理链质量对比；不覆盖错误轨迹的筛选策略，不覆盖训练动力学结论。
- 证据等级：A
- 可提炼要点：
  1. 设计：对同一问题取最高一致与最低一致的正确回答链做盲评配对分析，共 126 对；低一致链含伪推理的比例更高（35% vs 22%），形态包括内部自相矛盾与误用题目信息（预印本数据，未复现）。
  2. 定位：对「rollout 多样性越高越好」的既有口径提供反向修正——组内一致度可作廉价的质量信号；与本域 10-18 投递的 rollout-diversity-efficiency（adaptive replay）线互补，合箱时同箱对照。
  3. 本轮未下原件（原件配额用于 E1/E2 与审核/基准域），定量口径引用时须回指论文原文。
- 关闭条件：缺原件全文核对配对构建与盲评流程；下轮按配额补 PDF 后可关「口径未核对」部分。

## 台账登记（未过开箱门槛，暂不建块）

- FOCUS: Active Critic Learning for Long-Horizon Language Model Agents（2610.35801，published 2026-10-26）<https://arxiv.org/abs/2610.35801>——critic 主题与本轮 `collect-20261028-reward-audit-harness-critic-rl.md` E3（S3AC）同线，块数配额所限降级台账。
- Frequency-Uniform Log-Regret Reinforcement Learning for Diffusions（2610.36758，published 2026-10-27）<https://arxiv.org/abs/2610.36758>——diffusion 上的策略优化，主题归属（00 或 01-dl）待定，先登记。
- Priority-Preserving Advantage Aggregation for Multi-Reward Policy Optimization（2610.34862，published 2026-10-26）<https://arxiv.org/abs/2610.34862>——多奖励聚合，与 SetGRPO 主题相邻，待积累后再决定并箱或独立成块。
