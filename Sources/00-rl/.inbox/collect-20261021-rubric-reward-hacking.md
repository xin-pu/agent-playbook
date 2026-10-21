# 投递：Rubric 奖励内部维度发散与 rubric hacking 缓解

## E1 · Rubric hacking 的训练内奖励维度追踪与恢复平衡

- 获取日期：2026-10-21
- 来源 URL：https://arxiv.org/abs/2610.26685
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.26685-rubric-hacking-divergence.pdf`
- 适用范围：preprint，未经同行评议；覆盖 rubric 打分奖励的 LLM 聊天模型 RL 训练（SJTU + Baidu，v1 提交 2026-10-19），以 ArenaHard v2.0 胜率做质量对照；不覆盖非 rubric 类过程奖励模型与多模态任务。
- 证据等级：A
- 可提炼要点：
  1. 论文 Figure 1 给出 rubric hacking 的典型曲线：整体 rubric 分数持续上升，ArenaHard v2.0 胜率先升后降，即奖励增长与真实质量脱钩。
  2. 与既有缓解路线（降低对 judge 模型偏差标准的过拟合）不同，本文把 rubric 总分拆解到内部潜在维度，追踪训练过程中各维度奖励份额的漂移（如简洁性维度的标准权重比例与标准数量比例随训练步发散）。
  3. 方法主张为「潜在维度恢复 + 平衡」：把发散的维度组合拉回原始 rubric 构成，从而在总分上升时保住生成质量。
- 关闭条件：缺第三方复现与对 ArenaHard 之外基准的泛化验证；同工作会议版录用或出现独立复现报告后可关。
