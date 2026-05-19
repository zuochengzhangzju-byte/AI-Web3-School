---
timezone: UTC+0
---

# DaisyDai

**GitHub ID:** Daishunying

**Telegram:** 

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->
# Hermes、Chatbot 与 OpenClaw 的区别与工作流程

# 一、整体关系图

核心理解：

-   Chatbot 是交互入口。
    
-   Hermes 是负责推理和决策的大脑。
    
-   OpenClaw 是负责执行动作的 Agent Runtime。
    
-   真正完整的 AI Agent 系统通常是三者协作。
    

* * *

# 二、Chatbot 是什么

## 1\. Chatbot 的定义

Chatbot 本质上是：

“人与 AI 对话的界面。”

它通常包含：

-   聊天窗口
    
-   用户输入
    
-   AI 输出
    
-   对话历史
    
-   简单上下文管理
    

常见例子：

-   ChatGPT
    
-   Claude
    
-   Gemini
    
-   Character AI
    
-   Discord Bot
    
-   Telegram Bot
    

Chatbot 的核心目标是：

“自然语言交互。”

它不一定真正执行复杂任务。

很多 chatbot 的能力停留在：

-   问答
    
-   文本生成
    
-   简单建议
    
-   内容总结
    
-   翻译
    
-   基础代码生成
    

因此：

Chatbot 更像：

```text
Human ↔ Conversation Interface ↔ LLM
```

而不是完整 autonomous system。

* * *

## 2\. Chatbot 的工作流程

```text
用户输入
   ↓
聊天界面
   ↓
LLM 推理
   ↓
生成回答
   ↓
返回用户
```

这是最基础的 AI workflow。

如果进一步增强：

```text
User
 ↓
Chatbot UI
 ↓
LLM
 ↓
Search/API/Memory
 ↓
Response
```

这时已经开始接近 Agent。

* * *

## 3\. Chatbot 的优点

### 使用门槛低

用户直接对话即可。

### 非常适合：

-   学习
    
-   brainstorming
    
-   文本创作
    
-   coding assistant
    
-   quick research
    

### 适合快速验证 idea

很多 AI 产品第一版其实都是 chatbot。

* * *

## 4\. Chatbot 的局限

### 没有长期记忆

大多数 chatbot：

-   session limited
    
-   context 会丢失
    
-   无法长期跟踪任务
    

### 不会主动执行

它通常只会：

“回答。”

不会：

-   自动操作电脑
    
-   自动完成工作流
    
-   长期自主运行
    

### 缺少 orchestration

很多 chatbot 无法：

-   multi-step planning
    
-   autonomous workflow
    
-   complex tool execution
    

* * *

# 三、Hermes 是什么

## 1\. Hermes 的定义

Hermes 通常指 Nous Research 的 Hermes 系列模型。

它属于：

-   Instruction-tuned LLM
    
-   Agent-oriented LLM
    
-   Reasoning model
    

Hermes 不是单纯聊天模型。

它更强调：

-   tool use
    
-   structured output
    
-   reasoning
    
-   workflow coordination
    
-   autonomous behavior
    

因此很多 Agent 系统喜欢使用 Hermes。

* * *

## 2\. Hermes 的核心定位

Hermes 更像：

```text
AI Brain / AI Planner
```

它负责：

-   理解任务
    
-   推理
    
-   拆解步骤
    
-   调用工具
    
-   管理 workflow
    
-   生成 structured output
    

* * *

## 3\. Hermes 的工作流程

```text
User Task
    ↓
Hermes
    ↓
Reasoning / Planning
    ↓
Tool Calling
(Search/API/Files)
    ↓
Memory / Context
    ↓
Structured Output
```

如果再进一步：

```text
User
 ↓
Hermes Agent
 ↓
Task Planning
 ↓
Codex / APIs / Search
 ↓
Result Evaluation
 ↓
Final Output
```

这已经是 Agent workflow。

* * *

## 4\. Hermes 的优势

### 更适合 Agent 系统

Hermes 非常强调：

-   tool calling
    
-   multi-step reasoning
    
-   workflow chaining
    

### 适合长期学习系统

例如：

-   AI tutor
    
-   research agent
    
-   coding workflow
    
-   career optimization system
    

### 本地部署友好

Hermes 可以：

-   Ollama 本地运行
    
-   GPU 私有部署
    
-   接 LangGraph
    
-   接 AutoGen
    

这对 AI engineer 很重要。

* * *

## 5\. Hermes 的局限

### GUI 能力弱

Hermes 本身不会操作电脑。

它只是：

“决定做什么。”

### 工程稳定性不一定强于 Claude

在复杂 coding 上：

Claude Code / GPT-5 Codex 往往更稳定。

### 需要 workflow 框架配合

Hermes 通常需要：

-   LangGraph
    
-   OpenClaw
    
-   MCP
    
-   Tool layer
    

才能真正 autonomous。

* * *

# 四、OpenClaw 是什么

## 1\. OpenClaw 的定义

OpenClaw 更接近：

-   Computer Use Agent
    
-   Browser Agent
    
-   Agent Runtime
    
-   Autonomous Execution Framework
    

它的核心目标是：

“让 AI 真正操作电脑。”

例如：

-   打开网页
    
-   点击按钮
    
-   填表
    
-   下载文件
    
-   使用 terminal
    
-   操作软件
    

* * *

## 2\. OpenClaw 的核心定位

OpenClaw 更像：

```text
AI Body / Execution Layer
```

如果 Hermes 是“大脑”，

那么 OpenClaw 是：

-   手
    
-   眼睛
    
-   鼠标
    
-   键盘
    

它负责把 reasoning 转化为真实操作。

* * *

## 3\. OpenClaw 的工作流程

```text
User Goal
    ↓
LLM Reasoning
(Hermes/GPT)
    ↓
OpenClaw
    ↓
Screen Observation
    ↓
Action Decision
    ↓
Mouse/Keyboard Action
    ↓
Feedback Loop
    ↓
Next Action
```

这是典型 computer-use workflow。

* * *

## 4\. OpenClaw 的能力

### Browser Automation

例如：

-   自动申请工作
    
-   自动搜索信息
    
-   自动填写表单
    

### GUI Interaction

例如：

-   点击
    
-   输入
    
-   拖拽
    
-   切换窗口
    

### Tool Orchestration

它通常还能结合：

-   terminal
    
-   docker
    
-   APIs
    
-   OCR
    
-   vision model
    

* * *

## 5\. OpenClaw 的局限

### 本身不是“大脑”

OpenClaw 通常需要：

-   Hermes
    
-   GPT
    
-   Claude
    

作为 reasoning model。

### GUI automation 不稳定

网页变化可能导致：

-   点击失败
    
-   selector 错误
    
-   context confusion
    

### 成本较高

因为：

-   vision
    
-   screenshots
    
-   action loops
    

会消耗大量 token。

* * *

# 五、三者关系总结

## Chatbot vs Hermes vs OpenClaw

| 维度 | Chatbot | Hermes | OpenClaw |
| --- | --- | --- | --- |
| 本质 | 对话界面 | LLM/Reasoning | Agent Runtime |
| 主要作用 | 聊天交互 | 推理规划 | 执行操作 |
| 是否能长期规划 | 弱 | 强 | 中 |
| 是否会操作电脑 | 不会 | 不会 | 会 |
| 是否适合 Agent | 中 | 强 | 强 |
| 是否能独立使用 | 可以 | 可以 | 通常不行 |
| 是否支持 tool calling | 部分 | 强 | 强 |
| 核心定位 | Interface | Brain | Body |

* * *

# 六、典型真实工作流

## 场景：AI Career Optimization System

### 第一阶段：用户输入

```text
我想成为英国 AI systems engineer
```

* * *

### 第二阶段：Chatbot 接收输入

聊天界面负责：

-   用户交互
    
-   展示结果
    
-   管理 session
    

* * *

### 第三阶段：Hermes 推理

Hermes：

-   分析用户背景
    
-   搜索市场信息
    
-   识别技能缺口
    
-   制定 roadmap
    
-   输出计划
    

* * *

### 第四阶段：OpenClaw 执行

OpenClaw：

-   搜 LinkedIn
    
-   打开 GitHub
    
-   自动投递
    
-   自动整理岗位
    
-   自动填写申请
    

* * *

### 最终结构

```text
User
 ↓
Chatbot
 ↓
Hermes
 ↓
OpenClaw
 ↓
Real World Execution
```

这就是现代 AI Agent 系统。
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->

# AI × Web3 课程笔记（2023 年后发展与融合方向）

* * *

# 第一部分：AI 在 2023 年后的技术发展

* * *

# Chapter 1 — 生成式 AI（Generative AI）时代的开启

## 1.1 什么是生成式 AI

在 2023 年之前，大多数 AI 系统本质上是：

```text
输入数据 → 输出预测结果
```

例如：

-   图片分类
    
-   推荐系统
    
-   搜索排序
    
-   垃圾邮件检测
    
-   风控评分
    

它们通常只能完成“单一任务”。

而 2023 年后，AI 开始进入：

# Generative AI（生成式 AI）时代

其核心变化是：

# AI 不只是“判断”

而是开始“创造”。

例如：

-   写文章
    
-   写代码
    
-   生成图片
    
-   生成视频
    
-   生成语音
    
-   自动总结
    
-   自动推理
    

其中最重要的代表是：

-   OpenAI 的 GPT-4
    
-   Anthropic 的 Claude
    
-   Google 的 Gemini
    
-   Meta 的 Llama
    
-   DeepSeek 的 DeepSeek-R1
    

这些模型统称为：

# LLM（Large Language Model，大语言模型）

* * *

## 1.2 大语言模型（LLM）的核心原理

LLM 的本质可以理解为：

# “预测下一个 token 的概率机器”

例如：

输入：

```text
I love drinking
```

模型会预测：

```text
tea
coffee
water
```

哪个词概率最高。

虽然原理听起来简单，但由于：

-   参数规模巨大
    
-   训练数据极多
    
-   Transformer 架构强大
    

模型开始出现：

-   推理能力
    
-   语言理解能力
    
-   代码能力
    
-   长文本能力
    

* * *

## 1.3 Transformer 架构的重要性

现代 LLM 基本都基于：

# Transformer Architecture

由 Google Brain 在论文：

# “Attention Is All You Need”

中提出。

Transformer 最核心的机制：

# Attention（注意力机制）

其核心思想：

```text
模型会动态关注最重要的信息
```

例如：

句子：

```text
The animal didn't cross the street because it was tired.
```

模型会理解：

```text
it = animal
```

而不是 street。

这让 AI 第一次真正具备：

# 上下文理解能力

* * *

# Chapter 2 — 多模态 AI（Multimodal AI）

* * *

## 2.1 AI 为什么需要多模态

人类不是只通过文字理解世界。

而是通过：

-   视觉
    
-   听觉
    
-   语言
    
-   动作
    

共同感知世界。

因此：

# 下一代 AI 必须具备多模态能力

即：

# 一个模型同时处理：

-   文本
    
-   图片
    
-   音频
    
-   视频
    
-   代码
    
-   屏幕
    

* * *

## 2.2 GPT-4o 与实时 AI

2024 年后，多模态 AI 开始爆发。

代表包括：

-   GPT-4o
    
-   Gemini
    
-   Claude Vision
    

它们开始支持：

-   图片理解
    
-   OCR
    
-   视频分析
    
-   语音实时对话
    
-   屏幕识别
    

例如：

用户上传一张图：

AI 可以：

-   识别内容
    
-   分析逻辑
    
-   解数学题
    
-   阅读图表
    
-   理解 UI
    

这意味着：

# AI 开始获得“视觉能力”

* * *

## 2.3 多模态的重要意义

多模态意味着：

AI 开始从：

```text
语言系统
```

变成：

```text
数字世界感知系统
```

这会直接推动：

-   AI 助手
    
-   自动驾驶
    
-   AI 机器人
    
-   AI 操作电脑
    
-   AI 自动办公
    

的发展。

* * *

# Chapter 3 — Agentic AI（智能体 AI）

* * *

## 3.1 什么是 AI Agent

很多人认为：

Agent = 更复杂的 Prompt。

实际上并不是。

真正的 Agent 包括：

| 能力 | 含义 |
| --- | --- |
| Memory | 长期记忆 |
| Planning | 任务规划 |
| Tool Use | 工具调用 |
| Reflection | 自我反思 |
| Multi-step Reasoning | 多步推理 |
| Environment Interaction | 与环境交互 |

因此：

# Agent 本质上是“可行动的 AI”

* * *

# Chapter 4 — 推理模型（Reasoning Models）

* * *

## 4.1 从“语言生成”到“逻辑推理”

早期模型主要擅长：

-   模仿语言
    
-   生成文本
    

但：

不擅长复杂逻辑。

因此：

2024 年后 AI 开始强调：

# Reasoning（推理能力）

* * *

## 4.2 Chain-of-Thought（思维链）

推理模型的重要机制：

# Chain-of-Thought

即：

AI 不直接输出答案。

而是：

```text
问题
→ 分析
→ 分步骤推理
→ 验证
→ 输出
```

例如数学问题：

x^2-5x+6=0

模型会先：

1.  因式分解
    
2.  求根
    
3.  验证结果
    

而不是直接猜答案。

* * *

## 4.3 推理模型的重要意义

Reasoning Model 的意义在于：

# AI 开始接近“决策系统”

而不是：

# 单纯聊天机器人

这会推动：

-   自动研究
    
-   自动交易
    
-   自动分析
    
-   自动编程
    
-   自动科学研究
    

的发展。

* * *

# AI × Web3 的融合方向

* * *

# Chapter 5 — AI × Web3 的核心逻辑

* * *

## 5.1 两者为什么会融合

AI 最大的问题：

| AI 的问题 | Web3 的能力 |
| --- | --- |
| 黑箱 | 可验证 |
| 数据归属不清 | Ownership |
| 中心化 | 去中心化 |
| Agent 缺乏经济系统 | Token Economy |

因此：

# AI 提供智能

# Web3 提供信任

* * *

# Chapter 6 — AI Agent × Crypto Wallet

* * *

## 6.1 AI Wallet 的概念

未来钱包可能不只是：

# 存储资产

而会变成：

# Autonomous Economic Agent

即：

AI 自动：

-   管理资产
    
-   执行交易
    
-   分析风险
    
-   支付费用
    

* * *

## 8.2 Agent Economy

未来可能出现：

```text
AI 自己赚钱
AI 自己消费
AI 自己协作
```

例如：

-   AI 接任务
    
-   AI 写代码
    
-   AI 获得 Token
    
-   AI 支付 GPU 成本
    

这就是：

# Autonomous Economy（自主经济）

* * *

# Chapter 7 — AI × Web3 Security

* * *

## 7.1 为什么 AI 非常适合 Web3 安全

区块链数据：

-   开放
    
-   可追踪
    
-   结构化
    

非常适合 AI：

-   图分析
    
-   异常检测
    
-   行为识别
    

* * *

## 7.2 未来的重要方向

包括：

-   Smart Contract Audit
    
-   Fraud Detection
    
-   Wallet Risk Scoring
    
-   Scam Detection
    
-   On-chain Monitoring
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
