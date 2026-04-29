# Bento 布局库(Layouts)

8 种 Bento Grid 布局组合,每种都是完整可粘贴的 `<section class="slide">` 代码块,直接替换文案/图片即可。

---

## ⚠️ 生成前必读(Pre-flight)

### A. 类名必须来自 template.html

layouts.md 用到的类(`bento` / `b-card` / `b-card.glass|elev|grad|img` / `b-12x8` / `b-12x3` / `b-8x8` / `b-6x8` / `b-6x4` / `b-4x8` / `b-4x5` / `b-4x4` / `b-3x8` / `b-3x4` / `c-head` / `c-kick` / `c-title` / `c-foot` / `hero-num` / `stat-num` / `hu` / `kpi-row` / `kpi-l` / `kpi-v` / `feat-list` / `feat-item` / `dot` / `ft` / `icon-row` / `sticker` / `sticker.accent|flame|mint` / `kicker` / `lead` / `body` / `caption` / `meta-row` / `h-hero` / `h-hero-zh` / `h-xl` / `h-lg` / `h-md` / `h-sm` / `gtext` / `gtext-aurora|sky|flame|mint` / `frame-img` / `img-slot` / `chrome` / `foot`)**全部在 `assets/template.html` 的 `<style>` 块中已定义**。

**不要发明新类名**。如需自定义,用 `style="..."` inline 写。生成前若不确定,grep template.html 确认。

### B. Bento Grid 网格规范

每页 `.bento` 容器是 **12 列 × 8 行** 内部网格(`grid-template-columns:repeat(12,1fr);grid-template-rows:repeat(8,1fr)`),卡片用 `grid-column:span N` + `grid-row:span M` 填充,**总和必须 = 12×8 = 96 单元**(可以有空隙,但不能超)。

提供了快捷类:
| 快捷类 | grid-column / grid-row | 等于 |
|---|---|---|
| `.b-12x8` | span 12 / span 8 | 整页 |
| `.b-12x4` `.b-12x5` `.b-12x3` | span 12 / span N | 顶/底 banner |
| `.b-8x8` `.b-8x4` | span 8 / span N | 主卡 |
| `.b-6x8` `.b-6x4` `.b-6x5` | span 6 / span N | 半宽 |
| `.b-4x8` `.b-4x5` `.b-4x4` `.b-4x3` | span 4 / span N | 三分之一 |
| `.b-3x8` `.b-3x4` | span 3 / span N | 四分之一 |

**不在快捷类里的尺寸用 inline**:`<div class="b-card" style="grid-column:span 5;grid-row:span 4">`。

### C. 卡片密度节奏(本 skill 特殊规则)

guizang 强制 dark/light 主题交替,**本 skill 改成"卡片密度交替"**,因为 Apple keynote 通常一套主题贯穿:

- ✅ **推荐**:稠密页(4-7 卡)+ hero 页(1-3 卡)交替,3-4 张稠密插入 1 张 hero 喘息
- ❌ **禁止**:连续 5 页以上无 hero(节奏太密)
- ❌ **禁止**:连续 3 页以上单卡 hero(节奏太空)
- ✅ **首页用 Layout 1 单卡 hero**,**末页用 Layout 1 / 2 收尾**

主题色统一用同一个(见 `themes.md`),不强制切换。

### D. 图片处理(简单)

bento 卡里的图片用两种方式:
1. **占满整张卡**:用 `.b-card.img` 变体,内部 `<img class="img-fill">` 自动 `object-fit:cover`,文字用 `.img-overlay` 浮在底部
2. **作为卡内的部分内容**:用 `<figure class="frame-img">` + 内部 `<img>`,自动占满剩余空间

### E. 动效系统(默认 cascade)

- 不写 `data-animate` = `cascade`(每个 `[data-anim]` 元素逐个淡入,最适合 bento 多卡片)
- 单卡 hero 页(Layout 1):`data-animate="hero"`,节奏更慢更仪式感
- 大引用页:`data-animate="quote"`,逐行揭示
- 流水线 / 分步推进:`data-animate="pipeline"`(本 skill 较少用,bento 不适合分步推进)

---

## Layout 1 · Single Focus(单卡 hero)

**用途**:开场封面 / 章节幕封 / 单一有力金句 / 收尾页
**密度**:1 卡 · hero 页

```html
<section class="slide" data-theme="dark" data-animate="hero">
  <div class="chrome">
    <div>Bento Deck · 2026</div>
    <div>VOL.01</div>
  </div>
  <div class="bento">
    <div class="b-card glass b-12x8" style="justify-content:center" data-anim>
      <div class="sticker accent" data-anim>NEW · KEYNOTE</div>
      <div style="height:3vh"></div>
      <div class="kicker" data-anim>Bento Grid PPT</div>
      <h1 class="h-hero-zh" data-anim>把 PPT,<br>排成 <span class="gtext gtext-aurora">便当</span>。</h1>
      <div style="height:3vh"></div>
      <p class="lead" style="max-width:55vw" data-anim>
        卡片为最小单元,12 × 8 网格自由组合。Apple keynote / SaaS 路演 / AI demo 通用。
      </p>
      <div style="height:3vh"></div>
      <div class="meta-row" data-anim>
        <span>SUBTITLE OR PRESENTER</span><span>·</span><span>2026.04</span>
      </div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 1 · Single Focus</div>
    <div>— · —</div>
  </div>
</section>
```

**要点**:
- 用 `.b-card.glass` 让 mesh gradient 透出
- `style="justify-content:center"` 让内容垂直居中
- gradient text 只在 1-2 个关键词上,不要整段都 gradient
- sticker 在最顶可作"标签"(NEW / DEMO / VOL.01 等)

---

## Layout 2 · 50/50 Symmetric(对称双卡)

**用途**:产品并列 / 旧 vs 新对比 / 两个核心特性
**密度**:2 卡

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>双产品对比 · Compare</div>
    <div>02 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card grad b-6x8" data-anim>
      <div class="sticker accent">PRODUCT A</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-kick">DESKTOP · MAC</div>
        <div class="c-title">MacBook Pro M5</div>
      </div>
      <p class="body">14 寸 · 18 小时电池 · 神经网络引擎升级 40%。专业创作者的全速工作台。</p>
      <figure class="frame-img" style="margin-top:auto" data-anim>
        <img src="images/macbook.jpg" alt="MacBook Pro">
      </figure>
      <div class="c-foot">FROM ¥14,999</div>
    </div>
    <div class="b-card grad b-6x8" data-anim>
      <div class="sticker flame">PRODUCT B</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-kick">MOBILE · iPHONE</div>
        <div class="c-title">iPhone 17 Pro</div>
      </div>
      <p class="body">A19 仿生 · 2x 长焦 · ProRes 视频。一台口袋里的电影摄影机。</p>
      <figure class="frame-img" style="margin-top:auto" data-anim>
        <img src="images/iphone.jpg" alt="iPhone 17 Pro">
      </figure>
      <div class="c-foot">FROM ¥7,999</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 2 · 50/50 Symmetric</div>
    <div>— 02 / 12 —</div>
  </div>
</section>
```

**要点**:
- 两卡用相同变体(都 `.grad` 或都默认),保证视觉对称
- 用不同 `.sticker` 颜色(accent vs flame)制造区分
- `figure.frame-img` 配 `margin-top:auto` 让图自动贴到卡底

---

## Layout 3 · Asymmetric 8/4(主辅卡)

**用途**:1 个主内容 + 1 个数据/小图佐证
**密度**:2 卡

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>核心叙事 + 关键数字</div>
    <div>03 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card glass b-8x8" data-anim>
      <div class="sticker accent">KEY MESSAGE</div>
      <div class="c-head" style="margin-top:2vh">
        <div class="c-kick">THE STORY</div>
      </div>
      <h2 class="h-xl" style="margin-top:1vh">
        AI 让一个人的<br><span class="gtext gtext-aurora">产能</span>,
        变成一个公司的体量。
      </h2>
      <p class="lead" style="margin-top:3vh; max-width:38vw">
        过去十年,SaaS 让 5 人公司拥有 50 人的销售能力。
        过去 1 年,AI 让 1 人公司拥有 10 人的开发能力。
      </p>
      <div class="c-foot">— Garry Tan, YC President · 2026</div>
    </div>
    <div class="b-card grad b-4x8" data-anim>
      <div class="sticker mint">PROOF</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">实证</div>
      </div>
      <div class="kpi-row">
        <div class="kpi-l">独立开发者</div>
        <div class="kpi-v">11<span class="hu" style="font-size:.5em;color:var(--text-2)">万行代码</span></div>
      </div>
      <div class="kpi-row">
        <div class="kpi-l">交付时间</div>
        <div class="kpi-v">64<span class="hu" style="font-size:.5em;color:var(--text-2)">天</span></div>
      </div>
      <div class="kpi-row">
        <div class="kpi-l">GitHub Stars</div>
        <div class="kpi-v">5,166</div>
      </div>
      <div class="kpi-row">
        <div class="kpi-l">下载量</div>
        <div class="kpi-v">41K+</div>
      </div>
      <div class="c-foot">CodePilot · 2026.04</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 3 · Asymmetric 8/4</div>
    <div>— 03 / 12 —</div>
  </div>
</section>
```

**要点**:
- 8 列主卡承载叙事 + 大标题,4 列辅卡承载 KPI 列表
- 主卡用 glass 让背景透出,辅卡用 grad 增加视觉重量

---

## Layout 4 · 3-Column Equal(三方案并列)

**用途**:3 个套餐 / 3 个特性 / 3 个核心理念
**密度**:3 卡

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>三套版本 · Plans</div>
    <div>04 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card b-4x8" data-anim>
      <div class="sticker">FREE</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">Hobby</div>
      </div>
      <div class="hero-num" style="font-size:5vw">
        $0<span class="hu" style="font-size:.4em">/mo</span>
      </div>
      <ul class="feat-list" style="margin-top:3vh">
        <li class="feat-item"><span class="dot"></span><span class="ft">100 次 / 月</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">基础模型</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">社区支持</span></li>
      </ul>
      <div class="c-foot">START FREE</div>
    </div>
    <div class="b-card grad b-4x8" data-anim>
      <div class="sticker accent">RECOMMENDED</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">Pro</div>
      </div>
      <div class="hero-num gtext gtext-sky" style="font-size:5vw">
        $20<span class="hu" style="font-size:.4em;-webkit-text-fill-color:var(--text-2);background:none">/mo</span>
      </div>
      <ul class="feat-list" style="margin-top:3vh">
        <li class="feat-item"><span class="dot"></span><span class="ft">无限次调用</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">最新模型 + 优先队列</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">邮件支持 24h</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">API 访问</span></li>
      </ul>
      <div class="c-foot">MOST POPULAR</div>
    </div>
    <div class="b-card b-4x8" data-anim>
      <div class="sticker flame">TEAMS</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">Enterprise</div>
      </div>
      <div class="hero-num" style="font-size:5vw">
        Custom
      </div>
      <ul class="feat-list" style="margin-top:3vh">
        <li class="feat-item"><span class="dot"></span><span class="ft">SSO + SCIM</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">私有部署</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">SLA 99.9%</span></li>
        <li class="feat-item"><span class="dot"></span><span class="ft">专属客户成功经理</span></li>
      </ul>
      <div class="c-foot">CONTACT SALES</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 4 · 3-Column Equal</div>
    <div>— 04 / 12 —</div>
  </div>
</section>
```

**要点**:
- 中间卡用 `.grad` + accent sticker 强调"推荐版本"
- gradient text 只用在中间卡的价格上,凸显焦点

---

## Layout 5 · Hero + 2 Side(主次结合)

**用途**:1 个主产品 + 2 个补充信息(规格/价格/特性)
**密度**:3 卡

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>主推产品 · 关键参数</div>
    <div>05 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card img b-6x8" data-anim>
      <img class="img-fill" src="images/airpods.jpg" alt="AirPods Pro 3">
      <div class="img-overlay">
        <div class="sticker accent" style="margin-bottom:1.4vh">FLAGSHIP</div>
        <h2 class="h-lg">AirPods Pro 3</h2>
        <p class="body" style="margin-top:1vh">主动降噪 + 心率监测 + 实时翻译。</p>
      </div>
    </div>
    <div class="b-card grad b-3x8" data-anim>
      <div class="sticker mint">SPECS</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">关键参数</div>
      </div>
      <div class="kpi-row"><div class="kpi-l">续航</div><div class="kpi-v">8h</div></div>
      <div class="kpi-row"><div class="kpi-l">充电盒</div><div class="kpi-v">36h</div></div>
      <div class="kpi-row"><div class="kpi-l">重量</div><div class="kpi-v">5.3g</div></div>
      <div class="kpi-row"><div class="kpi-l">芯片</div><div class="kpi-v">H3</div></div>
    </div>
    <div class="b-card b-3x8" data-anim>
      <div class="sticker flame">PRICE</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">价格 · 上市</div>
      </div>
      <div class="hero-num gtext gtext-flame" style="margin-top:auto">
        ¥1,899
      </div>
      <div class="c-foot">2026.05.10 上市</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 5 · Hero + 2 Side</div>
    <div>— 05 / 12 —</div>
  </div>
</section>
```

**要点**:
- 主卡用 `.b-card.img` 让产品图占满,`.img-overlay` 浮在底部
- 右侧两张窄卡(3 列宽 × 8 行高)分别承载规格 + 价格

---

## Layout 6 · Top Hero + Grid(顶 banner + 3 卡)

**用途**:章节标题 + 3 个分支特性 / 3 个核心理由 / 3 个步骤
**密度**:4 卡(本 skill 主推之一)

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>三个核心理由 · Why</div>
    <div>06 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card grad b-12x3" data-anim>
      <div class="kicker">THE PITCH</div>
      <h2 class="h-xl" style="margin-top:1vh">
        为什么是 <span class="gtext gtext-sky">Bento</span>?
      </h2>
      <p class="lead" style="margin-top:1.4vh; max-width:62vw">
        不是单页大块文本,不是僵硬的"标题 + 三栏",而是按内容驱动的卡片网格。
      </p>
    </div>
    <div class="b-card b-4x5" data-anim>
      <div class="sticker mint">01 · FLEX</div>
      <div class="c-head" style="margin-top:2vh">
        <div class="c-title">灵活</div>
      </div>
      <p class="body">
        卡片数量取决于内容如何更好地呈现,1, 2, 3, 4, 5 张都可以。
      </p>
      <div class="c-foot">FLEXIBILITY</div>
    </div>
    <div class="b-card b-4x5" data-anim>
      <div class="sticker accent">02 · SCALE</div>
      <div class="c-head" style="margin-top:2vh">
        <div class="c-title">层级</div>
      </div>
      <p class="body">
        最重要的信息放最大的卡上,次要的散在周边。视觉一眼分主次。
      </p>
      <div class="c-foot">HIERARCHY</div>
    </div>
    <div class="b-card b-4x5" data-anim>
      <div class="sticker flame">03 · SPACE</div>
      <div class="c-head" style="margin-top:2vh">
        <div class="c-title">留白</div>
      </div>
      <p class="body">
        卡间至少 20px 间距,卡内 ≥ 24px padding。呼吸感是 bento 的灵魂。
      </p>
      <div class="c-foot">BREATHING</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 6 · Top Hero + Grid</div>
    <div>— 06 / 12 —</div>
  </div>
</section>
```

**要点**:
- 顶部 12×3 banner 占据 3 行高,留 5 行给下方 3 张卡
- 3 张子卡用三种 sticker 颜色(mint / accent / flame)区分
- 这是本 skill 最常用的"章节型"布局

---

## Layout 7 · Mixed Free Grid(自由混合)

**用途**:数据 dashboard / 信息密集页 / 多维度同屏展示
**密度**:5-7 卡(本 skill 主推之一)

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>数据全景 · Dashboard</div>
    <div>07 / 12</div>
  </div>
  <div class="bento">
    <!-- 左上:大数据卡 6×4 -->
    <div class="b-card grad b-6x4" data-anim>
      <div class="sticker accent">REVENUE</div>
      <div class="c-head" style="margin-top:1vh">
        <div class="c-title">营收</div>
      </div>
      <div class="hero-num gtext gtext-sky" style="font-size:6vw">
        30.3<span class="hu" style="-webkit-text-fill-color:var(--text-2);background:none">亿元</span>
      </div>
      <div class="c-foot">2025 · 同比 +2.4%</div>
    </div>
    <!-- 右上:KPI 卡 6×4 -->
    <div class="b-card b-6x4" data-anim>
      <div class="sticker">METRICS</div>
      <div class="c-head" style="margin-top:1vh">
        <div class="c-title">关键指标</div>
      </div>
      <div class="kpi-row"><div class="kpi-l">毛利率</div><div class="kpi-v">33.5%</div></div>
      <div class="kpi-row"><div class="kpi-l">净利率</div><div class="kpi-v">3.39%</div></div>
      <div class="kpi-row"><div class="kpi-l">ROE</div><div class="kpi-v">3.37%</div></div>
    </div>
    <!-- 中:全宽 banner 12×2 -->
    <div class="b-card glass b-12x2" data-anim>
      <div class="icon-row" style="font-size:max(15px,1.2vw)">
        <span class="sticker mint" style="margin-right:1em">INSIGHT</span>
        <span>2025 增收不增利 · 汇兑损益 + 拓展投入 + 应收账款共同挤压利润</span>
      </div>
    </div>
    <!-- 底排 4 张 stat 小卡 3×2 -->
    <div class="b-card b-3x2" data-anim>
      <div class="caption">PATENTS</div>
      <div class="stat-num" style="font-size:3vw">981</div>
    </div>
    <div class="b-card b-3x2" data-anim>
      <div class="caption">DATA · 万份</div>
      <div class="stat-num gtext gtext-mint" style="font-size:3vw">890</div>
    </div>
    <div class="b-card b-3x2" data-anim>
      <div class="caption">BCG · 亿份</div>
      <div class="stat-num" style="font-size:3vw">4</div>
    </div>
    <div class="b-card b-3x2" data-anim>
      <div class="caption">REPORTS · 万</div>
      <div class="stat-num gtext gtext-flame" style="font-size:3vw">1000+</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 7 · Mixed Free Grid</div>
    <div>— 07 / 12 —</div>
  </div>
</section>
```

**要点**:
- 总共 7 卡:6×4 + 6×4 + 12×2 + 4×(3×2)= 24 + 24 + 24 + 24 = 96 单元 ✅
- 中间 12×2 全宽 banner 适合放一句洞察 / 总结句
- 底排 4 张窄卡用更小的 caption + 简化 stat,密度感强
- `.b-3x2` 不在快捷类里,用 inline:`<div class="b-card" style="grid-column:span 3;grid-row:span 2">`(注:已在 template.html 中定义为快捷类,可直接用)

**网格计算助记**:
```
┌──────────┬──────────┐  6×4 + 6×4
│ 6×4 stat │ 6×4 KPI  │
├──────────┴──────────┤  12×2 banner
│   12×2 insight     │
├──────┬──────┬──────┬──────┤  4×(3×2)
│ 3×2  │ 3×2  │ 3×2  │ 3×2  │
└──────┴──────┴──────┴──────┘
```

---

## Layout 8 · Stat Showcase 2×2(4 大数字)

**用途**:4 个核心 KPI / 4 个关键里程碑 / 4 个产品参数
**密度**:4 卡(数字驱动)

```html
<section class="slide" data-theme="dark">
  <div class="chrome">
    <div>核心数字 · Numbers</div>
    <div>08 / 12</div>
  </div>
  <div class="bento">
    <div class="b-card grad b-6x4" data-anim>
      <div class="sticker accent">REVENUE</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">营收</div>
      </div>
      <div class="hero-num gtext gtext-sky">
        30.3<span class="hu" style="-webkit-text-fill-color:var(--text-2);background:none">亿元</span>
      </div>
      <div class="c-foot">2025 · 同比 +2.4%</div>
    </div>
    <div class="b-card b-6x4" data-anim>
      <div class="sticker">NET PROFIT</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">归母净利</div>
      </div>
      <div class="hero-num">
        1.05<span class="hu">亿元</span>
      </div>
      <div class="c-foot" style="color:var(--accent-3)">2025 · 同比 -32.8%</div>
    </div>
    <div class="b-card b-6x4" data-anim>
      <div class="sticker mint">PATENTS</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">累计专利</div>
      </div>
      <div class="hero-num gtext gtext-mint">
        981<span class="hu" style="-webkit-text-fill-color:var(--text-2);background:none">项</span>
      </div>
      <div class="c-foot">含发明专利 200+ 项</div>
    </div>
    <div class="b-card grad b-6x4" data-anim>
      <div class="sticker flame">DATA</div>
      <div class="c-head" style="margin-top:1.4vh">
        <div class="c-title">睡眠数据样本</div>
      </div>
      <div class="hero-num gtext gtext-flame">
        890<span class="hu" style="-webkit-text-fill-color:var(--text-2);background:none">万份</span>
      </div>
      <div class="c-foot">+ 4 亿份 BCG 心冲击图</div>
    </div>
  </div>
  <div class="foot">
    <div>Layout 8 · Stat Showcase 2×2</div>
    <div>— 08 / 12 —</div>
  </div>
</section>
```

**要点**:
- 4 张等大卡(`6×4`),sticker 颜色形成"四角呼应"
- 数字大小 = `hero-num`(默认 8vw)
- 每张卡的 `gtext` 渐变方向不同(sky / 无 / mint / flame)制造彩色角点
- 负向数据(同比下降)用 `style="color:var(--accent-3)"` 标红,正向用 `var(--accent-4)` 标绿(本例中只标红)

---

## Layout 决策树

```
内容是什么?
├─ 开场 / 章节封 / 收尾金句   → Layout 1 (Single Focus)
├─ 双产品 / 旧 vs 新对比     → Layout 2 (50/50)
├─ 1 个核心叙事 + KPI 佐证   → Layout 3 (8/4)
├─ 3 个套餐 / 3 个特性      → Layout 4 (3-Column)
├─ 1 主产品 + 规格 + 价格    → Layout 5 (Hero + 2 Side)
├─ 章节标题 + 3 子点        → Layout 6 (Top Hero + Grid)  ★ 本 skill 主推
├─ 5-7 个维度的 dashboard   → Layout 7 (Mixed Free)      ★ 本 skill 主推
└─ 4 个 KPI / 4 个里程碑    → Layout 8 (Stat Showcase 2×2)
```

---

## 完整 Deck 节奏建议(20 页参考)

| 页 | Layout | 密度 | 说明 |
|---|---|---|---|
| 1 | L1 Single Focus | hero | 开场 |
| 2 | L6 Top Hero + Grid | 4 卡 | 三个理由 |
| 3 | L7 Mixed Free | 7 卡 | 数据 dashboard |
| 4 | L1 Single Focus | hero | 章节幕封"产品" |
| 5 | L5 Hero + 2 Side | 3 卡 | 主产品介绍 |
| 6 | L8 Stat Showcase | 4 卡 | 关键数字 |
| 7 | L4 3-Column | 3 卡 | 三个套餐 |
| 8 | L1 Single Focus | hero | 章节幕封"技术" |
| 9 | L7 Mixed Free | 6 卡 | 技术架构 dashboard |
| 10 | L3 Asymmetric 8/4 | 2 卡 | 核心叙事 + 数据 |
| 11 | L2 50/50 | 2 卡 | 旧 vs 新 |
| 12 | L1 Single Focus | hero | 章节幕封"市场" |
| 13 | L8 Stat Showcase | 4 卡 | 市场数据 |
| 14 | L6 Top Hero + Grid | 4 卡 | 三个客户案例 |
| 15 | L1 Single Focus | hero | 章节幕封"未来" |
| 16 | L4 3-Column | 3 卡 | 路线图 Q1/Q2/Q3 |
| 17 | L7 Mixed Free | 5 卡 | 团队 + 融资 + 进度 |
| 18 | L3 Asymmetric 8/4 | 2 卡 | 愿景宣言 + 关键数字 |
| 19 | L1 Single Focus | hero | 大问题 / Call to Action |
| 20 | L1 Single Focus | hero | "谢谢" / 联系方式 |

每 3-5 页插入 1 个 hero 喘息,稠密页(4-7 卡)+ hero 页比例约 2:1。
