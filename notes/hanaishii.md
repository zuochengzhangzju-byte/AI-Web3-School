---
timezone: UTC+8
---

# hanaishii

**GitHub ID:** hanaishii

**Telegram:** 

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-29
<!-- DAILY_CHECKIN_2026-05-29_START -->
\# 学习笔记：HashKey模型——AI Agent链上落地的三层闭环架构 这套架构是为解决AI Agent在Web3/DeFi场景落地的核心痛点而设计，构建了「底层支撑-安全交互-价值沉淀」的全链路闭环，让AI的链上行为从“不可控、无价值”变成“可管控、可确权”。 --- ## 一、价值沉淀层：让AI的产出真正成为链上资产 这一层解决的核心问题，是AI的价值如何从“无形的输出”变成“可确权、可流转的链上资产”。 - 核心逻辑：将AI生成的数字内容、推理服务、训练数据集，甚至AI Agent自身的行为模式，通过代币化（Tokenization）完成链上确权，让AI与AI之间也能实现自动化的商业协作，最终完成价值的沉淀与流转。 - 典型实践：Virtuals Protocol、Clanker这类项目，正是通过链上代币化的方式，打通了AI价值的流转路径，实现了AI-to-AI的商业闭环。 --- ## 二、安全交互层：给AI的链上操作加上“三重防护锁” 这是整个架构的核心安全屏障，专门针对大模型幻觉、逻辑漏洞、越权操作等风险，给AI参与DeFi交互加上了全流程的约束，避免无差别操作导致的资损。 1. **共管式智能钱包**：基于ERC-4337账户抽象和MPC多方安全计算技术，采用“人类-智能体-托管商”共管的签名机制，通过多方协同管控，避免单点操作带来的风险。 2. **带边界的打包授权**：给AI的所有操作划定明确权限，任何授权都必须包含「操作意图+执行计划+ABI级风控规则+结束条件」，从源头限制AI的操作范围，防止幻觉引发的失控行为。 3. **标准化操作处方**：为AI的DeFi交互设置“安全路径白名单”，仅允许调用Uniswap等经过审计的标准化协议接口执行操作，规避自定义逻辑可能带来的漏洞与逻辑硬伤。 --- ## 三、底层支撑层：构建去信任的AI运行底座 这一层为整个体系提供去中心化的基础设施支撑，摆脱对Web2中心化巨头的依赖，保障AI Agent生态的中立性、安全性与可扩展性。 - 去中心化算力（DePIN）：打破Web2巨头对高端GPU资源的垄断，汇聚全球闲置算力资源，为AI的训练与推理提供分布式算力支持，典型项目包括Bittensor、Akash、Render、Aethir等。 - 去中心化存储：保障AI工作流的隐私安全与训练数据的完整性，避免数据被篡改、污染或滥用，实现数据的可验证与长期保存，Filecoin、Arweave、0G Network等项目为AI数据提供了可信的存储底座。 --- ## 整体逻辑梳理 这套架构是一个从“下到上”的完整闭环：去中心化的算力与存储提供了可信的运行底座，安全交互层把控AI链上操作的全流程风险，最终让AI的价值通过价值沉淀层实现确权、流转与沉淀，解决了AI Agent在Web3落地的三大核心痛点：基础依赖中心化、链上操作不可控、AI价值无闭环。
<!-- DAILY_CHECKIN_2026-05-29_END -->

# 2026-05-28
<!-- DAILY_CHECKIN_2026-05-28_START -->

| 技术方向 | 代表方案 | 核心能力 | 落地价值 |
| --- | --- | --- | --- |
| zkML（零知识机器学习） | - | AI 模型在不泄露核心权重的前提下，向智能合约证明推理结果的真实性 | 解决 AI 链上部署的 “黑盒验证” 矛盾，兼顾模型隐私与链上可验证性 |
| zk-Proof + TEE（可信执行环境） | Layer2 隐私层、Phala Network 等硬件隐私层 | 将 “默认隐私” 作为网络底座，开发者可直接调用隐私基础设施 | 大幅降低隐私应用的开发门槛，让隐私能力成为链上的 “原生功能” |
<!-- DAILY_CHECKIN_2026-05-28_END -->

# 2026-05-25
<!-- DAILY_CHECKIN_2026-05-25_START -->


Workflow（AI 工作流）是一种预定义、线性化的自动化任务执行框架： 核心逻辑：将多个 AI 模型 / 工具调用按固定顺序串联，形成闭环流程 数据流转：上一步的输出结果，直接作为下一步的输入参数 灵活性：流程节点中可嵌入人工干预环节，适配复杂场景  

workflow vs agent  

| 对比维度 | Workflow（工作流） | Agent（智能体） |
| --- | --- | --- |
| 流程逻辑 | 预定义、写死的固定流程：每一步的动作、顺序提前配置完成，不可随意变更 | 动态、自主决策流程：可根据任务进展，自主判断下一步调用的工具 / 动作 |
| 适用场景 | 确定性强、规则明确的任务（如批量翻译、数据清洗、标准化文案生成） | 不确定性高、需要灵活决策的任务（如复杂问题拆解、多步骤推理、开放式对话） |
| 核心特点 | 流程透明、可控性强，适合标准化自动化 | 自主性强、适配性高，适合非标准化、探索性场景 |
<!-- DAILY_CHECKIN_2026-05-25_END -->

# 2026-05-24
<!-- DAILY_CHECKIN_2026-05-24_START -->



Agent = 能持续调用工具、读取状态、调整步骤的 AI 系统。  

| 概念 | 核心要点 |
| --- | --- |
| Tool Use（工具使用） | 让 Agent 从 “纯回答” 升级为 “能做事”，但工具会放大风险（读网页、写数据库、发交易的风险等级完全不同） |
| Planning（规划） | 把目标拆解为可执行步骤，需明确：每步用什么工具、是读 / 写操作、是否需要人工确认、失败后能否重试 |
| State（状态） | 任务状态必须外置可查，不能只藏在 prompt 对话历史中 |
| Reflection（反思） | 自我检查可提升结果质量，但不能替代外部验证 |
| Multi-Agent（多智能体） | 多 Agent 协作时，需警惕责任边界模糊、权限扩散的问题 |
<!-- DAILY_CHECKIN_2026-05-24_END -->

# 2026-05-23
<!-- DAILY_CHECKIN_2026-05-23_START -->




Few-shot（少样本提示）是一种 Prompt 工程方法，核心是在提示词中加入少量示例，引导模型模仿示例的判断逻辑、输出格式与风格，解决 “规则 / 边界难以用一句话明确” 的任务。 它主要适用于三类场景：交易解释（需同时呈现资产变化、风险提示等多维度信息，示例比纯文字更直观）、生成格式复杂的输出（如特定结构的 JSON、Markdown 报告）、内容审核（清晰展示合规 / 违规边界）。 关键注意事项：示例并非一次性素材，而是需随业务规则、评估用例迭代更新的测试资产；当业务规则或数据格式变更时，旧示例可能误导模型，必须同步维护。
<!-- DAILY_CHECKIN_2026-05-23_END -->

# 2026-05-22
<!-- DAILY_CHECKIN_2026-05-22_START -->





Framework是把模型、工具、状态、检索、评估、部署组织成可维护的系统。框架解决的是工程组织问题。
<!-- DAILY_CHECKIN_2026-05-22_END -->

# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->






![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/hanaishii/images/2026-05-19-1779205752836-image.png)
<!-- DAILY_CHECKIN_2026-05-19_END -->

# 2026-05-18
<!-- DAILY_CHECKIN_2026-05-18_START -->








![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/hanaishii/images/2026-05-18-1779119674940-image.png)![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/hanaishii/images/2026-05-18-1779119851332-image.png)![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/hanaishii/images/2026-05-18-1779119869424-image.png)
<!-- DAILY_CHECKIN_2026-05-18_END -->
<!-- Content_END -->
