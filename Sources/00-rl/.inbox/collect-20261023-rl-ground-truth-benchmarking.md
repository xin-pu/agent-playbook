# 投递：RL 评测的 ground-truth-first 框架（2026-10-23 daily）

## E1 · 用反最优性构造「已知最优解」的 RL 基准

- 获取日期：2026-10-23
- 来源 URL：https://arxiv.org/abs/2610.30954
- 本地原件：`Sources/00-rl/.inbox/originals/arxiv-2610.30954-ground-truth-first-rl-benchmark.pdf`
- 适用范围：preprint，未经同行评议；覆盖 RL 基准方法论——从平滑全可观测到非平滑/部分可观测任务的认证最优值函数构造；不覆盖 LLM 推理类任务的离散环境实例。
- 证据等级：A
- 可提炼要点：
  1. 现有 RL 基准多为相对评测（按回报排名），距最优的差距不可观测，结论易受奖励设计、随机性、超参与模拟器细节影响。
  2. 框架基于 converse optimality：每个任务构造时先认证最优值函数与策略，对学习者隐藏、只用于评测；统一两种模式——连续时间生成器采样认证环境做灵敏度基准，离散时间原生生成器做 oracle 参照对比（optimality gap、regret、policy error）。
  3. 可与 `04-benchmarks` 的 eval-methodology 线互引（合箱时由主流程决定是否在 04 侧加引用指针，本块为唯一登记处）。
- 关闭条件：物理可解释性优势与离散任务（LLM RL）的可迁移性未验证；需读全文的适用范围声明与实例清单。
