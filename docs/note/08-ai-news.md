# 08｜情报雷达（ai-news）

> agent-browser 抓取 AIBase + 36氪，生成赛博朋克风格资讯展示页面。

## 核心概念

### 工作流

agent-browser 抓取 → 整理数据（ai-news-data.js）→ 生成展示页面（ai-news.html）

### 数据与展示分离

- ai-news-data.js — 纯数据文件，通过 script src 引入
- ai-news.html — 展示页面，独立更新
- 每天更新只需重新生成 JS，数据格式不变

### 抓取规格

- 每个数据源至少 5 条，合计目标 15-20 条
- 去除明显重复（相同主题/相似标题）
- 某个数据源失败 → 跳过，继续其他源

### 赛博朋克视觉要点

- 背景：深蓝/黑色调（#0a0e27、#1a1a2e）
- 发光效果：text-shadow + box-shadow 实现霓虹
- 配色：青色、紫色、粉色三色系
- 扫描线或网格背景

### 安装依赖

npm install -g agent-browser
agent-browser install
npx skills add vercel-labs/agent-browser --skill agent-browser

## 竞赛价值

- 展示「输入一条指令 → 自动获取当日 AI 资讯 → 生成可查看页面」的完整截图
- 视觉效果好，实用性强
