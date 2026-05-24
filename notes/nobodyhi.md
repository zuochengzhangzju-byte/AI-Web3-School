---
timezone: UTC+8
---

# nobodyhi

**GitHub ID:** nobodyhi

**Telegram:** 

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-24
<!-- DAILY_CHECKIN_2026-05-24_START -->
\# GLM MaaS API 入门：5分钟跑通第一个请求

GLM 系列模型（如 GLM-5.1）提供 OpenAI 兼容接口，只需换一个 `base_url` 和 `api_key`。

\---

\## 第一步：获取 API Key

首先需要一个智谱 BigModel 平台的 API Key：

1\. 访问 \[智谱AI开放平台\]([https://open.bigmodel.cn/](https://open.bigmodel.cn/)) 注册账号

2\. 登录后进入控制台，找到「API Keys」页面

3\. 点击「创建 API Key」，生成形如 `xxxxxxxx.xxxxxxxxxxxxxxxx` 的密钥

\> 💡 **安全提醒**：不要将 API Key 硬编码在代码中，建议使用环境变量。

\---

\## 第二步：环境准备

确保你的 Python 版本 ≥ 3.8，然后安装 OpenAI SDK（推荐方式）：

\`\`\`bash

pip install --upgrade openai>=1.0

\`\`\`

\---

\## 第三步：发起第一个请求

\### 方式一：使用 OpenAI SDK（推荐）

由于 GLM API 完全兼容 OpenAI 接口格式，直接用 OpenAI SDK 改一下 `base_url` 即可：

\`\`\`python

import os

from openai import OpenAI

\# 初始化客户端，指向智谱的 API 地址

client = OpenAI(

api\_key=os.environ.get("BIGMODEL\_API\_KEY"), # 替换为你的 API Key

base\_url="[https://open.bigmodel.cn/api/paas/v4/](https://open.bigmodel.cn/api/paas/v4/)"

)

\# 发起对话请求

response = [client.chat](http://client.chat).completions.create(

model="glm-5.1", # 模型名称

messages=\[

{"role": "user", "content": "用一句话解释什么是量子计算"}

\],

max\_tokens=1024,

temperature=0.7

)

\# 打印模型回复

print(response.choices\[0\].message.content)

\`\`\`

**预期输出示例**（模型实际生成内容可能略有不同）：

\`\`\`

量子计算是利用量子力学原理（如叠加和纠缠）进行信息处理的计算方式，能够在特定问题上远超经典计算机的计算能力。

\`\`\`

\### 方式二：使用 curl（无编程环境）

\`\`\`bash

curl [https://open.bigmodel.cn/api/paas/v4/chat/completions](https://open.bigmodel.cn/api/paas/v4/chat/completions) \\

\-H "Authorization: Bearer $BIGMODEL\_API\_KEY" \\

\-H "Content-Type: application/json" \\

\-d '{

"model": "glm-5.1",

"messages": \[{"role": "user", "content": "用一句话解释什么是量子计算"}\],

"max\_tokens": 1024

}'

\`\`\`

\---

\## 响应格式解析

返回的 JSON 结构与 OpenAI 完全一致：

\`\`\`json

{

"id": "chatcmpl-abc123",

"object": "chat.completion",

"created": 1744000000,

"model": "glm-5.1",

"choices": \[

{

"index": 0,

"message": {

"role": "assistant",

"content": "量子计算是利用量子力学原理..."

},

"finish\_reason": "stop"

}

\],

"usage": {

"prompt\_tokens": 18,

"completion\_tokens": 35,

"total\_tokens": 53

}

}

\`\`\`

\- `choices[0].message.content`：模型生成的回复内容

\- `usage`：本次请求消耗的 Token 数量，可用于监控配额

\---

\## 常见问题

\### Q1：API Key 格式和 OpenAI 不一样能用吗？

可以。智谱的 API Key 是 `xxx.xxx` 格式（而非 OpenAI 的 `sk-xxx`），但放在 `Authorization: Bearer` 头中完全兼容，SDK 会自动处理。

\### Q2：想看模型边想边输出怎么办？

设置 `stream=True`，可以逐字接收响应，适合需要实时展示的场景：

\`\`\`python

stream = [client.chat](http://client.chat).completions.create(

model="glm-5.1",

messages=\[{"role": "user", "content": "写一首关于夏天的短诗"}\],

stream=True

)

for chunk in stream:

if chunk.choices\[0\].delta.content:

print(chunk.choices\[0\].delta.content, end="", flush=True)

\`\`\`

\### Q3：GLM-5.1 和 GLM-4 有什么区别？

GLM-5.1 是智谱2026年4月发布的旗舰模型，在代码能力和长任务执行上显著增强，适合 Agent 场景（工具调用、多步规划等）。如果是简单对话，GLM-4 系列也完全够用。

\---

\## 总结

三步搞定：

1\. **注册** → 获取 API Key

2\. **安装** → `pip install openai`

3\. **运行** → 替换 `base_url` 和 `api_key`，其他和 OpenAI 一模一样

如果你想进一步了解流式输出、工具调用（Function Calling）等进阶用法，随时可以问我！
<!-- DAILY_CHECKIN_2026-05-24_END -->

# 2026-05-23
<!-- DAILY_CHECKIN_2026-05-23_START -->

\## Getting Started with the Claude API

\### 1. **Installation & Setup**

\`\`\`bash

pip install anthropic

\`\`\`

Set your API key:

\`\`\`python

import anthropic

import os

client = anthropic.Anthropic(

api\_key=os.environ.get("ANTHROPIC\_API\_KEY") # Or set directly

)

\`\`\`

\### 2. **Basic Message Creation**

\`\`\`python

response = client.messages.create(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

messages=\[

{"role": "user", "content": "Hello, Claude! Explain quantum computing briefly."}

\]

)

print(response.content\[0\].text)

\`\`\`

\### 3. **System Prompts**

\`\`\`python

response = client.messages.create(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

system="You are a physics professor who explains concepts with simple analogies.",

messages=\[

{"role": "user", "content": "Explain quantum computing briefly."}

\]

)

\`\`\`

\### 4. **Multi-turn Conversations**

\`\`\`python

messages = \[

{"role": "user", "content": "What's the capital of France?"},

{"role": "assistant", "content": "The capital of France is Paris."},

{"role": "user", "content": "What's its population?"}

\]

response = client.messages.create(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

messages=messages

)

\`\`\`

\### 5. **Streaming Responses**

\`\`\`python

with [client.messages.stream](http://client.messages.stream)(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

messages=\[{"role": "user", "content": "Write a short poem about AI"}\]

) as stream:

for text in stream.text\_stream:

print(text, end="", flush=True)

\`\`\`

\## Advanced Features

\### Vision Capabilities

\`\`\`python

import base64

with open("image.jpg", "rb") as img\_file:

image\_data = base64.b64encode(img\_[file.read](http://file.read)()).decode("utf-8")

response = client.messages.create(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

messages=\[{

"role": "user",

"content": \[

{

"type": "image",

"source": {

"type": "base64",

"media\_type": "image/jpeg",

"data": image\_data

}

},

{

"type": "text",

"text": "Describe this image in detail."

}

\]

}\]

)

\`\`\`

\### Tool Use (Function Calling)

\`\`\`python

tools = \[

{

"name": "get\_weather",

"description": "Get weather for a location",

"input\_schema": {

"type": "object",

"properties": {

"location": {"type": "string", "description": "City and state"},

"unit": {"type": "string", "enum": \["celsius", "fahrenheit"\]}

},

"required": \["location"\]

}

}

\]

response = client.messages.create(

model="claude-3-5-sonnet-20241022",

max\_tokens=1024,

tools=tools,

messages=\[{"role": "user", "content": "What's the weather in San Francisco?"}\]

)

\`\`\`

\## Best Practices

1\. **Error Handling**

\`\`\`python

from anthropic import APIError, RateLimitError

try:

response = client.messages.create(...)

except RateLimitError:

\# Implement exponential backoff

pass

except APIError as e:

print(f"API error: {e}")

\`\`\`

2\. **Token Management** - Monitor `response.usage.input_tokens` and `output_tokens`

3\. **Model Selection** - Choose based on needs:

\- Claude 3.5 Sonnet: Best balance of speed/capability

\- Claude 3 Opus: Most capable for complex tasks

\- Claude 3 Haiku: Fastest, most cost-effective
<!-- DAILY_CHECKIN_2026-05-23_END -->

# 2026-05-22
<!-- DAILY_CHECKIN_2026-05-22_START -->


web3
<!-- DAILY_CHECKIN_2026-05-22_END -->

# 2026-05-20
<!-- DAILY_CHECKIN_2026-05-20_START -->



## **1\. Getting Started with the OpenAI API**

Start by getting your API key from the [OpenAI Platform](https://platform.openai.com/). Add a spending limit in your account settings (e.g., $10–20) while learning to avoid unexpected costs.

python

```
import os
from openai import OpenAI

client = OpenAI(api_key=os.environ.get("OPENAI_API_KEY"))
```

✨ **Model Selection (2026)**

| Model | Best For | Approx. Input Cost |
| --- | --- | --- |
| GPT-4o | Complex reasoning, multimodal tasks, highest quality | $2.50 / 1M tokens |
| GPT-4o-mini | Most production apps – fast, cheap, capable | $0.15 / 1M tokens |
| o3 / o3-mini | Math, science, logic with deep reasoning | Premium |
| text-embedding-3-small | RAG and semantic search | $0.02 / 1M tokens |

* * *

## **💬 2. Chat Completions API & Streaming**

Chat Completions API is the core of most OpenAI apps. Messages include system, user, and assistant roles.

python

```
response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ],
    temperature=0.7,
    max_tokens=1000
)
```

For real-time UX, use **streaming**:

python

```
stream = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Tell me a story"}],
    stream=True
)
for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="")
```

* * *

## **3\. Prompt Engineering: The Six Core Principles**

Based on OpenAI's official 2026 guidelines, effective prompt engineering now emphasizes **clarity, structured instructions, and reasoning**.

| Principle | Example Application |
| --- | --- |
| Write Clear Instructions | "Summarize AI in healthcare (200 words) with 3 cases." vs. vague "Talk about AI." |
| Provide Reference Text | Inject external context (RAG) to reduce hallucinations and ground responses in facts. |
| Split Complex Tasks | Break into intent classification → summarization → analysis → conclusion pipeline. |
| Give the Model Time to Think | Use Chain-of-Thought: "Let's think step by step" → dramatically improves logic and math. |
| Leverage External Tools | Offload precise calculations to code execution; use function calling for real-time data. |
| Iterative Development | A/B test different phrasing; analyze failures and iterate systematically. |

💡 **Key Insight for 2026**: Shorter, results-oriented prompts are often more effective than lengthy, over‑specified ones—a shift noted in OpenAI's latest guidance.

* * *

## **4\. Function Calling (Tool Use)**

Function calling is the primary way to connect AI models to external APIs and actions. The model returns a structured JSON tool call rather than raw text, which you then execute.

### **Define a function schema (JSON)**

python

```
tools = [{
    "type": "function",
    "function": {
        "name": "get_weather",
        "description": "Get current temperature for a location",
        "parameters": {
            "type": "object",
            "properties": {
                "location": {"type": "string", "description": "City and state, e.g., San Francisco, CA"},
                "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]}
            },
            "required": ["location"]
        }
    }
}]
```

### **Let the model choose a tool**

python

```
response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": "What's the weather in Tokyo?"}],
    tools=tools,
    tool_choice="auto"          # model decides when to call
)
```

### **Handle the tool call**

python

```
tool_call = response.choices[0].message.tool_calls[0]
arguments = json.loads(tool_call.function.arguments)
# Execute actual weather API call, then return result to model
```

For **multi‑step workflows**, you can chain multiple function calls—the model sees previous outputs before deciding the next action, enabling powerful agents that search, fetch, then process.

* * *

## **5\. Embeddings & RAG (Retrieval-Augmented Generation)**

Embeddings convert text into dense **vectors** (e.g., 1,536 floats for `text-embedding-3-small`) that capture semantic meaning.

python

```
response = client.embeddings.create(
    model="text-embedding-3-small",
    input="Your text here"
)
vector = response.data[0].embedding
```
<!-- DAILY_CHECKIN_2026-05-20_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->




While LLMs are an impressive achievement, their output is only statistically plausible and not the result of a reasoning process.  
  
**Understanding NLP and LLMs**

While this course was originally focused on NLP (Natural Language Processing), it has evolved to emphasize Large Language Models (LLMs), which represent the latest advancement in the field.

**What’s the difference?**

-   **NLP (Natural Language Processing)** is the broader field focused on enabling computers to understand, interpret, and generate human language. NLP encompasses many techniques and tasks such as sentiment analysis, named entity recognition, and machine translation.
    
-   **LLMs (Large Language Models)** are a powerful subset of NLP models characterized by their massive size, extensive training data, and ability to perform a wide range of language tasks with minimal task-specific training. Models like the Llama, GPT, and Claude series are examples of LLMs that have revolutionized what’s possible in NLP.
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
