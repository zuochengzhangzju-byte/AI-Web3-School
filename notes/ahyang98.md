---
timezone: UTC+8
---

# ahyang

**GitHub ID:** ahyang98

**Telegram:** @ahyangchen

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-25
<!-- DAILY_CHECKIN_2026-05-25_START -->
```yaml
title: 链感知上下文（Chain-aware Context）
created: 2026-05-25
updated: 2026-05-25
type: concept
tags: [ai, web3, context, architecture]
sources: [raw/articles/链感知上下文（Chain-aware Context）.md]
confidence: high
```

# 链感知上下文（Chain-aware Context）

## 概述

Chain-aware Context 指的是让 AI 在回答或行动前，能看见正确的链、地址、合约、交易、事件、余额、授权和数据来源，而不是只靠用户一句话猜测链上状态。

## 为什么要学

普通 AI 上下文来自文档和聊天历史。AI×Web3 多了一层：**链上状态持续变化，且直接影响资产和权限**。

如果 Agent 不知道当前 chain id、合约地址、ABI、用户授权、交易历史，就可能给出错误建议甚至生成危险交易。

## 第一性原理

> **模型不能凭语言记忆判断链上事实，链上事实必须从工具和索引层读取。**

### 三项原则

1.  **链上状态有时间性** — 同一地址的余额、授权、仓位随区块变化
    
2.  **上下文要带来源** — 合约地址、区块号、交易哈希、explorer 链接都应可追溯
    
3.  **上下文要区分事实和解释** — 工具返回事实，模型负责解释，不要把模型猜测当事实
    

## 上下文类型

| 上下文 | 难度 | 说明 |
| --- | --- | --- |
| On-chain Data | 初级 | 余额、交易、日志等链上可验证数据。需带 chain id、block number |
| Contract Docs | 初级 | ABI 之外的业务语义。NatSpec、README、审计报告 |
| ABI / Event | 中级 | 合约可调用能力和业务日志。能调用≠应该调用 |
| Transaction History | 中级 | 用户/合约过去行为。需保留 tx hash、block number、logs |
| Explorer Context | 初级 | 区块浏览器提供的可检查入口和证据链接 |
| Indexing Context | 中级 | 把事件整理成面向产品查询的数据。需带时间戳和同步状态 |
| Citation | 初级 | 结论引用具体链上证据。没有 citation 的解释只是观点 |

## 理想上下文包

一个好的链感知上下文应包含：

-   用户目标
    
-   当前 chain id 和网络名称
    
-   用户地址和余额
    
-   相关合约地址、ABI、文档和风险提示
    
-   最近交易和授权
    
-   索引数据更新时间
    
-   每条关键结论的 citation
    

## 关联概念

-   [Web3 工具调用](web3-tool-use) — 依赖本上下文作为输入层
    
-   [AI x Web3 School](ai-web3-school) — 来源课程
<!-- DAILY_CHECKIN_2026-05-25_END -->

# 2026-05-24
<!-- DAILY_CHECKIN_2026-05-24_START -->

# obsidian

1.  obsidian为本地md文档，方便与AI结合
    
2.  可以保存到github进行同步和管理
    
3.  可以采用karpathy模式，进行每日信息收集、AI整理、总结
    

这是目前对obsidian的应用模式

# subagent或者多agent模式

1.  multi agent模式，上下文隔离，互不干扰，可以并行执行
    
2.  hermes中有看板模式，可以控制多任务之间的依赖。
<!-- DAILY_CHECKIN_2026-05-24_END -->

# 2026-05-22
<!-- DAILY_CHECKIN_2026-05-22_START -->


今天了解到obsidian和subagent，明后天会重点学习下。
<!-- DAILY_CHECKIN_2026-05-22_END -->

# 2026-05-21
<!-- DAILY_CHECKIN_2026-05-21_START -->



# task3存在的问题

昨天没调完，存在跨域问题，今天让agent进行了修复，现在测试已经ok
<!-- DAILY_CHECKIN_2026-05-21_END -->

# 2026-05-20
<!-- DAILY_CHECKIN_2026-05-20_START -->




# Task3

针对taks3今天用hermes做了一个交互转账的demo，整体按照spec进行开发。

## 需求

1.  选择一个 Week 1 概念，例如 LLM / workflow / agent、钱包 / 签名 / 交易、Gas / 合约执行，你生成一个可交互产物：小页面、CLI、流程图、quiz、概念卡片或最小 demo，你觉着做啥好
    
2.  按照上面的workflow，你做一个用户转账的完整实现吧，先写需求和设计文档，
    

工程放到/home/ahyang/project/web3/ai-web3-school-cohort/demos/task3-transfer-token，

包括前端、后端、合约前端使用Typescript/Vite/Tailwind/Shadcn/WAGMI/VIEM

使用 Fast API作为后端，agent就用你自己吧，当然需要做成可配置的

合约写一个ERC20，使用hardhat创建工程，部署账户、网络做成可配置的

3.  需要能对接hermes agent、再把测试和部署设计加上
    
4.  不用docker，直接本地部署
    

# 开发计划

好了，接下来写开发计划

# 编码

ok，按照开发计划开始开发吧

# 提交

好的，先提交一下github

# 部署

用我的账户、rpc部署合约到sepolia
<!-- DAILY_CHECKIN_2026-05-20_END -->

# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->





之前已经在用claude code写代码，分析代码库了，

刚才在安装hermes，配置了deepseek，对接了微信，刚调通了，可惜错过了打卡时间了。

# 2026-05-19

# 任务1：

learning agent已经搭建

![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/ahyang98/images/2026-05-19-1779173933371-image.png)
<!-- DAILY_CHECKIN_2026-05-19_END -->
<!-- Content_END -->
