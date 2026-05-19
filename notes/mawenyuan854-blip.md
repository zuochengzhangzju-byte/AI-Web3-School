---
timezone: UTC+8
---

# yuannnn

**GitHub ID:** mawenyuan854-blip

**Telegram:** @Yuan_022

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->
**首先记录一下经过乱七八糟error终于成功接入tg的claude code:**

1.vscode或者cursor安装cc 感觉vscode更方便界面更清晰一些，还有node和git，最好这些东西都塞进c盘（并不知道对不对）  
[2.cc](http://2.cc) switch 配置cc 用的ds v4 pro 由于不是原生 导致用cc自带的接入tg方法大失败 发送消息后能看到tg bot在打字但是没有回复 问cc后它说它可以收到消息 也能主动给我发送（测试成功） 但是种种原因 最重要的就是接入的不是cc的ai而是ds导致的 它没法自动回复我  
3.调查后选择尝试用cc connect，交给cc自动配置 终于成功接入并对话  
4.将prompt发给tg bot后有的网站它无法读取，可能是cc的安全配置原因 请教大家后 下载官方读网站的mcp（好像依旧不太行） 用curl绕过限制终于成功抓取！

**LLM**

-   第一性原理：llm并不是百分百正确的事实，是执行工具，越是需要准确真实知识或信息的动作越需要自主校验
    
-   token：处理文本的基本单位。代码、JSON、长标识符、表格和混合语言文本经常比普通段落更吃token。
    
-   embedding：把文字/代码转成数字向量，让计算机比较「含义是否接近」。
    
    -   简单例子：
        
        -   知识库有 3 句话：A "MetaMask 是以太坊钱包" / B "比特币是加密货币" / C "今天天气很热"
            
        -   用户问 "怎么用以太坊钱包" → 系统把这句话也转成向量 → 跟 A 最接近，跟 C 最远
            
        -   RAG 系统先把 A 抓出来喂给 LLM 做参考
            
    -   关键认知：Embedding 负责匹配「意思接近」，不是判断「是否正确」。
        
    -   RAG: 用来让回答更准确 真实（当用户提出问题时，系统先从知识库里找相关材料，再让模型基于这些材料回答。）
        
        -   chunking：用合理的方法把长文本切分，可以有效节省token，方便ai检索。 方法： 比较稳的做法是按结构切：标题、API endpoint、函数说明、标准小节、FAQ 问答、审计或变更记录。每个 chunk 保留来源 URL、标题路径、更新时间和版本。
            
-   transformer:核心是：
    
    -   Attention（注意力机制） 在 Transformer 诞生之前，旧的 AI 读书就像是“狗熊掰棒子”，读到第 100 个字时，前面的第 1 个字 差不多就忘光了，或者很难把它们联系起来。而 Attention（注意力机制） 彻底改变了这一点。现在 AI 读一段话，就像人类拿了一把高光荧光笔。 当它读到“他”这个字时，它会立刻用荧光笔把前文的“张三”划上重点； 当它读到“bank”这个字时，它会同时注意到上下文里出现的“河岸”还是“贷款”，从而瞬间判断出这里的 “bank”是指地理名词还是金融机构。 这就是它能极其丝滑、毫无违和感地和你对话，并且看懂上万字复杂长文的原因。它能同时兼顾上下文里所 有的细节和它们之间的微妙关系。 但这只是联系上下文，没有真实的数据库，不能保证完全正确。
        
-   Hallucination：（想要避免的）生成的结果不真实或无法验证。或在执行时用了错误的参数，权限解释等
    
-   Multimodal：多模态，让ai可以处理多种类型的文件，这样可以读懂更多真实的工作界面。
    
-   **LLM 在 AI×Web3 全栈中的位置：理解层（Understanding Layer）**
    
    -   负责：把用户目标转成可讨论的计划，把复杂链上数据解释成人能读的语言，把文档和代码串成可执行思路
        
    -   配套需要的层：
        
        1.  数据层：RPC、索引器、预言机、向量库、项目文档
            
        2.  编排层：Prompt、Context、RAG、Agent workflow
            
        3.  执行层：工具调用、钱包、Smart Account、合约交互
            
        4.  安全层：Guard、simulation、权限策略、人工确认、日志
            
    -   **关键原则：LLM 越靠近执行层，越要把它的自然语言输出变成可验证对象。**
        

**Prompt：给模型指令让它来工作**

-   第一性原理：
    
    -   指令分层要清楚：系统规则、开发者规则、用户目标、检索内容不能混在一起。
        
    -   输出格式要机器可检验：关键结果尽量用 JSON schema、函数参数或明确字段承载。
        
    -   高风险动作不能只靠 prompt 拦截：写入数据库、发送消息、调用外部工具、执行支付或签名类动作，都必 须再经过代码层校验和 human check。
        
-   instruction: 给模型建立规则，要做什么不能做什么，输出什么。
    
    -   实用写法
        
        -   任务目标
            
        -   可用输入
            
        -   禁止行为
            
        -   输出格式和失败格式
            
-   few-shot: 当无法完全文字说清时，直接给模型一些示例进行模仿。（弊端：维护成本增高，当真实操作更新后示例可能会落后而误导模型）
    
-   structured output: 结构化输出，规定模型返回结果的结构，方便后续检查测试等
    
-   prompt injection：外界注入新的prompt引导模型做事，如泄露信息，调用危险工具等。
    
    -   应对方法：
        
        -   把外部内容标记为不可信数据
            
        -   工具调用前做参数校验
            
        -   敏感动作强制走 allowlist 和 human approval
            
        -   不把密钥、主权限和不可撤销动作交给模型
            
-   **Prompt 在 AI×Web3 全栈中的位置：接口层（Interface Layer）**
    
    -   Prompt 处在用户目标和模型行为之间——把「帮我看看这笔交易」变成模型可执行的任务：读哪些字段、怎么解释资产变化、哪些风险要标记、什么时候必须说不知道
        
    -   更稳的 6 层安全链路：
        
        1.  Prompt → 定义任务和输出格式
            
        2.  Context → 提供可信数据和来源边界
            
        3.  Model → 生成解释或候选动作
            
        4.  Code → 校验 schema 和业务规则
            
        5.  Guard / Simulation → 检查链上影响
            
        6.  Human check → 确认高风险动作
            
    -   **关键原则：Prompt 是软约束，不是安全边界。真正的边界必须由代码、权限、校验和审计来承担。**
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->

[https://www.notion.so/AI-web3-3647977eeab480d1b0e5fbf128bfa11e?source=copy\_link](https://www.notion.so/AI-web3-3647977eeab480d1b0e5fbf128bfa11e?source=copy_link)

![image.png](attachment:7fe443bc-87ea-4891-9177-67061b082049:image.png)

Web 2很多环节是基于信任进行（上图，信任bank institution不造假），web3想要解决这些：将bank institution换成block chain（支付流程）。原因：钱包：解决用户如何控制自己的资产。

![image.png](attachment:87101c2a-1de3-495a-97b7-101fbc6d3bf5:image.png)

-   钱包：解决用户如何控制自己的资产。
    

private key保密，一串随机数，和消息结合，通过算法在不泄露private key的基础上产出signature进行交易。（b站：lindell）

![image.png](attachment:10c169b1-330e-4443-a0f8-dd0cfa5cd650:image.png)

![image.png](attachment:77457cf7-2331-4fe6-a5f8-05702434de8e:image.png)

钱包分类：

![image.png](attachment:f2071935-b8b7-4f4d-9aea-a9a0534129d9:image.png)

-   交易的关键参数：
    

Gas让交易更快上链（多少钱给矿工）

nounce：保证交易顺序，确保交易不会重复提交

calldata：evm（python）的解析器，让交易多样

-   如何确定交易成功：
    

![image.png](attachment:d180c87b-7dca-4046-93bb-6784888b2d7a:image.png)

kya/kyt：合规检测是否有效

-   交易模拟：
    

签名前，不用签名模拟交易，看看此交易会对哪些相关方产生影响，减少风险。

tee 1, tee 2: 多签系统，非常安全的签名环境，保证key不泄露

![image.png](attachment:4511a729-3b8e-4110-9d5d-c70ce29fb310:image.png)

由于web3交易不可逆，因此对安全要求极高

![image.png](attachment:decc5914-6f81-413b-babf-35f1cf7c5307:image.png)

[https://updraft.cyfrin.io/career-tracks](https://updraft.cyfrin.io/career-tracks) 这里有web3各种职位的相应的学习路径和教程
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
