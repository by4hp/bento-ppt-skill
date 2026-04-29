# bento-ppt-skill

> 一个 [Claude Code](https://claude.com/claude-code) skill — 生成 **"Apple keynote × 现代 SaaS"** 风格的横向翻页 Bento Grid 网页 PPT(单 HTML 文件,离线可用)。

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Inspired by](https://img.shields.io/badge/inspired%20by-guizang--ppt--skill-purple.svg)](https://github.com/op7418/guizang-ppt-skill)

---

## 一句话定位

把每页 PPT 视作一个 **12×8 网格**,卡片用 `.b-NxM` 快捷类自由组合,生成单文件 HTML deck 给浏览器横向翻页演示。视觉基调可在 5 套精选主题之间切换,不允许自定义颜色 — 保护美学下限。

适合:**产品发布会 / SaaS 路演 / AI demo / 数据 dashboard / 功能矩阵展示型 PPT**。

---

## 安装

把本仓库 clone 到你的 Claude Code skills 目录(全局或项目本地皆可):

```bash
# 全局 skill(所有项目可用)
git clone <this-repo-url> ~/.claude/skills/bento-ppt-skill

# 或项目本地 skill
cd path/to/your/project
git clone <this-repo-url> .claude/skills/bento-ppt-skill
```

> `<this-repo-url>` 即本 repo 的 git URL — 在 GitHub 页面右上角"Code"按钮里复制。

重启 Claude Code,在新会话里说:

```
用 bento-ppt-skill 给我做一份 [主题] 的 PPT
```

或直接 `/bento-ppt-skill` 触发。

---

## 5 套主题色(选 1 套,不允许自定义)

| 主题 | 调性 | 适合 |
|---|---|---|
| 🌑 **Apple Dark**(默认) | Tile #272729 + Sky Link Blue + 零渐变 | 通用科技 / 不知道选啥 |
| ☀️ **Apple Light** | Parchment #f5f5f7 + Action Blue #0066cc | 消费品 / 浅色官网风 |
| 🌌 **Vision Aurora** | 深空蓝紫粉 mesh + 玻璃感(自创) | AI / 未来感 / 沉浸感 |
| ⬛ **Vercel Geist** | Vercel Black #171717 + Geist 字体 + 极紧 tracking | 开发者工具 / 克制科技 |
| 🌿 **Claude Warm** | Canvas 米白 + Coral #cc785c + 衬线标题 | AI 工具 / Anthropic 风 / editorial 温暖 |

> 4 套主题(除 Vision Aurora)的颜色全部精校自真实站点 design tokens · 数据来源 [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) · 命令 `npx getdesign@latest add <site>`。
> 完整原始 DESIGN.md 在 [`references/design-md/`](references/design-md/),含组件 / 阴影 / 排版完整规范。

完整 `:root` CSS 变量见 [references/themes.md](references/themes.md)。

---

## 8 种 Bento 布局

| # | Layout | 卡数 | 用途 |
|---|---|---|---|
| 1 | Single Focus | 1 hero | 开场 / 章节封 / 收尾 |
| 2 | 50/50 Symmetric | 2 | 双产品对比 |
| 3 | Asymmetric 8/4 | 2 | 主叙事 + 数据佐证 |
| 4 | 3-Column Equal | 3 | 三方案 / 三套餐 |
| 5 | Hero + 2 Side | 3 | 主产品 + 规格 + 价格 |
| 6 | **Top Hero + Grid** ★ | 4 | 章节标题 + 3 子卡 |
| 7 | **Mixed Free Grid** ★ | 5-7 | 数据 dashboard |
| 8 | Stat Showcase 2×2 | 4 | 4 个核心数字 |

完整骨架(粘贴即用)见 [references/layouts.md](references/layouts.md)。

---

## 网格系统

`.bento` 容器 = 12 列 × 8 行 grid,卡片用 `.b-NxM` 快捷类填充:

```html
<section class="slide">
  <div class="bento">
    <div class="b-card grad b-12x3"> ... </div>   <!-- 顶部 banner -->
    <div class="b-card b-4x5"> ... </div>          <!-- 三张特性卡 -->
    <div class="b-card b-4x5"> ... </div>
    <div class="b-card b-4x5"> ... </div>
  </div>
</section>
```

22 个尺寸快捷类:`.b-12x[8/5/4/3/2]` · `.b-8x[8/5/4/3]` · `.b-6x[8/5/4/3]` · `.b-4x[8/5/4/3/2]` · `.b-3x[8/4/3/2]`

不在快捷类里的尺寸用 inline `style="grid-column:span N;grid-row:span M"`。

---

## 卡片变体

| 变体类 | 视觉 |
|---|---|
| `.b-card`(默认) | 实底 + 细边 |
| `.b-card.glass` | 半透 + 模糊,让背景渐变透出 |
| `.b-card.elev` | 浮起阴影 |
| `.b-card.grad` | 卡内带微弱径向渐变 |
| `.b-card.img` | 内部图片占满 + 文字浮在底 |

---

## 致谢 · Inspired by

本 skill **架构和工程范式参考自开源项目** [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill)(作者:歸藏 Guizang)。直接复用了:

- 横向翻页系统(键盘 / 滚轮 / 触屏 / ESC 索引 / 圆点 nav)
- Motion One 动效系统(本地 + CDN 双保险加载)
- Skill 文件骨架(SKILL.md + assets + references)
- 类预检 + 主题节奏的工程理念
- 字体 + Lucide icon 的加载方式

**风格上完全重新设计**:guizang 是"电子杂志 × 电子墨水"(衬线大标题 + 墨水色 + WebGL 流体背景),本 skill 是"Apple keynote × 现代 SaaS"(全 sans + 5 套科技风主题 + CSS gradient mesh + 12×8 bento 网格)。两者各有定位,**不互相替代**:

| 选 guizang | 选 bento |
|---|---|
| 个人分享 / 私享会 / 行业观察 | 产品发布 / SaaS 路演 / AI demo |
| 文化向 / 杂志向 / 衬线美学 | 科技向 / dashboard / 现代感 |
| 单页大块文本为主 | 多卡片网格组合为主 |

---

## 文件结构

```
bento-ppt-skill/
├── SKILL.md              ← Claude Code 入口(7 问澄清 + Step 1-6 + 6 条哲学)
├── README.md             ← 本文件(GitHub 视角速览)
├── assets/
│   ├── template.html     ← 单文件种子(CSS gradient bg + bento grid + 翻页 JS + 3 示例 slide)
│   └── motion.min.js     ← Motion One 本地副本(64KB,离线兜底)
└── references/
    ├── themes.md         ← 5 套主题 :root 块
    ├── layouts.md        ← 8 个布局完整骨架 + Pre-flight + 决策树
    ├── components.md     ← 字体 / 网格 / 卡片 / 数字 / sticker / gradient / 动效手册
    └── checklist.md      ← P0-P3 质量清单 + 自检脚本
```

完整工作流和 7 问需求澄清,见 [SKILL.md](SKILL.md)。

---

## License

MIT(参考 guizang-ppt-skill 的开源精神)。

如果你觉得有用,⭐ 一下 + 给原作 [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) 也来一颗。

---

## Roadmap(已规划未实现)

- [ ] `.bt` bento-table 组件(商业用途多列对比表)
- [ ] L9 Table-Centric layout(表格主导的页面)
- [ ] 透明 PNG 产品图漂浮模式(iPhone 发布会风)
- [ ] 更多主题(Web3 霓虹 / 极简纸感 / Material You)

欢迎 Issue / PR 讨论。
