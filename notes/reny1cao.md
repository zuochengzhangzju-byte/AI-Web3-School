---
timezone: UTC+8
---

# Renyi Cao

**GitHub ID:** reny1cao

**Telegram:** 

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->
今天学习了「AI Agent 入门 —— Hermes 从 0 到 1」。这节课让我更清楚地区分了 chatbot、AI IDE、coding agent 和通用 agent 底座。Hermes 的重点不是单纯聊天或写代码，而是把模型、工具、消息平台、memory 和 skills 连接起来，让 agent 能围绕长期任务持续工作。

我今天最有收获的是 skills 和 memory 的概念：skills 可以理解为可复用的任务说明书，包含角色、流程、边界和输出格式；memory 则用于保存长期背景和偏好。它们共同解决的问题是：agent 不应该每次都从零开始，而应该逐渐沉淀工作方式。

安全上也有一个重要提醒：API key、cookie、secret 不能直接发到聊天或公开笔记里；dangerous command 要单次授权并看清楚；涉及钱包签名、转账、授权和合约写入的动作必须保留人工确认。今天的 proof-of-work 是把 Hermes 课程内容整理进 GitHub 学习仓库，并准备继续做 Agent、Tool Calling、MCP、Memory、Skill 概念卡。
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->

今天参加并整理了「AI 时代 Web3 开发者需要具备的基础知识与架构能力」内容，同时补读了 Ethereum 官方交易文档。今天最大的收获是：AI 并没有降低系统复杂度，而是放大了开发者的基础知识、架构判断和验收能力；Web3 也不是脱离 Web2 的孤岛，真实项目里仍然需要支付系统、链上监听、风控、索引和回调等工程能力。

Web3 部分我重点整理了 wallet 和 transaction 的关键概念：钱包本质上不是钱袋，而是签名器；交易是一段由私钥授权的状态变化。gas 决定执行成本，nonce 决定账户交易顺序，data / call data 决定合约到底被调用了什么。后续做测试网交易前，我会先检查 network、to、value、data、gas、nonce，并坚持“未签名前先做交易模拟”。

今天的 proof-of-work 是把会议纪要和交易参数整理进 GitHub 学习仓库，形成后续 Week 1 概念卡、测试网交易和最小合约实验的基础材料。
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
