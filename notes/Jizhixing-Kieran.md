---
timezone: UTC+8
---

# Jizhixing-Kieran

**GitHub ID:** Jizhixing-Kieran

**Telegram:** @Kieran_Ji

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-19
<!-- DAILY_CHECKIN_2026-05-19_START -->
# 拒绝纸上谈兵，用费曼技巧复盘我的个人 Agent 开发之路

**写在前面：我的学习理念**

在今天的共学营学习中，我没有选择传统的摘抄式笔记，而是更倾向于用**费曼技巧**来复盘——即“把自己做了什么、怎么做的讲出来”。只有能清晰地讲明白一个技术落地的过程，才算是真正掌握了它。

**第一步：大模型调研与选型**

在开发个人 Agent 的初期，我并没有盲目上手，而是对市面上主流的大模型能力进行了深度调研。我先后对比了豆包、DeepSeek、KIMI 以及阿里千问等多个模型的表现。

经过综合考量，我最终确定了使用 **Qwen3.6-Max** 作为我的核心模型。它在代码逻辑理解和长上下文处理上的表现，非常契合我开发 Agent 的需求。

**第二步：部署 Claude Code 并接入千问**

选型确定后，我迅速部署了 **Claude Code (CC)**，并成功将其与千问大模型进行了接入。  
  

![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/Jizhixing-Kieran/images/2026-05-19-1779188258024-image.png)

接入完成后，我立刻用千问进行了一次 **Vibe Coding** 的实战体验。我的第一个目标是实现 Agent 的**自动化定时和提醒功能**，这对于我日常依赖的飞书机器人至关重要。

**第三步：解决痛点——赋予 CC “长期记忆”**

在实际使用中，我发现了一个明显的痛点：每次调用强大的 Claude Code 和 Qwen3.6-Max 时，它们都会“失忆”，丢失之前的对话上下文和项目背景。

为了解决这个问题，我并没有妥协，而是动手为它建立了记忆系统：

1.  **建立记忆文件**：我让 CC 创建并维护了核心的记忆文档。
    
2.  **固化核心信息**：将“我是谁（独立开发者）”、“项目是什么（飞书 AI 聊天机器人）”、“文件在哪（关键路径速查）”等信息写入记忆。
    
3.  **跨会话继承**：现在，每次新对话启动时，CC 都会自动加载这些背景，真正实现了跨会话的持续开发。
    

![image.png](https://raw.githubusercontent.com/IntensiveCoLearning/AI-Web3-School/main/assets/Jizhixing-Kieran/images/2026-05-19-1779188203878-image.png)

**总结**

今天不仅完成了个人 Agent 的核心功能迭代，更重要的是打通了“Claude Code + 千问大模型”的高效开发流。从解决失忆问题到落地定时提醒，AI 真正成为了我开发路上的得力兄弟。

**下一步计划：** 继续拓展飞书机器人的业务功能，优化代码沙箱的安全性，让 Agent 更稳定地服务于我的日常生活。

昨天打卡结果直接编辑在了GitHub本地仓库中，所以打卡失败了，今天过来补一下
<!-- DAILY_CHECKIN_2026-05-19_END -->
<!-- Content_END -->
