---
timezone: UTC+8
---

# juyixin98

**GitHub ID:** juyixin98

**Telegram:** 

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->
📝 今日核心进展：完成了 RPC Agent 最小实验。使用公共以太坊 RPC 节点，通过 eth\_blockNumber / eth\_getBalance / eth\_gasPrice 三个方法，演示了 Agent 如何查询真实链上数据。关键理解：Agent 不直接「知道」链上状态，而是通过 JSON-RPC Tool Use 获取——这和 Web2 的 API tool 本质相同，区别在于数据格式（hex/Wei）和写操作的安全边界（需要私钥签名）。

📎 实验代码：[https://github.com/juyixin98/ai-web3-school-cohort-0/tree/main/experiments/001-rpc-agent](https://github.com/juyixin98/ai-web3-school-cohort-0/tree/main/experiments/001-rpc-agent)
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->

📝 今日学习了 AI × Web3 Handbook 的 Agent 和 Chain-aware Context 章节，重点理解了：1）Agent 如何从「回答问题」进入「多步执行流程」；2）链上状态（区块、交易、合约事件）如何被组织成 Agent 可理解的上下文。下一步计划深入 Web3 Tool Use，尝试让 Agent 直接调用链上 RPC。
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
