---
timezone: UTC+8
---

# Justin Li

**GitHub ID:** may-tonk

**Telegram:** @maytonk

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-24
<!-- DAILY_CHECKIN_2026-05-24_START -->
本文用于总结近期围绕 ChainMind 项目学到的核心内容，包括项目定位、量化属性、相似 GitHub 项目对比、当前工程状态、已形成的判断框架，以及后续最值得继续推进的方向。

## **1\. 我们对 ChainMind 的重新定位**

ChainMind 不应该被定义为普通行情看板，也不应该被包装成 AI 自动交易机器人。

更准确的定位是：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`面向 BNB / EVM meme token 的链上行为风险过滤与可解释投研系统。`

它的核心目标不是预测某个 token 一定会涨，而是回答：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`这个链上机会是否真实？ 风险来自哪里？ 早期资金是否已经撤退？ 买盘是否真实扩散？ 多个钱包买入是真共识还是假共识？ 聪明钱信号是否可复制？ 是否值得进入人工研究列表？`

因此，ChainMind 第一阶段的正确方向是：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`先过滤坏机会 再识别可观察机会 最后由 AI 解释为什么`

## **2\. ChainMind 是否算量化**

ChainMind 算量化，但不是传统意义上的自动交易量化。

它更接近：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`链上行为因子研究型量化 风险过滤型量化 半自动投研量化系统 事件驱动型链上分析系统`

它不属于：

-   高频交易量化。
    
-   做市或套利机器人。
    
-   单纯 K 线技术指标策略。
    
-   自动下单系统。
    
-   黑箱式机器学习涨跌预测模型。
    

ChainMind 的量化特征主要来自三类因子：

### **2.1 Token Risk 因子**

用于判断 token 是否存在明显风险。

典型指标包括：

-   流动性是否过低。
    
-   5m / 15m net\_buy\_usd 是否转负。
    
-   trades / unique\_traders 是否异常。
    
-   前 20 / 50 早期买家清仓比例。
    
-   holder 集中度。
    
-   同 funder 早期买家数量。
    
-   新钱包比例。
    
-   合约权限和 LP 风险。
    

### **2.2 Wallet Alpha 因子**

用于判断某个钱包是否真的有稳定 alpha。

典型指标包括：

-   历史胜率。
    
-   realized PnL。
    
-   median return。
    
-   最大回撤。
    
-   rug exposure。
    
-   最近 7D / 30D / 90D 表现。
    
-   买入后 15m / 1h / 6h 表现。
    

### **2.3 Copyability 因子**

用于判断普通用户是否还能复制这个钱包信号。

典型指标包括：

-   是否同区块买入。
    
-   是否开池几秒内买入。
    
-   是否依赖机器人速度或极高 gas。
    
-   买入时流动性是否过低。
    
-   买入后 5-15 分钟是否仍有成交量。
    
-   买入后是否仍有净买入和观察窗口。
    

核心认知是：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`高胜率钱包 ≠ 可复制钱包 聪明钱买入 ≠ 普通用户能跟`

## **3\. 与 GitHub 相似项目的对比**

我们查看了 GitHub 上几类相似项目后发现，ChainMind 不是和某一个项目完全重合，而是处在多个方向的交叉点上。

## **3.1 传统 crypto 量化交易框架**

代表项目：

-   Freqtrade: [https://github.com/freqtrade/freqtrade](https://github.com/freqtrade/freqtrade)
    
-   Hummingbot: [https://github.com/hummingbot/hummingbot](https://github.com/hummingbot/hummingbot)
    
-   Jesse: [https://github.com/jesse-ai/jesse](https://github.com/jesse-ai/jesse)
    

这些项目重点在：

-   策略回测。
    
-   参数优化。
    
-   交易所连接。
    
-   订单管理。
    
-   自动交易执行。
    
-   实盘风控。
    

ChainMind 与它们的区别：

| 对比维度 | 传统交易框架 | ChainMind |
| --- | --- | --- |
| 核心目标 | 自动交易与策略执行 | 风险过滤与投研解释 |
| 数据基础 | K 线、订单簿、交易所成交 | 链上交易、钱包、资金来源 |
| 输出结果 | 买卖信号或订单 | 风险等级、观察理由、研究报告 |
| 是否下单 | 通常会 | 第一阶段不做 |
| 适合场景 | 已知交易对策略 | 新 meme token 早期筛选 |

学习结论：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind 不应该去卷成熟 trading bot， 而应该强调链上行为风控和可解释研究。`

## **3.2 Rug / Honeypot / Token 安全检测工具**

代表项目：

-   RugWatch: [https://github.com/machenxi/rugpull-scam-token-detection](https://github.com/machenxi/rugpull-scam-token-detection)
    
-   bsc-honeypot-detector: [https://github.com/mraicodedev/bsc-honeypot-detector](https://github.com/mraicodedev/bsc-honeypot-detector)
    
-   DumpDetective: [https://github.com/JN-Bot666/dump-detective](https://github.com/JN-Bot666/dump-detective)
    

这些项目重点在：

-   合约是否高危。
    
-   是否 honeypot。
    
-   是否能正常卖出。
    
-   LP 是否有风险。
    
-   owner / mint / blacklist / tax 权限。
    
-   项目方或创建者钱包是否异常。
    

ChainMind 与它们的区别：

| 对比维度 | Token 安全工具 | ChainMind |
| --- | --- | --- |
| 核心关注 | 合约和池子是否危险 | 资金行为是否真实、独立、可复制 |
| 判断对象 | token 合约 / LP / 权限 | token + 早期买家 + 钱包集群 |
| 优势 | 快速安全红旗 | 解释风险来源和观察条件 |
| 可借鉴点 | honeypot、LP、权限、税率检查 | 纳入 Risk Score 基础层 |

学习结论：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind 不必重复造 Token Sniffer。 更好的做法是把 GoPlus / honeypot / LP 检查作为基础安全层， 然后继续做早期资金行为分析。`

## **3.3 Smart Money / Wallet Tracker / Copy Trader 项目**

代表项目：

-   whale-wallet-mirror-copy-trader: [https://github.com/Rezzecup/whale-wallet-mirror-copy-trader](https://github.com/Rezzecup/whale-wallet-mirror-copy-trader)
    
-   DeepLens: [https://github.com/alanisme/deeplens](https://github.com/alanisme/deeplens)
    

这类项目重点在：

-   监听重点钱包。
    
-   追踪 whale / smart money。
    
-   提醒钱包买入或卖出。
    
-   有些项目会直接做 mirror trading。
    

ChainMind 与它们的区别：

| 对比维度 | Wallet Tracker | ChainMind |
| --- | --- | --- |
| 常见逻辑 | 某钱包买了就提醒或复制 | 先判断这个信号是否可信、独立、可复制 |
| 主要风险 | 盲目追高或跟机器人 | 通过 Copyability 降噪 |
| 输出结果 | 钱包动作通知 | 钱包质量、同实体风险、可复制性 |
| 差异化 | 速度和钱包列表 | 判断质量和复盘闭环 |

学习结论：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind 的差异化不是“更快提醒聪明钱”， 而是判断聪明钱信号是否真的值得普通用户观察。`

## **3.4 链上数据基础设施项目**

代表项目：

-   Ethereum ETL: [https://github.com/blockchain-etl/ethereum-etl](https://github.com/blockchain-etl/ethereum-etl)
    
-   BlockSci: [https://github.com/citp/BlockSci](https://github.com/citp/BlockSci)
    
-   Dune SQL 查询仓库: [https://github.com/bitman09/Dune-Analytics](https://github.com/bitman09/Dune-Analytics)
    

这些项目更像基础设施，重点在：

-   链上数据抽取。
    
-   数据清洗。
    
-   查询模板。
    
-   地址和交易分析。
    
-   研究型数据处理。
    

ChainMind 与它们的关系：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`Dune / ETL / RPC / API 是数据基础设施。 ChainMind 是基于这些数据的 meme token 风险研究应用。`

学习结论：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind 应该复用这些数据能力， 但产品价值要体现在评分、解释、分级和复盘上。`

## **4\. ChainMind 的核心差异化**

综合对比后，ChainMind 最应该强调的差异化是：

1.  不只看合约安全，还看早期买家是否撤退。
    
2.  不只看聪明钱买入，还判断该信号是否可复制。
    
3.  不只看钱包数量，还判断是否存在同实体分仓和假共识。
    
4.  不直接输出交易指令，而是输出研究结论、风险来源和观察条件。
    
5.  不停留在一次性评分，而是通过每日复盘持续校正规则。
    

一句话表达：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind 是 meme token 的链上风险研究 copilot， 不是自动炒币机器人。`

## **5\. 当前工程状态学习**

当前项目已经从纯文档阶段进入基础工程阶段。

已经具备：

-   Python 项目配置：`pyproject.toml`。
    
-   开发依赖：`requirements-dev.txt`。
    
-   样本 token JSON。
    
-   本地分析脚本：`scripts/analyze_token.py`。
    
-   CLI 入口：`src/chainmind/cli/analyze_token.py`。
    
-   编排层：`src/chainmind/orchestration/analyze_token.py`。
    
-   领域对象：`src/chainmind/domain/token_snapshot.py`。
    
-   风险评分模块：`src/chainmind/scoring/token_risk.py`。
    
-   机会评分模块：`src/chainmind/scoring/opportunity.py`。
    
-   优先级分级模块：`src/chainmind/scoring/priority.py`。
    
-   基础自动测试：`tests/unit/test_analyze_token_cli_foundation.py`。
    

已验证的最小链路：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`样本 token JSON -> TokenSnapshot -> token risk / opportunity score -> grade A/B/C/D -> action -> CLI 输出`

这说明项目已经可以开始从“想法验证”进入“规则验证”。

## **6\. 当前已经形成的判断框架**

ChainMind 的综合判断可以分为 8 类：

1.  是否进入分析。
    
2.  合约安全判断。
    
3.  买卖盘健康判断。
    
4.  早期买家行为判断。
    
5.  同实体 / 假共识判断。
    
6.  钱包质量判断。
    
7.  可复制性判断。
    
8.  是否推送判断。
    

最终输出应包含：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`Risk Score Entity Cluster Score Wallet Alpha Score Copyability Score Opportunity Score Priority Score Grade A/B/C/D`

可观察候选的大致逻辑是：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`风险不过高 + 买盘相对健康 + 早期买家未明显撤退 + 没有强同实体嫌疑 + 有高质量钱包参与 + 这个钱包信号仍有可复制窗口`

## **7\. Dune 手动分析学习**

Phase 1 的重点不是立即自动化，而是用 Dune 手动跑通分析路径。

已经理解的 Dune 分析模块包括：

-   token 基础信息。
    
-   合约创建信息。
    
-   DEX 交易与主要池子。
    
-   5 分钟买卖盘。
    
-   早期买家分析。
    
-   holder 集中度。
    
-   早期买家资金来源。
    
-   同来源资金统计。
    

关键学习点：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`同 funder 是风险证据之一， 但不能直接等于同一个真实人。`

需要进一步区分：

-   普通钱包地址。
    
-   DEX Router。
    
-   池子合约。
    
-   协议基础设施地址。
    
-   交易所或常见资金分发地址。
    

否则 same-funder 规则容易误判。

## **8\. AI 在项目中的正确位置**

AI 不应该直接读取全量原始交易并预测涨跌。

AI 更适合在规则过滤之后工作：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`程序负责计算 规则负责过滤 AI 负责解释 复盘负责校正`

AI 的输入应该是结构化摘要，例如：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`{"token":"XXX","chain":"bnb","risk_score":68,"opportunity_score":55,"early_buyer_exit_ratio":0.42,"same_funder_cluster_count":2,"copyability_score":61}`

AI 的输出应该回答：

-   是否值得观察。
    
-   机会来自哪里。
    
-   风险来自哪里。
    
-   是否可复制。
    
-   后续观察条件是什么。
    
-   不确定性在哪里。
    

## **9\. 最需要避免的表达**

项目介绍中应避免：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`AI 自动发现暴涨币 智能炒币机器人 自动跟单系统 保证发现 alpha 高胜率买入信号`

更推荐使用：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`链上行为风险过滤 meme token 投研辅助 可解释风险摘要 聪明钱可复制性判断 同实体与假共识识别`

推荐一句话：

![](http://localhost:63342/markdownPreview/1736260782/docs/learning?_ijt=o9fek9s7gq87sjai28vme2ljk7)

`ChainMind helps researchers filter risky meme tokens and explain on-chain signals before making manual decisions.`

## **10\. 后续最值得推进的方向**

短期最重要的不是做大而全，而是补齐一个可验证闭环。

推荐优先级：

### **P0：沉淀 Phase 1 Dune SQL**

把已经跑通的手动查询整理为固定 SQL 模板：

-   基础交易。
    
-   5m 买卖盘。
    
-   早期买家。
    
-   资金来源。
    
-   holder 集中度。
    

### **P0：完善 Token Risk Score**

把当前硬编码启发式规则逐步变成可配置权重：

-   低流动性。
    
-   net\_buy\_usd 转负。
    
-   trades / unique\_traders 异常。
    
-   早期买家清仓比例。
    
-   same-funder 风险。
    
-   holder 集中度。
    
-   合约安全风险。
    

### **P1：补充 Entity Cluster Score**

先做低成本版本：

-   同 funder。
    
-   买入时间集中。
    
-   新钱包比例。
    
-   买入前交易次数。
    
-   基础设施地址过滤。
    

### **P1：生成 AI 报告模板**

让 AI 基于结构化 JSON 生成：

-   A/B/C/D 等级解释。
    
-   机会来源。
    
-   风险来源。
    
-   可复制性说明。
    
-   后续观察条件。
    
-   不确定性。
    

### **P2：建立复盘数据**

每次分析或推送后记录：

-   15m / 1h / 6h / 24h 最大涨幅。
    
-   15m / 1h / 6h / 24h 最大回撤。
    
-   是否 rug。
    
-   是否存在普通用户可执行窗口。
    
-   当时风险分和机会分是否合理。
<!-- DAILY_CHECKIN_2026-05-24_END -->

# 2026-05-22
<!-- DAILY_CHECKIN_2026-05-22_START -->

### 1\. 基本概念概述

-   **EOA（Externally Owned Account，外部拥有账户）** 传统钱包账户，由私钥直接控制。最常见的 MetaMask 默认账户。
    
-   **智能账户（Smart Account / ERC-4337 Account Abstraction）** 基于智能合约实现的账户（也称 AA 账户）。用户不直接用私钥签名，而是通过 EntryPoint 合约和 UserOperation 发起交易。代表项目：ERC-4337、Pimlico、Alchemy Account、ZeroDev 等。  
    **智能账户（智能账户/ERC-4337 账户抽象）** 基于智能合约实现的账户（也称 AA 账户）。用户不直接用私钥签名，而是通过 EntryPoint 合约和 UserOperation 发起交易。代表项目：ERC-4337、Pimlico、Alchemy Account、ZeroDev 等。
    
-   **多签账户（Multi-Signature Wallet）** 需要多个私钥共同批准才能执行交易的智能合约钱包。代表项目：Gnosis Safe（现 Safe）、Gnosis MultiSig 等。
    

* * *

### 2\. 详细维度对比

| 维度 | EOA（传统钱包） | 智能账户（Smart Account） | 多签账户（Multi-Sig）  多签名 |
| --- | --- | --- | --- |
| 1. 谁持有控制权 | 单一私钥持有者 谁掌握私钥，谁就完全控制账户 | 合约 + 签名者 合约拥有逻辑控制权，私钥仅用于签名 UserOp。支持多因素或社交恢复 | 多人/组织共同控制 合约拥有最终控制权，需要设定阈值（Threshold） |
| 2. 谁可以发起交易 | 只有私钥持有者本人 必须用私钥签名 | 任何被授权的签名者或 Bundler 支持 Gasless、批量、自动化发起 | 任意签名者可提出交易，但需达到多人确认 一人无法单独执行 |
| 3. 是否支持多人确认 | 不支持 单签 | 支持（高度灵活） 可设置多签名者、不同权重、临时授权 | 原生强支持 典型 2/3、3/5、M-of-N 模式 |
| 4. 是否支持恢复、限额或自动化策略 | 极弱 丢私钥 = 资产永久丢失 几乎无限额、自动化功能 | 最强 • 社交恢复（朋友/邮箱/Guardian） • 每日限额 • 自动化支付、条件触发 • 模块化插件 | 较强 • 可设置多签恢复机制 • 限额模块 • 但自动化较弱（需额外模块） |
| 5. 典型使用场景 | • 个人日常小额交易 • DeFi 个人操作 • 新手入门 | • 个人高级钱包（Gasless、批量交易） • 团队/DAO 日常支出 • 企业级支付自动化 • 移动端友好钱包 | • DAO 国库管理 • 团队/公司资产共管 • 大额资金托管 • 机构/高净值用户 |
| 6. 主要风险点 | • 私钥泄露 = 资产全部丢失 • 单点故障 • 钓鱼签名风险高 • 无法挽回 | • 合约漏洞风险（虽经审计） • 依赖 Bundler / EntryPoint • 复杂度高，新手易误操作 • 部分实现仍有中心化风险 | • 审批流程慢 • 签名者勾结风险（内部作恶） • 合约漏洞 • 密钥管理复杂 |

* * *

### 3\. 权限与风险深度解读

**控制权本质差异**

-   **EOA**：控制权 = 私钥。极简但脆弱，一人掌控一切。
    
-   **智能账户**：控制权从“私钥”转移到“智能合约逻辑”。私钥只是“钥匙”之一，可随时更换或增加防护。
    
-   **多签**：控制权被明确分散到多人。任何单人无法独占资产。
    

**交易发起与批准流程**

-   EOA：签名即执行。
    
-   智能账户：签名 → UserOperation → Bundler 打包 → EntryPoint 执行（可实现“一人签名 + 自动执行”或“多人签名”）。
    
-   多签：提出交易 → 多人签名确认 → 达到阈值后执行。
    

**恢复能力**

-   EOA：几乎无恢复能力（除非提前在中心化交易所托管）。
    
-   智能账户：支持 Guardian（守护者）机制，可通过社交恢复、时间锁、邮箱验证等方式找回。
    
-   多签：可通过更换签名者或设置备用多签实现恢复。
    

**自动化与策略支持**

智能账户在这方面优势最大，可集成：

-   消费限额（spending limits）
    
-   自动支付订阅
    
-   条件交易（if-then 逻辑）
    
-   插件系统（Session Keys）  插件系统（会话密钥）
    

* * *

### 4\. 实际选择建议

-   **个人用户**：推荐从 **EOA 起步**，资金量增大后升级到 **智能账户**（兼顾便利性和安全性）。
    
-   **团队 / DAO / 公司**：强烈推荐 **多签账户**（Safe）作为主要资金管理工具，可结合智能账户作为执行层。
    
-   **高安全性需求**：**多签 + 智能账户混合使用**（多签作为最终国库，智能账户作为日常操作账户）。
    
-   **高便利性需求**：优先 **智能账户**（Gasless、批量、移动端友好）。
    

* * *

### 5\. 总结表格（一目了然）

| 账户类型  类类型 | 安全性  安全 | 便利性  方便 | 适合多人  多人 | 恢复能力 | 推荐指数（个人） | 推荐指数（团队） |
| --- | --- | --- | --- | --- | --- | --- |
| EOA | 低 | 高 | 不适合  不匹配 | 极差  不同之处 | ★★★☆☆ | ★☆☆☆☆ |
| 智能账户 | 中高  初中和高中 | 最高 | 支持 | 优秀 | ★★★★★ | ★★★★☆ |
| 多签账户 | 最高 | 中低 | 极适合 | 良好 | ★★★☆☆ | ★★★★★ |
<!-- DAILY_CHECKIN_2026-05-22_END -->

# 2026-05-21
<!-- DAILY_CHECKIN_2026-05-21_START -->


# **2026-05-21 项目进度总结**

## **1\. 今日目标**

今天的工作目标不是直接完成整个 ChainMind 项目，而是先完成以下两件事：

1.  确认当前 Python 工程能够在 PyCharm 中正常运行和测试。
    
2.  用一个真实 BSC 代币完成 Phase 1 Dune 手动分析流程的首轮检验。
    

本次检验采用的目标代币为：

| 字段 | 内容 |
| --- | --- |
| 链 | BSC / BNB Chain |
| 代币名称 | 14 |
| 代币地址 | 0x205f39c39f5fe15d4ef000aeb835de8deb264444 |
| 检验日期 | 2026-05-21 |

## **2\. 今日先完成的工程准备**

### **2.1 项目结构确认**

今天先确认了当前项目已经具备基础工程骨架：

-   `src/chainmind/`：正式 Python 包代码。
    
-   `scripts/`：本地脚本入口。
    
-   `tests/`：自动测试目录。
    
-   `samples/`：样例 token 数据。
    
-   `docs/`：项目设计、路线图和分析手册。
    
-   `experiments/`：实验与阶段检验记录。
    

这说明当前项目已经可以从“只有想法和文档”进入“可运行、可检验”的状态。

### **2.2 PyCharm 运行配置学习**

今天重点理解了 PyCharm `Run/Debug Configuration` 的作用。

当前运行配置中关键字段的含义如下：

| 配置项 | 含义 |
| --- | --- |
| Python Interpreter | 选择用哪个 Python 环境运行项目 |
| Script path | 选择要运行的 Python 脚本 |
| Parameters | 给本次运行传入输入文件和运行选项 |
| Working directory | 指定程序从哪个目录出发查找相对路径 |

本项目当前分析脚本需要传入 snapshot JSON 文件，因此不能只运行脚本本身，还需要给出输入参数。

示例参数：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`samples\tokens\example-healthy-token.json --json`

其含义是：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`使用健康样例 token 数据运行分析，并以 JSON 格式输出结果。`

### **2.3 本地脚本验证**

今天在 PyCharm 中完成了两个样例输入的运行验证。

**健康样例**

输入：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`samples\tokens\example-healthy-token.json`

观察到的结果方向：

| 字段 | 结果 |
| --- | --- |
| symbol | GOOD |
| grade | A |
| action | manual_review |
| risk_score | 20 |
| opportunity_score | 75 |

**风险样例**

输入：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`samples\tokens\example-risky-token.json`

观察到的结果方向：

| 字段 | 结果 |
| --- | --- |
| symbol | RISK |
| grade | D |
| action | filter |
| risk_score | 100 |
| opportunity_score | 30 |

这说明当前最小分析链路已经可以根据不同输入产生不同判断结果。

### **2.4 自动测试验证**

今天运行了当前项目的基础单元测试：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`tests\unit\test_analyze_token_cli_foundation.py`

运行结果：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`1 passed`

该测试确认了当前最小分析流程可以完成：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`TokenSnapshot -> analyze_token -> AnalysisResult`

当前工程层结论：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`PyCharm 本地运行、样例脚本和基础自动测试均已通过。`

## **3\. 今日学习到的工程概念**

### **3.1 命令行脚本与输入参数**

今天明确了一个重要概念：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`程序负责处理规则，参数负责告诉程序本次处理什么输入。`

当前 `scripts/analyze_token.py` 不是最终产品界面，而是早期开发和测试时的本地入口。

它的价值在于：

-   快速验证分析逻辑。
    
-   快速替换不同输入样例。
    
-   方便调试和自动测试。
    
-   后续可以被 API、定时任务或 Hermes 调用。
    

### **3.2 当前结构化结果与未来报告的区别**

当前脚本输出的是结构化分析结果，例如：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`risk_score opportunity_score grade action reasons`

它不是最终面向人的完整报告，而是后续报告层可使用的基础判断结果。

当前阶段的职责可以先这样理解：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`ChainMind 核心逻辑负责结构化判断。 AI 报告层负责把判断解释成人能读懂的摘要。 Hermes 更偏向负责触发、调度和推送。`

## **4\. Phase 1 今日检验内容**

### **4.1 Phase 1 当前理解**

Phase 1 当前先聚焦：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`用 Dune 手动分析 BSC token， 跑通风险过滤所需的数据查询和观察路径。`

今天做的是：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`Phase 1 Dune 手动分析流程首轮检验。`

它不是一次性完成整个项目，也不是马上完成所有后续阶段。

### **4.2 已检验的 Dune 分析模块**

今天已经对目标代币 `14` 检验了以下模块：

1.  DEX 交易活动观察。
    
2.  5 分钟买卖盘与净买入观察。
    
3.  Buyer Analysis 排名买家分析。
    
4.  Tracks All Trades 全量交易行为查看。
    
5.  Holder Analysis 持有人汇总与集中度字段查看。
    
6.  合约创建信息查询。
    
7.  早期买家入场前 BNB 资金来源查询。
    
8.  selected early buyers 的同来源资金汇总。
    

当前检验结论：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`Phase 1 的主要 Dune 查询路径已经能够跑通。`

## **5\. 目标代币检验记录**

### **5.1 合约创建信息**

今天已从 Dune 查询到该代币的创建记录：

| 字段 | 观察结果 |
| --- | --- |
| 创建时间 | 2026-05-17 16:12:21 |
| 区块号 | 98843750 |
| 创建交易 | 0xe9f50e4d32b55431717ee394d54f1615961b3f293dbdeb5d15a4bc8478b80d01 |
| 代币地址 | 0x205f39c39f5fe15d4ef000aeb835de8deb264444 |
| 创建侧地址观察值 | 0x757eba15a64468e6535532fcf093cef90e226f85 |

说明：

-   当前创建记录查询已可用。
    
-   本次只做流程检验，没有展开字节码审计。
    

### **5.2 交易与持有人字段**

今天从 Dune 看到了以下关键字段：

-   交易者活跃度。
    
-   `net_buy_usd` 变化。
    
-   买卖交易比例。
    
-   trader 的买入额、卖出额、净 token 变化。
    
-   holder 数量与 top holder 集中度字段。
    

Holder 汇总中观察到：

| 字段 | 观察值 |
| --- | --- |
| holder_count | 1985 |
| buy_volume_usd | 2188487.9 |
| sell_volume_usd | 2169786.4 |
| net_buy_usd | 18701.5 |
| top10_supply_pct | 0.2 |
| top20_supply_pct | 0.3 |

注意：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`集中度字段的百分比展示口径后续需要进一步确认， 不能仅凭显示值直接形成正式规则。`

### **5.3 早期买家分析**

今天已拿到前排早期买家的排名、首次买入时间、买入额和当前余额字段。

本次用于资金来源测试的前 5 个 early buyers 为：

| 排名 | 地址 |
| --- | --- |
| 1 | 0x0f80aa9dd2aff0d79455a1f7843c6e39e5a27985 |
| 2 | 0xa9b0295aa2d8486735d3fb3e92ab77e678ae3f9a |
| 3 | 0x79e337339346c9f5786a746916a0600d3f9eda65 |
| 4 | 0x175c6e02f549d9ae58205693854b2f8f8621022a |
| 5 | 0x4dc0c365578ed0b5161ce97551c613354df3e400 |

通过该模块，后续可以继续观察：

-   早期买家是否大量退出。
    
-   前排买家买入时间是否过度集中。
    
-   早期买家当前余额是否快速归零。
    

### **5.4 资金来源与同来源信号**

今天已完成前 5 个 early buyers 的入场前 BNB 资金来源测试。

观察到：

1.  排名第 1 的 early buyer 在首次买入前收到了多笔 BNB 入账。
    
2.  地址 `0x62ccef0b4545166f721caa9fee13c1d3767e27dc` 在选定 early buyers 中覆盖了 2 个买家。
    
3.  地址 `0x10ed43c718714eb63d5aa57b78b54704e256024e` 也覆盖了 2 个买家，但这类基础设施地址不能直接当作真实出资人判断。
    

本次学习到的关键点：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`同来源资金是风险证据之一， 但同一个来源地址不一定代表同一个真实人或同一实体。`

后续若要把 same-funder 信号写入规则，需要先区分：

-   普通钱包地址。
    
-   DEX Router。
    
-   池子合约。
    
-   其他协议基础设施地址。
    

## **6\. Phase 1 当前结论**

### **6.1 已完成**

截至 2026-05-21，已经完成：

-   Phase 1 的首轮流程检验。
    
-   Dune 主要分析模块可执行性验证。
    
-   当前项目 Python 本地运行与测试验证。
    
-   第一份 Phase 1 检验报告落盘。
    

本次检验报告位置：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`experiments/week1-risk-filter/phase1-check-report.md`

### **6.2 当前阶段判断**

当前可以将 Phase 1 状态记录为：

![](http://localhost:63342/markdownPreview/277497423/docs/progress?_ijt=3l4bp4ejcm389oqs945ukjbr59)

`Phase 1 首轮检验完成。`

这表示：

-   手动分析流程可跑通。
    
-   查询模块已被理解和验证。
    
-   可以进入下一阶段准备。
    

这不表示：

-   整个项目已经完成。
    
-   后续规则、报告、实体识别、推送、复盘已经完成。
<!-- DAILY_CHECKIN_2026-05-21_END -->

# 2026-05-20
<!-- DAILY_CHECKIN_2026-05-20_START -->



几天继续了链上数据分析，AI+Defi投研报告自动项目的学习详细链接[链接](https://github.com/may-tonk/ai-web3-school-cohort-0/tree/codex/chainmind-foundation)
<!-- DAILY_CHECKIN_2026-05-20_END -->

# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->




**今天和AI探讨了链上数据分析，AI+Defi的想法，简单的建立了一个工作项目计划，内容太多了，上传到了AI x Web3school的GitHub了；详细请查看**[**链接**](https://github.com/may-tonk/ai-web3-school-cohort-0/blob/master/daily/2026-05-19/AI_DeFi_Meme_Workflow_%E5%AD%A6%E4%B9%A0%E6%80%BB%E7%BB%93.md)
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->





\# 2026-05-18 — Day 1: 初始化与学习启动

\> 日期：2026-05-18

\> 周次：Week 1

\> 主题：AI and Web3 foundations — 基础对齐 + 数据连接

\---

\## 📝 今日学习内容

\### 课程/资料阅读

\- \[x\] 读取 Learning Agent Prompt: [https://aiweb3.school/learning-agent.zh.txt](https://aiweb3.school/learning-agent.zh.txt)

\- \[x\] 阅读 Handbook 结构和内容：[https://aiweb3.school/zh/handbook/](https://aiweb3.school/zh/handbook/)

\- \[x\] 了解 WCB Agent API 文档: [https://web3career.build/llms.txt](https://web3career.build/llms.txt)

\### 关键收获

\- Learning Agent 设计原则：轻量优先、人工确认、开源沉淀、隐私安全

\- 仓库结构：daily/ tasks/ experiments/ handbook-feedback/ hackathon/ submissions/ templates/

\- 每日流程：课程 → 实践 → 笔记 → 打卡

\- 课程时长确认：\*\*4 周\*\*（2026-05-18 → 2026-06-14）

\---

\## 🚀 今日产出物

\### 1. GitHub 学习仓库（完成初始化）

\- 创建本地仓库并 push 到 GitHub

\- 仓库地址：[https://github.com/may-tonk/ai-web3-school-cohort-0](https://github.com/may-tonk/ai-web3-school-cohort-0)

\- 总计 **5 次 commit**

\### 2. 核心文件

\- \[x\] `profile.md` — 学员画像（技能、目标、方向）

\- \[x\] `learning-plan.md` — 4 周精确学习计划（ChainMind 项目主线）

\- \[x\] `tasks/week1-daily-tasks.md` — Week 1 每日任务清单

\- \[x\] `README.md` — 项目介绍 + Week 1 目标 + 记录结构

\### 3. 目录结构

\- \[x\] `daily/` — 每日学习笔记

\- \[x\] `tasks/` — 每周任务清单

\- \[x\] `experiments/` — 实验记录

\- \[x\] `handbook-feedback/` — 手册反馈

\- \[x\] `submissions/` — 最终交付物

\- \[x\] `templates/` — 笔记模板

\- \[x\] `hackathon/` — 黑客松材料

\### 4. 环境配置

\- \[x\] `.env` 安全存放 WCB Agent Secret API Key（已加入 .gitignore）

\- \[x\] `.gitignore` — 排除敏感文件

\- \[x\] 仓库移至 D 盘`D:\ai-web3-school-cohort-0`）

\### 5. WCB 平台连接

\- \[x\] 验证 WCB API 连接正常

\- \[x\] 确认已录取 AI × Web3 School（Program ID: `cmnx791nl008sru0167pzp4ki`）

\- \[x\] 查看今日活动安排（Co-learning + AI 基础讲座）

\---

\## 📊 今日打卡信息

**打卡类型**：初始化完成 / 学习记录

**主要证据**：GitHub 仓库 + 学习计划 + 每日笔记

**证据链接**：[https://github.com/may-tonk/ai-web3-school-cohort-0](https://github.com/may-tonk/ai-web3-school-cohort-0)

\---

\## 🤔 反思与问题

1\. 平台任务似乎尚未发布`tasks.listForLearner` 返回空），可能需要明天再查。

2\. 今天以工程化初始化为主，明天开始进入核心学习与编码阶段。

3\. 需要了解 Hermes Agent 的具体使用方式，以便更好地将学习流程自动化。

\---

\## 📅 明日计划（Day 2 — 5/19）

\- \[ \] 搭建 `chainmind/core/agent.py` ReAct 骨架

\- \[ \] 学习 Handbook LLM / Tool Use 章节

\- \[ \] 实现多工具支持

\- \[ \] git commit: `feat: multi-tool support with retry`

\---
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
