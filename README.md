# Claude Code Skill 入门实战课

> 告别低效重复，构建 AI 自动化工作流体系。用 SOLO 将日常高频、重复的工作场景封装成可复用的 Skill。

## 课程信息

| 项 | 内容 |
|----|------|
| 讲师 | 陈燊燊（资深提示词工程师、资深 AI OPC 场景化教练） |
| 副标题 | 告别低效重复，构建 AI 自动化工作流体系 |
| 共 | 9 个 Skill 场景 + 1 个综合整合 |

## 9 个 Skill 场景

| # | 文件夹 | Skill | 核心能力 |
|---|--------|-------|---------|
| 01 | `lesson1-intro` | — | Skill 概念、文件结构、触发机制 |
| 02 | `lesson2-meeting-minutes` | meeting-minutes | 会议录音/转写稿 → 结构化会议纪要 |
| 03 | `lesson3-product-reverse` | product-reverse-analysis | 产品截图 → 业务逻辑/架构分析报告 |
| 04 | `lesson4-requirement-miner` | product-requirement-miner | 用户评论 CSV → 产品优化路线图 |
| 05 | `lesson5-prd` | prd | 模糊想法 → 完整 PRD 文档（8段式） |
| 06 | `lesson6-prototype-design` | product-prototype-design + pinme-deploy | 产品描述 → 可交互 HTML 原型 + IPFS 部署 |
| 07 | `lesson7-data-analysis` | data-analysis | CSV 数据 → 业务分析报告（What→SoWhat→NowWhat） |
| 08 | `lesson8-ai-news` | ai-news | 自动抓取 → AI 资讯展示页面（赛博朋克风格） |
| 09 | `lesson9-skill-evolver` | skill-evolver + weekly-report | 对话复盘 → 优化版 Skill；纯文本周报生成 |

## 文件结构

```
skill-design-track/
├── lesson1-intro/           # 课程介绍 + Skill 基础概念
├── lesson2-meeting-minutes/ # Skill 01: 会议纪要生成
├── lesson3-product-reverse/ # Skill 02: 竞品逆向分析
├── lesson4-requirement-miner/ # Skill 03: 需求清洗
├── lesson5-prd/             # Skill 04: PRD 文档工厂
├── lesson6-prototype-design/ # Skill 05: 原型演示 + pinme 部署
├── lesson7-data-analysis/   # Skill 06: 数据分析
├── lesson8-ai-news/         # Skill 07: AI 情报雷达
├── lesson9-skill-evolver/   # Skill 08: Skill 进化管家
└── README.md
```

## Skill 核心设计原则

### 1. 触发机制
`description` 字段列举典型用语、适用场景、关键词变体，描述越精准触发越准确。

### 2. 人在环路中
关键决策点使用 `AskUserQuestion` 让用户确认，而非全自动跑完——比全自动更安全。

### 3. 强指令词
- **必须**、**始终**、**确保** → 执行力高
- **严禁**、**禁止**、**切勿** → 明确禁区

### 4. Refine-Before-Write
先逼用户想清楚（核心逻辑、目标用户、成功指标），再帮写。缺少关键信息时主动追问，禁止直接生成。

### 5. 结构分离
- `SKILL.md` — 主指令（做什么+怎么做）
- `assets/` — 模板文件
- `references/` — 参考资料
- `scripts/` — 辅助脚本

## 快速开始

```bash
# 查看某个 Skill 的结构
ls -la lesson2-meeting-minutes/

# 查看 Skill 主文件
cat lesson2-meeting-minutes/SKILL.md
```

## 赛道建议（SOLO Skill 大赛）

| 赛道 | 推荐 Skill |
|------|-----------|
| More Than Coding | meeting-minutes、product-requirement-miner、weekly-report |
| Code With SOLO | product-prototype-design、data-analysis、ai-news |

**高分要素**：真实场景 + 前后对比截图 + 可访问的演示链接

## 参考资料

- 原始课程资料：`extracted/lessonN/`
- 课程笔记：`study/` 目录
- 极客时间：[Claude Code Skill 入门实战课](https://time.geekbang.org/)