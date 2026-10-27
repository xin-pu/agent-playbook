# 投递：01-dl / 00-rl 窗口扫描与台账登记（2026-10-27 daily）

> 巡检通道：arXiv API（export.arxiv.org，5 组查询顺序抓取，其中 `cat:cs.LG AND abs:"reinforcement learning"` 首发超时后单发重试成功）。窗口 2026-10-26 01:00Z~2026-10-27 01:00Z。本轮 00-rl、01-dl 无可开箱包级新增，仅登记台账。

## 台账登记

- 00-rl：RL 关键词两路查询（GRPO/RLHF/reward model/policy optimization 与 cat:cs.LG/cs.AI AND reinforcement learning，共 120 条去重记录）最新 submitted 批次止于 2026-10-24T19:49Z，该批次已于 2026-10-26 daily 轮登记（`collect-20261026-policy-optimization-rl-systems.md`），本轮无新增。
- 2026-10-25：`2610.33988`（Hybrid Mamba-Transformer Network for Single-Shot 3D Reconstruction from Fringe Patterns，cs.CV）——Mamba/Transformer 混合架构命中 01-dl 关键词，但应用域为条纹投影计量（metrology），与既有箱（MoE routing、量化、推理效率）主题距离远；未下载原件、单一来源，不满足开箱门槛，只登记标题与链接 <https://arxiv.org/abs/2610.33988>，等同类混合架构 LLM 向证据积累后合并评估。
- 2026-10-25：`2610.33964`（QECGBERT: ECG Foundation Model via VQ-VAE Waveform Tokenization，cs.LG）——医疗生理信号基座模型，超出 01-dl 覆盖（深度学习与模型架构以语言/多模态为主），不建块，登记链接 <https://arxiv.org/abs/2610.33964>。
- 通道记录：arXiv API 首发查询超时一次（28s），按「单条顺序 + 间隔 sleep」策略重试一次成功，不影响结论；openreview/semanticscholar/huggingface papers 未探测（沿用 2026-10-09 可达性表结论：不可达，不浪费超时）。
