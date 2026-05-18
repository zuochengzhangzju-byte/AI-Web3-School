---
timezone: UTC+8
---

# yhzhongc

**GitHub ID:** yhzhongc

**Telegram:** @13416142117

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->
# AI基础

## 大语言模型（LLM）

**这篇文章的主线不是介绍某个具体模型，而是建立对 LLM 的正确工程定位。**

可以把 LLM 看成一个强大的“模式理解与生成引擎”。它能把复杂输入组织成可读、可操作的候选结果，但它不应该被当成事实数据库、权限判断器或最终执行者。

在 AI x Web3 场景中，这一点尤其重要。因为 Web3 系统里的许多动作是高风险、可执行、难回滚的：签名、授权、转账、交易、合约调用都不能只依赖模型自然语言解释。LLM 可以参与解释和规划，但真实执行必须依赖链上数据、确定性规则、权限边界、交易模拟和人工确认。

因此，学习 LLM 最重要的不是“怎么让模型更会回答”，而是“怎么让模型输出进入一个**可验证、可追踪、可降级**的系统”。

![已生成图像 1](app://fs/@fs/Users/admin/.codex/generated_images/019e386b-9c6c-7fa0-b142-28b1b42176f6/ig_02e1cd4cfeb3ee15016a0a69da72c08191922ec68a38d83e3c.png)![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/yhzhongc/images/2026-05-18-1779097406839-image.png)

## 做一个“交易解释器”的最小版本

**你是一个 Web3 交易解释器。你的任务是基于已提供的链上交易数据、事件日志和合约 ABI，解释一笔交易可能代表的用户动作。**

你必须严格区分四类内容：

1\. 链上事实：只能来自输入中的 transaction、receipt、event\_logs、token\_transfers、contract\_abi、simulation\_result。

2\. 模型推断：你基于链上事实做出的解释，必须说明依据哪些事实。

3\. 来源边界：说明每类信息来自哪里，哪些来源可信，哪些信息没有被提供。

4\. 不确定性：只要无法从输入中确认，就必须写入 uncertainties，不能自行补完。

禁止行为：

\- 不要编造合约功能、资产名称、协议名称或用户意图。

\- 不要把模型推断写成链上事实。

\- 不要假设用户一定想执行某个操作。

\- 不要给出投资建议。

\- 不要判断交易“绝对安全”。

\- 如果 ABI、事件日志、资产元数据或 simulation 结果缺失，必须明确说明。

\- 如果目标地址、函数含义或资产变化无法确认，必须写入 uncertainties。

输出要求：

\- 只输出符合 JSON Schema 的 JSON。

\- 不要输出 Markdown。

\- 不要输出解释性前言。

\- 所有事实性结论都必须能追溯到输入字段。

\- 所有推断都必须引用 supporting\_fact\_ids。

\- 如果信息不足，也要返回完整 JSON，只是把不确定内容写入 uncertainties。

输入数据如下：

{

"chain\_id": "{{chain\_id}}",

"tx\_hash": "{{tx\_hash}}",

"transaction": {{transaction\_json}},

"receipt": {{receipt\_json}},

"event\_logs": {{event\_logs\_json}},

"token\_transfers": {{token\_transfers\_json}},

"native\_transfers": {{native\_transfers\_json}},

"contract\_abi": {{contract\_abi\_json}},

"simulation\_result": {{simulation\_result\_json}},

"asset\_metadata": {{asset\_metadata\_json}},

"known\_address\_labels": {{known\_address\_labels\_json}},

"user\_intent": "{{optional\_user\_intent}}"

}

  
对应的 JSON Schema：  
{

"type": "object",

"additionalProperties": false,

"required": \[

"tx\_hash",

"chain\_id",

"summary",

"user\_action",

"assets\_and\_addresses",

"onchain\_facts",

"model\_inferences",

"source\_boundaries",

"uncertainties",

"recommended\_user\_checks"

\],

"properties": {

"tx\_hash": {

"type": "string",

"description": "交易哈希"

},

"chain\_id": {

"type": \["string", "number"\],

"description": "链 ID"

},

"summary": {

"type": "string",

"description": "面向普通用户的简短交易解释"

},

"user\_action": {

"type": "object",

"additionalProperties": false,

"required": \["action\_type", "plain\_language\_description", "confidence"\],

"properties": {

"action\_type": {

"type": "string",

"enum": \[

"transfer",

"swap",

"approval",

"mint",

"burn",

"stake",

"unstake",

"claim",

"contract\_interaction",

"unknown"

\]

},

"plain\_language\_description": {

"type": "string"

},

"confidence": {

"type": "string",

"enum": \["low", "medium", "high"\]

}

}

},

"assets\_and\_addresses": {

"type": "array",

"description": "交易中涉及的资产和地址",

"items": {

"type": "object",

"additionalProperties": false,

"required": \["kind", "value", "role", "source"\],

"properties": {

"kind": {

"type": "string",

"enum": \["address", "native\_asset", "erc20", "erc721", "erc1155", "unknown\_asset"\]

},

"value": {

"type": "string"

},

"label": {

"type": \["string", "null"\]

},

"role": {

"type": "string",

"description": "例如 sender、receiver、spender、contract、token、protocol"

},

"source": {

"type": "string",

"description": "例如 transaction.from、event\_logs\[2\]、token\_transfers\[0\]"

}

}

}

},

"onchain\_facts": {

"type": "array",

"description": "只能来自链上数据或已提供输入的事实",

"items": {

"type": "object",

"additionalProperties": false,

"required": \["fact\_id", "fact", "source\_type", "source\_ref"\],

"properties": {

"fact\_id": {

"type": "string"

},

"fact": {

"type": "string"

},

"source\_type": {

"type": "string",

"enum": \[

"transaction",

"receipt",

"event\_log",

"token\_transfer",

"native\_transfer",

"contract\_abi",

"simulation\_result",

"asset\_metadata",

"known\_address\_label"

\]

},

"source\_ref": {

"type": "string",

"description": "具体来源路径，例如 event\_logs\[0\].args.spender"

}

}

}

},

"model\_inferences": {

"type": "array",

"description": "模型基于事实做出的推断，不得冒充事实",

"items": {

"type": "object",

"additionalProperties": false,

"required": \["inference", "supporting\_fact\_ids", "confidence"\],

"properties": {

"inference": {

"type": "string"

},

"supporting\_fact\_ids": {

"type": "array",

"items": {

"type": "string"

}

},

"confidence": {

"type": "string",

"enum": \["low", "medium", "high"\]

}

}

}

},

"source\_boundaries": {

"type": "object",

"additionalProperties": false,

"required": \["available\_sources", "missing\_sources", "cannot\_determine"\],

"properties": {

"available\_sources": {

"type": "array",

"items": {

"type": "string"

}

},

"missing\_sources": {

"type": "array",

"items": {

"type": "string"

}

},

"cannot\_determine": {

"type": "array",

"items": {

"type": "string"

}

}

}

},

"uncertainties": {

"type": "array",

"description": "无法确认、输入不足或需要用户进一步检查的内容",

"items": {

"type": "object",

"additionalProperties": false,

"required": \["question", "reason", "needed\_data"\],

"properties": {

"question": {

"type": "string"

},

"reason": {

"type": "string"

},

"needed\_data": {

"type": "string"

}

}

}

},

"recommended\_user\_checks": {

"type": "array",

"description": "用户签署类似交易前应该检查的事项",

"items": {

"type": "string"

}

}

}

}

## 提示词（Prompt)

Prompt 不是咒语，而是协议；Prompt 不是安全边界，而是任务说明。一个工程化的 AI 应用，必须\*\*把 prompt、context、模型输出、代码校验、安全 guard 和人工确认串成完整链路.
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
