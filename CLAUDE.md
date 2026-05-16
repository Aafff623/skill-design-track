# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

Claude Code Skill 入门实战课学习仓库。课程共 9 个 Skill 场景，覆盖从会议纪要到专属 AI 助理的完整工作流。

| 编号 | 文件夹 | Skill 名 | 解决什么问题 |
|------|--------|---------|------------|
| 01 | `lesson1-intro` | — | Skill 概念、文件结构、触发机制 |
| 02 | `lesson2-meeting-minutes` | meeting-minutes | 会议录音/转写稿 → 结构化会议纪要 |
| 03 | `lesson3-product-reverse` | product-reverse-analysis | 产品截图 → 业务逻辑/架构分析报告 |
| 04 | `lesson4-requirement-miner` | product-requirement-miner | 用户评论 CSV → 产品优化路线图 |
| 05 | `lesson5-prd` | prd | 模糊想法 → 完整 PRD 文档 |
| 06 | `lesson6-prototype-design` | product-prototype-design + pinme-deploy | 产品描述 → 可交互 HTML 原型 + IPFS 部署 |
| 07 | `lesson7-data-analysis` | data-analysis | CSV 数据 → 业务分析报告 |
| 08 | `lesson8-ai-news` | ai-news | 自动抓取 → AI 资讯展示页面 |
| 09 | `lesson9-skill-evolver` | skill-evolver + weekly-report | 对话复盘 → 优化版 Skill；纯文本周报生成 |

## Skill 架构规范

每个 Skill 遵循统一文件结构：

```
skill-name/
├── SKILL.md          # 主指令文件（触发条件 + 工作流 + 输出格式）
├── assets/           # 模板文件（输出格式模板）
├── references/       # 参考资料（分类指南、识别模式）
└── scripts/          # 辅助脚本（CSV 读取等）
```

**SKILL.md 头部必填字段：**

```yaml
---
name: skill-name
description: 触发门控 — 列举典型用语、适用场景、关键词变体
---
```

## Skill 设计核心原则

### 1. 触发机制
`description` 字段决定何时自动触发。描述越精准，触发越准确。列举：
- 典型用户语言
- 适用场景
- 关键词变体

### 2. 人在环路中（Human-in-the-Loop）
在关键决策点使用 `AskUserQuestion` 让用户确认，而非全自动跑完。比全自动更安全。

### 3. 强指令词
- **必须**、**始终**、**确保** — 执行力高
- **严禁**、**禁止**、**切勿** — 明确禁区
- 避免弱描述（尽量、最好）

### 4. 结构分离
- `SKILL.md` 只写「做什么+怎么做」
- 模板抽到 `assets/`
- 规则抽到 `references/`
- 保持主文件简洁

### 5. Refine-Before-Write
先逼用户想清楚，再帮写。缺少核心信息时主动追问，禁止直接生成。

## 高价值 Skill 特征

- 解决高频重复的真实工作场景
- 有结构化输出格式，效果可对比、可验收
- 配有模板和参考资料，减少每次调用的认知负担
- 支持迭代进化（skill-evolver 模式）

## 赛道建议（SOLO Skill 大赛）

| 赛道 | 推荐 Skill |
|------|-----------|
| More Than Coding | meeting-minutes、product-requirement-miner、weekly-report |
| Code With SOLO | product-prototype-design、data-analysis、ai-news |

高分要素：真实场景 + 前后对比截图 + 可访问的演示链接。

## 技术约束

| Skill | 技术栈 | 特殊要求 |
|-------|--------|---------|
| product-prototype-design | HTML5 + TailwindCSS（CDN）+ Vanilla JS | 严禁蓝紫渐变，行业驱动设计规范 |
| pinme-deploy | IPFS | SPA 必须用 Hash 路由 |
| ai-news | agent-browser 抓取 | 需提前安装依赖 |
| data-analysis | pandas/numpy/scipy/matplotlib | 支持 `--quick --auto` 跳过交互 |

## 约定

- 使用 Conventional Commits 格式提交代码
- 每个 Lesson 包含：原始资料（`extracted/lessonN/`）、课程笔记（`study/`）
- AI 配置标记：`CLAUDE.md`、`AGENTS.md`、`.claude/` 等