---
tags:
  - TRAE
  - SOLO
  - Skill
  - 极客时间
type: 课程笔记
status: 完成
created: 2026-05-16
updated: 2026-05-16
source: "极客时间 · Claude Code Skill 入门实战课 · 陈燊燊"
duration: "08:12"
---

# 课程介绍｜这门课程能给你带来什么？

> 告别低效重复，构建 AI 自动化工作流体系。用 SOLO（Claude Code 产品形态）将日常高频、重复的工作场景封装成可复用的 Skill，让 AI 真正成为生产力工具而非玩具。

> [!note] 通俗摘要
> 这门课解决一个核心问题：**如何让 AI 帮你反复做同一类工作**，而不是每次从头描述需求。答案是把工作流程封装成 Skill——一个带有结构化指令、模板和参考资料的 AI 技能包。课程用 9 个真实职场场景（会议纪要、竞品逆向、需求清洗、PRD 文档、产品原型……）手把手演示如何从 0 到 1 设计、创建和迭代一个 Skill。

## 核心概念

**什么是 Skill**

Skill 是一个结构化的 AI 工作流配置包，包含：
- `SKILL.md`：主指令文件，定义触发场景（description）和工作流（步骤、逻辑、输出格式）
- `assets/`：模板文件，如输出格式模板
- `references/`：参考资料，如分类指南、识别模式
- `scripts/`：辅助脚本，如 CSV 读取工具

> *📌 Skill 不是 prompt，它是可以被反复调用的「工作流单元」，像代码函数一样有输入/输出/逻辑/参考资料。*

**Skill 的触发机制**

SKILL.md 头部的 `description` 字段决定何时自动触发。描述越精准，触发越准确。好的 description 要列举：典型用户语言、适用场景、关键词变体。

**课程覆盖的 9 个 Skill 场景**

| 编号 | Skill 名 | 解决什么问题 |
|------|---------|------------|
| 01 | meeting-minutes | 会议录音/转写稿 → 结构化会议纪要 |
| 02 | product-reverse-analysis | 产品截图 → 业务逻辑/架构分析报告 |
| 03 | product-requirement-miner | 用户评论 CSV → 产品优化路线图 |
| 04 | prd | 模糊想法 → 完整 PRD 文档 |
| 05 | product-prototype-design | 产品描述 → 可交互 HTML 原型 |
| 06 | data-analysis | CSV 数据 → 业务分析报告 |
| 07 | ai-news | 自动抓取 → AI 资讯展示页面 |
| 08 | skill-evolver / weekly-report | 对话复盘 → 优化版 Skill；周报生成 |
| 09 | OpenClaw | 专属 AI 助理（综合能力） |

## 在大赛中的位置

> *📌 这门课直接对应 SOLO 技能创作赛的「创作」赛道。每节课的 Skill 都可以作为参赛作品的原型，结合自己的真实场景改造后发布。*


