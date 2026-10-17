# 投递：MoE 路由的探索困境与离策略漂移（moe-routing 追加）

> 建议合入箱：`moe-routing`（`Sources/01-dl/moe-routing/moe-routing-source.md`）。本轮为 2026-10-18 weekly 档。

## E1 · MirrorMoE：细粒度专家 × 共享专家的「探索困境」——共享专家压制了细粒度分段本应带来的组合表达力

- 获取日期：2026-10-18
- 来源 URL：https://arxiv.org/abs/2610.22353
- 本地原件：`Sources/01-dl/.inbox/originals/arxiv-2610.22353-moe-routing-exploration.pdf`
- 适用范围：preprint，未经同行评议；覆盖现代 MoE 两大主流设计（fine-grained expert segmentation 与 shared experts）在路由探索上的相互作用；不覆盖具体训练吞吐与部署成本。
- 证据等级：A
- 可提炼要点：
  1. 结构矛盾定位：细粒度分段靠固定激活率下更多专家组合提升表达力，但路由空间组合爆炸意味着更强的探索需求；共享专家（每 token 激活）压低 token 表征差异，反而使路由更不探索——两者互相拆台，细粒度的表达力收益在实践中可能兑现不了。
  2. 方案 MirrorMoE：以 token-adaptive 抑制「不必要专家」来收缩探索空间，正面处理两设计的冲突。作者单位组合（ETH/HKU/MPI/CMU 线）提示为方法学工作而非厂商报告。
  3. 对既有箱的增量：`moe-routing` 首轮登记了路由解释与门控设计，本块补上「路由空间探索」这一此前未覆盖的失败轴；与 Router Drift Control（本文件 E2）一为结构层、一为训练层，可作对照行。
- 关闭条件：定量收益需原件实验表核对（本轮只提炼了摘要与引言口径的机制结论）；缺第三方复现。

## E2 · Router Drift Control：routing replay 有梯度偏差，rollout-训练路由分歧本身就是信号

- 获取日期：2026-10-18
- 来源 URL：https://arxiv.org/abs/2610.21682
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 MoE 在离策略 RL（训练-推理失配、mini-batch、异步）下的 router drift 抑制；不覆盖非 MoE 模型的 off-policy 修正。
- 证据等级：A
- 可提炼要点：
  1. 对既有修正手段的批评：Rollout Routing Replay（R3，训练时复用 rollout 阶段专家选择）会丢「训练路由选中但 rollout 未选」专家的贡献，引入梯度偏差——MoE×RL 的失配不止是权重问题，还是路由决策问题。
  2. RDC 用 rollout-训练路由分歧信号来控制漂移；与 00-rl 本轮 E2（token 级重要性采样）处于同一「异步 RLVR 失配」问题族，但作用在路由层，提炼去向建议两处互引。
- 关闭条件：未取原件，机制描述止于摘要；需下载 PDF 核对偏差分析定理与实验幅度，或等复现后可关。

## 台账登记（本轮巡检流水，不产生证据块）

- MoE 混合精度量化簇：`2610.20353`（对比校准）、`2610.20826`（路由统计不可作量化敏感度代理，负面结果）、`2610.19232`（Spectral-MoE 稠密转稀疏的逐层利用率）——与 `model-compression` / `moe-training-efficiency` 候选主题吻合，建议下轮成簇开箱；其中 20826 的「路由统计不可靠」与 E1/E2 构成同一主题的三角证据。
- `2610.20247`（多语言 MoE 容量-计算分配）、`2610.19975`（LatentLoop 循环 MoE 非对称计算）：留档。
- 服务侧（暂不入库，属 `01-dl` 边缘）：`2610.21500`（远程 KV 层反而慢于 GPU）、`2610.18451`（FastEEP 弹性专家并行）。
- 03 域投递中「spec 主仓 301 更名」一条已登记在 `Sources/03-mcp/.inbox/collect-20261018-mcp-weekly.md` 台账，此处不重复。
