# 投递：Deep Agents 上下文工程与检索（2026-10-24 daily）

## E1 · LangChain：长程 agent 的「记住但不全塞上下文」五条路

- 获取日期：2026-10-24
- 来源 URL：https://www.langchain.com/blog/context-engineering-deep-agents-remember
- 本地原件：—
- 适用范围：厂商教程/工程博客（B 级），发布 2026-10-24T01:05Z；覆盖 LangChain Deep Agents 的上下文管理设计取向；不覆盖框架无关的方法学比较，也不给出性能定量。
- 证据等级：B
- 可提炼要点：
  1. 问题陈述：长运行 agent 随上下文堆积而退化；博客给出五类手段——offloading（把内容移出上下文）、summarization、skills、subagents、memory。
  2. 与既有 02-agent 记忆箱（memory-assembly、self-evolution）同一主题层次：这是框架侧对「记忆分层」的工程化表述，可作为教程级证据，不作定量结论来源。
- 关闭条件：需要与 agent-memory-state 箱已有证据块对比后由人工决定合并去向；正文引用时应回指具体机制而非博客结论。

## E2 · LangChain：上下文工程从检索开始（Deep Agents harness 的 retrieval 层）

- 获取日期：2026-10-24
- 来源 URL：https://www.langchain.com/blog/context-engineering-starts-with-retrieval
- 本地原件：—
- 适用范围：厂商教程/工程博客（B 级），发布 2026-10-23T21:32Z；覆盖 Deep Agents harness 用于「把对的上下文放进来」的检索技术；不覆盖检索质量基准数字。
- 证据等级：B
- 可提炼要点：
  1. 问题陈述：agent 在笨拙的搜索、超量返回与陈旧数据上浪费时间与上下文窗口；作者主张上下文工程的第一步是检索质量而非窗口大小。
  2. 与 E1 构成一对「写入侧 / 读取侧」材料：E1 讲记忆如何不占上下文，E2 讲上下文如何靠检索进入；合箱时建议同入一个 agent-memory/context 箱。
- 关闭条件：技术清单细节未逐条核对（正文未抓全）；需要与 02-agent 现有 memory 证据块合并评估后再关。
