# 投递：MoE 服务通信卸载与确定性路由（2026-10-28 daily）

> 巡检通道：arXiv API（mixture of experts 查询，同轮 `collect-20261028-kv-state-compression.md` 头部说明）。窗口 2026-10-27T00:00Z~2026-10-28T01:10Z。判重：2610.36339 / 2610.34721 均未见于 `Sources/`（与 10-20 moe-routing-training-systems、10-26 投递的 scoutroute 线为不同 arXiv ID）。

## E1 · INC-MoE：把 dispatch/combine 两个集合通信卸载到交换机

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.36339>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖专家并行（EP）MoE 服务里 dispatch/combine 两个关键路径操作的在网计算（in-network）卸载与重叠；不覆盖训练期并行策略，不覆盖非交换机内 reductions 的通用 All-to-All 方案对比数字。
- 证据等级：A
- 可提炼要点：
  1. 问题：EP 服务中 dispatch（把 token 发往选中专家所在加速器）与 combine（把专家输出送回 token 归属端）都在关键路径上，多机部署可主导 MoE 层延迟。
  2. 方案（原文口径）：dispatch 用交换机侧多播做 in-network AllGather，combine 用交换机侧归约做 in-network ReduceScatter，两个集合通信互相重叠并与专家计算重叠；端主机与交换机之间用消息语义交互。
  3. 主题坐标：与本域 moe-routing 系既有箱同属「MoE 系统瓶颈从路由算法转向搬运」的推进线；性能数字在截断处之外，登记前须回原文。
- 关闭条件：无原件，加速比与交换机硬件依赖（型号/可编程性要求）未核对；下轮补 PDF 或人工合箱时读实验节再定。

## E2 · Prefetch-Steered Routing：逻辑缓存令路由输出与传输时序解耦

- 获取日期：2026-10-28
- 来源 URL：<https://arxiv.org/abs/2610.34721>
- 本地原件：—
- 适用范围：preprint，未经同行评议；覆盖 GPU 显存放不下 MoE 权重时 batch-1 解码的 host-memory 拷贝瓶颈，以及 cache-aware 路由与异步预取耦合导致的评测失真问题；不覆盖多 batch 服务吞吐场景。
- 证据等级：A
- 可提炼要点：
  1. 评测有效性发现：cache-aware 路由偏向常驻专家、叠加异步预取后，模型输出取决于传输时序——不复现该时序的 harness 已不再评测「真正部署的那个模型」；与 02-agent 域 harness 证据线跨箱互指。
  2. 方案：PSR 让路由只看确定性逻辑缓存——每层每 token 至多插入 n 个由「下一层路由器」预测的专家，物理拷贝只影响延迟不影响输出，从而把「可复现」与「省拷贝」解耦。
  3. 实验口径：OLMoE-1B-7B、50%/25% 专家常驻配置下验证（结果数字在截断处，不登记）。
- 关闭条件：无原件，n 值、延迟-质量权衡数字未核；引用「时序依赖破坏评测」论点前须回论文实验节或复现。
