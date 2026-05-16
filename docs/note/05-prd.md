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
duration: "09:16"
skill: "product-prototype-design + pinme-deploy"
---

# 05｜原型演示：自然语言生成可交互 Demo

> Skill 名：`product-prototype-design` — 快速生成高保真的产品交互原型（单个独立 HTML 文件）。`pinme-deploy` — 一键部署前端静态网站到 IPFS 网络。

> [!note] 通俗摘要
> 这节课实际上教了两个 Skill 的组合：先用 `product-prototype-design` 把产品描述生成可交互的 HTML 原型，再用 `pinme-deploy` 把这个 HTML 文件一键发布到 IPFS 网络（零配置、无服务器），获得可分享的链接。亮点是**行业驱动的设计规范**——不同行业（科技/金融/电商/餐饮……）自动套用对应的配色、字体和交互风格，而不是千篇一律的蓝紫渐变。

## 核心概念

**product-prototype-design：5 阶段流程**

```mermaid
graph LR
    P1[检测模式\nA明确行业/B行业模糊/C只有想法]
    P2[推断行业\n科技/金融/电商/餐饮/医疗……]
    P3[选择视觉规范\n配色+字体+圆角+动效]
    P4[生成原型\nHTML5+TailwindCSS+Vanilla JS\n单文件交付]
    P5[输出与迭代\n部署+询问调整方向]
    P1-->P2-->P3-->P4-->P5
```

**行业视觉规范（部分）**

| 行业 | 主色调 | 风格特点 | 圆角/阴影 |
|------|--------|---------|---------|
| 科技/互联网 | 深蓝/宝蓝 | 专业冷静科技感 | 极细边框，低阴影 |
| 电商/零售 | 红/橙/橘黄 | 活泼促销感 | 大圆角 `rounded-2xl`，强阴影 |
| 餐饮/美食 | 暖橙/暖红 | 食欲温暖烟火气 | 有机形状，背景米白 |
| 游戏/娱乐 | 紫/蓝/霓虹色 | 炫酷年轻视觉冲击 | 霓虹发光边框 |

**硬性禁忌（所有行业）**

> *📌 严禁使用蓝色到紫色的渐变（`from-blue-500 to-purple-500`），拒绝「千篇一律的 AI 审美」。*

**技术栈**

- HTML5 + TailwindCSS（CDN）+ Vanilla JavaScript（ES6+）
- Lucide Icons（图标）
- 所有样式、逻辑、Mock 数据内联到单个 `.html` 文件

**pinme-deploy：7 步部署流程**

```
检查 pinme 安装 → 识别项目类型 → 检查路由模式 → 执行构建 → 验证目录 → 上传 IPFS → 返回访问 URL
```

> *📌 SPA 项目必须使用 Hash 路由（HashRouter / createWebHashHistory），否则子页面会出现 404——IPFS 不支持服务端路由重写。*

**pinme 常用命令**

| 命令 | 说明 |
|------|------|
| `pinme upload <目录>` | 上传静态目录 |
| `pinme list` | 查看上传记录 |
| `pinme rm <hash>` | 删除已发布内容 |
| `pinme bind <目录> --domain <域名>` | 绑定自定义域名（需 VIP） |

## Skill 创建提示词

> Lesson5 包含两个 Skill 的创建提示词。

**pinme-deploy 创建提示词**（`pinme-prompt.md`，节选）：
```
创建 pinme-deploy skill，该 skill 利用 pinme 来实现静态页面发布功能。

Step 1: 检查环境 — 使用 `pinme -v` 判断是否已安装
Step 2: 构建并上传 — 执行构建命令（可选）+ pinme upload <静态目录>

框架构建目录：Vite→dist/；React CRA→build/；纯 HTML→根目录
路由注意：⚠️ 必须使用 hash 模式（React: HashRouter；Vue: createWebHashHistory）

请将 skill 保存到当前目录 .claude/skill 下
```

**product-prototype-design 创建提示词**（`prd-prompt.md`，节选）：
```
使用 skill-creator 创建产品原型设计 skill，用于快速生成产品原型

Step 1: 推断行业 — 根据用户背景信息推断行业，无法推断时主动询问
Step 2: 选择视觉设计规范 — 严格遵循行业视觉规范（配色/字体/圆角/动效）
  禁忌：严禁使用蓝色到紫色渐变（from-blue-500 to-purple-500）
Step 3: 创建原型 — HTML5 + TailwindCSS + Vanilla JS，单文件交付
Step 4: 网站部署 — 使用 pinme-deploy skill 完成原型页面部署
```

> *📌 两个 Skill 是**链式调用**设计：prototype-design 的第 4 步直接调用 pinme-deploy——这是课程演示的 Skill 复用模式，参赛时可以借鉴。*

## 示例输出（课程演示成果）

Lesson5 配套了完整演示成果，可直接查看参考：
- `积分兑换功能PRD.md`：用 prd Skill 生成的完整 PRD（含状态机/埋点/边界场景，9段结构）
- `积分兑换原型.html`：用 product-prototype-design 生成的可交互电商原型页面（电商行业规范）

## 行业设计规范参考（`references/industry-design-specs.md`）

> 完整规范文件覆盖 14 个行业，每个行业包含：Tailwind 色值、字体、圆角/阴影、动效、布局风格、Google Fonts 推荐。使用时按行业直接查表套用即可。

| 行业 | Tailwind 主色 | 字体 | 典型特征 |
|------|-------------|------|---------|
| 科技/互联网 | `blue-600` / `slate-800` | Inter | 负白空间、gap-8、hover:-translate-y-1 |
| 金融/银行 | `slate-900` / `emerald-800` | Playfair Display | 直角/小圆角、严谨对齐、无花哨动效 |
| 电商/零售 | `red-500` / `orange-500` | Poppins | 大圆角 rounded-2xl、CTA 悬浮、animate-pulse |
| 餐饮/美食 | `orange-500` / `amber-400` | Ma Shan Zheng | 有机形状、hover:scale-105、大图驱动 |
| 游戏/娱乐 | `violet-500` 霓虹色 | Orbitron | 强制深色、ring-1 ring-cyan-400、碎片化布局 |
| 医疗/健康 | `emerald-500` / `sky-500` | Lato | 极简、leading-relaxed、柔和阴影 |

> *📌 所有行业都禁止使用蓝紫渐变（`from-blue-* to-purple-*`）。游戏行业额外禁止渐变，必须用霓虹发光代替。*



## 在大赛中的位置

> *📌 这个 Skill 组合的竞争力很强：非开发者也能直接用，效果直观（可交互 HTML），还能一键获得可分享链接。参赛时「描述产品 → 生成原型 → 在线演示」的完整链路截图是非常好的展示素材。*

🐱 `product-prototype-design` 是「设计师」，`pinme-deploy` 是「快递员」——设计师做好作品，快递员把链接送到你手上，整个流程 10 分钟内完成。
