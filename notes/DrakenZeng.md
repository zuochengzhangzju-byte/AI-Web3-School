---
timezone: UTC+8
---

# Draken

**GitHub ID:** DrakenZeng

**Telegram:** @draken_zeng

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->
# 一、核心思想与基础概念

### 1.1 基本哲学

-   **万物皆函数 (Everything is a Function)**：一切智能过程都可以用数学函数表示
    
-   **符号主义 (Symbolism)**：试图用精确的符号逻辑解释智能（遇到瓶颈）
    
-   **连接主义 (Connectionism)**：通过大量简单单元的连接来模拟智能
    

### 1.2 模型基础

-   **模型 (Model)**：表示复杂函数的数学结构
    
-   **权重 (Weight)**：模型中的可调整参数
    
-   **大模型 (Large Model)**：参数量特别巨大的模型
    
-   **大语言模型 (LLM, Large Language Model)**：专门处理自然语言的大模型
    

# 二、基本概念

### 1\. Token

-   LLM 处理的最小单位,既不是字符也不是单词,是介于两者之间的"子词片段"(subword)。每个 token 在模型内部就是一个**整数 ID**。
    
-   **为什么不用字符或单词:**
    
    -   **按单词切**:词表会爆炸(英文几十万),且没法处理拼写错误 / 新词 / 中日韩这种没空格的语言
        
    -   **按字符切**:序列太长(1 万字文档 = 1 万 token),O(n²) attention 直接爆
        
    -   **subword 是折中**:常见词整词作一个 token(`the` / `tion`),低频词被拆碎(`unbelievable` → `un` + `believe` + `able`)
        

\*\*总结：\*\*Token 是信息论意义上的"最优压缩单位" —— 在固定词表预算(~10万)下,让训练语料的平均每 token 信息密度最大化。BPE算法本质就是贪心地"合并最高频 pair",直到词表填满。

### 2\. Embedding

-   把离散对象(token / 句子 / 图片 / 用户)映射到一个**固定维度的浮点向量**(典型 768 / 1024 / 1536 / 3072 维),让"语义相似"变成"向量距离近"。
    

例如：Token 是整数(5050、6231)。整数之间没有"相似度"概念:5050 和 5051不比 5050 和 99999 更相关。Embedding 给每个 token ID 分配一个向量，让语义相似的 token -> 向量距离近。

-   向量空间满足三件事,而这三件事是 LLM 能力的基础:
    
    -   可微(可以梯度下降训练) —— 离散整数不可微,向量可以
        
    -   可度量(cosine / 欧氏距离 = 语义相似度) ——"猫"和"狗"距离近,"猫"和"汽车"距离远
        
    -   可代数运算(著名的 king - man + woman ≈ queen) —— 语义关系变成几何方向
        

\*\*总结：\*\*Embedding 不是"设计"出来的,是"任务逼迫"出来的副产品。任何能让模型在大规模任务上做对预测的几何结构,就是好的 embedding。

### 3\. Transformer

-   2017 年 Google “Attention is All You Need” 提出的**纯 attention + 前馈层堆叠**的神经网络架构。所有现代 LLM(GPT / Claude / Llama / Qwen / Gemini)都是 Transformer 的变种。
    

Transformer = Attention + MLP + Residual + LayerNorm

| 组件 | 解决的根本问题 |

| Attention | “token 之间如何交换信息” —— 横向 mixing |

| MLP(前馈层) | “单个 token 内部如何加工信息” —— 纵向 transform。Attention 只能做"加权混合"线性操作,需要 MLP 提供非线性表达力 |

| Residual(x + sublayer(x)) | "深层网络如何保证梯度能传回去" —— 没有 residual ,堆 100 层直接训不动 |

| LayerNorm | "数值如何保持稳定" —— 防止激活值在深层网络里爆炸/消失 |
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
