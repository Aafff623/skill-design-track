---
name: ai-news
description: 获取每日最新AI资讯并生成赛博朋克风格展示页面。当用户提到"AI资讯"、"AI新闻"、"今日AI动态"、"最新AI消息"、"AI行业资讯"或类似需求时触发此skill。即使用户没有明确说要生成页面，只要提到想了解AI资讯、查看AI新闻、获取AI动态，都应该使用此skill来抓取数据并生成可视化页面。
---

# AI资讯获取与展示

这个skill帮助用户获取最新的AI行业资讯，从多个可靠数据源抓取内容，并生成赛博朋克风格的HTML展示页面。

## 工作流程

### Step 1: 数据获取

使用agent-browser skill访问以下数据源获取AI资讯：

1. **AIBase** - `https://www.aibase.com/zh/news`
2. **36氪 AI频道** - `https://www.36kr.com/information/AI/`

#### 抓取要求

- 每个数据源至少抓取5条资讯
- 两个数据源合计目标15-20条
- 去除明显重复的内容（相同主题、相似标题）
- 如果某个数据源无法访问或加载失败，跳过该源，继续其他数据源
- 确保不会因为单个数据源失败而整体失败

#### 数据提取字段

对每条资讯提取以下信息：
- **title**: 文章标题（保持原文）
- **description**: 文章主旨的精炼摘要，控制在80字以内
- **link**: 文章详情链接（如果链接不完整，自动补全域名前缀）
- **tags**: 2-4个相关标签数组，根据标题和内容自动推断（如：["AI", "大模型", "应用"]）

### Step 2: 生成数据文件

将抓取的数据整理为JavaScript格式，保存为 `ai-news-data.js`：

```javascript
const NEWS_DATA = [
  {
    "title": "文章标题",
    "description": "文章主旨80字以内的精炼摘要",
    "link": "https://example.com/article",
    "tags": ["AI", "相关标签1", "相关标签2"]
  }
  // ... 更多资讯
];
```

**重要注意事项**：
- JS文件中字符串内部的双引号必须用反斜杠 `\` 转义
- 确保生成的是合法的JavaScript语法
- 数组最后一项后面不要加逗号

### Step 3: 生成展示页面

创建赛博朋克风格的HTML展示页面 `ai-news.html`，通过 `<script src>` 引入数据文件。

#### HTML结构要求

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI资讯 - 赛博朋克风格</title>
    <!-- CSS样式 -->
</head>
<body>
    <!-- 页面内容 -->

    <!-- 在 </body> 前引入数据文件 -->
    <script src="ai-news-data.js"></script>
    <script>
    // NEWS_DATA 变量来自 ai-news-data.js
    // 此处编写渲染逻辑
    </script>
</body>
</html>
```

#### 设计要求

**赛博朋克视觉风格**：
- 深色背景（#0a0e27、#1a1a2e等深蓝/黑色调）
- 霓虹灯效果（使用 text-shadow 和 box-shadow 实现发光效果）
- 科技感字体（推荐使用系统等宽字体或引入 Google Fonts）
- 渐变色彩（青色、紫色、粉色的霓虹配色）
- 扫描线或网格背景效果

**功能要求**：
- 卡片式布局展示每条资讯
- 每个卡片显示：标题、描述、标签、原文链接
- 响应式设计，支持移动端（使用 CSS Grid 或 Flexbox）
- 顶部显示日期和资讯总条数
- 标签使用不同颜色区分
- 链接hover效果（霓虹发光）

**交互优化**：
- 卡片hover时产生发光或抬升效果
- 平滑的过渡动画
- 链接在新标签页打开（`target="_blank"`）

## 输出文件

在当前工作目录生成以下文件：

1. `ai-news-data.js` - 资讯数据文件（JavaScript变量）
2. `ai-news.html` - 赛博朋克风格展示页面

## 完成后的提示

生成文件后，告知用户：

```
✅ AI资讯已获取完成！

📁 生成文件：
- ai-news-data.js（共 X 条资讯）
- ai-news.html（赛博朋克风格展示页面）

🌐 查看方式：
在浏览器中打开 ai-news.html 即可查看

数据源：AIBase、36氪 AI频道
```

## 错误处理

- 如果所有数据源都无法访问，明确告知用户并建议检查网络连接
- 如果只有部分数据源失败，继续使用可用数据源，并在最后提示用户
- 如果抓取的资讯数量少于预期，告知用户实际获取的数量

## 注意事项

- 数据抓取可能需要一些时间，请耐心等待
- 确保生成的HTML文件可以在各种现代浏览器中正常显示
- description的摘要应该精炼、准确，避免过长或过于简单
- tags要有意义，反映资讯的核心主题
