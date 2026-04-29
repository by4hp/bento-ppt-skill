# 主题色预设(Themes)

5 套精心调配的主题色板,覆盖 **Apple keynote × 现代 SaaS** 美学谱系。**不允许用户自定义颜色** — 色彩搭配错了画面瞬间垮,5 套预设保护美学下限。

---

## 使用方法

1. 基于内容主题推荐一套,或直接问用户选哪一套
2. 打开 `assets/template.html` 的 `<style>` 块,找到开头 `:root{` 块
3. **整体替换**标有"主题"注释的 `--bg-base` / `--card` / `--text` / `--accent-*` / `--gtext-*` 这一组变量
4. 其他 CSS 都走 `var(--...)`,无需任何其他改动

---

## 1. 🌑 Apple Dark(默认)

**适合**:科技产品发布、AI demo、企业级 keynote、不知道选啥的安全默认。
**调性**:纯黑主底 + 系统灰阶卡片 + 蓝紫粉品牌渐变。iOS 18 / macOS Sequoia 风。

```css
:root{
  --bg-base:#000000;
  --bg-elev:#0a0a0c;
  --card:#141417;
  --card-elev:#1c1c20;
  --card-border:rgba(255,255,255,0.08);
  --card-glow:rgba(255,255,255,0.04);
  --text:#f5f5f7;
  --text-2:rgba(245,245,247,0.7);
  --text-3:rgba(245,245,247,0.45);

  --accent-1:#0a84ff;
  --accent-2:#bf5af2;
  --accent-3:#ff375f;
  --accent-4:#30d158;

  --gtext-aurora:linear-gradient(135deg,#0a84ff 0%,#bf5af2 50%,#ff375f 100%);
  --gtext-sky:linear-gradient(135deg,#64d2ff 0%,#0a84ff 100%);
  --gtext-flame:linear-gradient(135deg,#ff9f0a 0%,#ff375f 100%);
  --gtext-mint:linear-gradient(135deg,#30d158 0%,#64d2ff 100%);
}
```

**默认 slide 主题标记**:`<section class="slide" data-theme="dark">`(全 dark 主题)

---

## 2. ☀️ Apple Light

**适合**:产品官网型展示、消费品发布、面向中文受众的"明亮路演"。
**调性**:Apple.com 浅灰主底 + 白卡片 + 黑色文字 + 蓝色 accent。柔和、官方、安全。

```css
:root{
  --bg-base:#f5f5f7;
  --bg-elev:#ffffff;
  --card:#ffffff;
  --card-elev:#fbfbfd;
  --card-border:rgba(0,0,0,0.06);
  --card-glow:rgba(0,0,0,0.02);
  --text:#1d1d1f;
  --text-2:rgba(29,29,31,0.7);
  --text-3:rgba(29,29,31,0.45);

  --accent-1:#0066cc;
  --accent-2:#5e5ce6;
  --accent-3:#ff2d55;
  --accent-4:#34c759;

  --gtext-aurora:linear-gradient(135deg,#0066cc 0%,#5e5ce6 50%,#ff2d55 100%);
  --gtext-sky:linear-gradient(135deg,#5ac8fa 0%,#0066cc 100%);
  --gtext-flame:linear-gradient(135deg,#ff9500 0%,#ff2d55 100%);
  --gtext-mint:linear-gradient(135deg,#34c759 0%,#5ac8fa 100%);
}
```

**默认 slide 主题标记**:`<section class="slide" data-theme="light">`(全 light 主题)

---

## 3. 🌌 Vision Aurora

**适合**:Vision Pro 类沉浸式发布、AI 大模型发布、未来感强的 demo。
**调性**:深空蓝主底 + 紫粉 mesh + 高玻璃感卡片。模仿 Vision Pro keynote 那种"宇宙感"。

```css
:root{
  --bg-base:#05071a;
  --bg-elev:#0a0e2a;
  --card:#101535;
  --card-elev:#161c42;
  --card-border:rgba(180,160,255,0.12);
  --card-glow:rgba(180,160,255,0.08);
  --text:#f0eeff;
  --text-2:rgba(240,238,255,0.72);
  --text-3:rgba(240,238,255,0.45);

  --accent-1:#7b9eff;
  --accent-2:#c084fc;
  --accent-3:#f472b6;
  --accent-4:#22d3ee;

  --gtext-aurora:linear-gradient(135deg,#22d3ee 0%,#7b9eff 35%,#c084fc 70%,#f472b6 100%);
  --gtext-sky:linear-gradient(135deg,#22d3ee 0%,#7b9eff 100%);
  --gtext-flame:linear-gradient(135deg,#f472b6 0%,#c084fc 100%);
  --gtext-mint:linear-gradient(135deg,#22d3ee 0%,#7b9eff 100%);
}
```

**默认 slide 主题标记**:`data-theme="dark"`(永远 dark,Light 版没意义)

**配套微调**:此主题下 `.bg-blob` 的 opacity 可拉到 0.65 加强宇宙感。

---

## 4. ⬛ Vercel Mono(克制科技)

**适合**:开发者工具发布、SaaS 路演、Linear / Vercel / Resend 风格。
**调性**:纯黑 + 纯白文字 + 极细灰边 + 几乎无渐变。克制、工程师审美。

```css
:root{
  --bg-base:#000000;
  --bg-elev:#000000;
  --card:#0a0a0a;
  --card-elev:#111111;
  --card-border:rgba(255,255,255,0.1);
  --card-glow:rgba(255,255,255,0.02);
  --text:#ffffff;
  --text-2:rgba(255,255,255,0.65);
  --text-3:rgba(255,255,255,0.4);

  --accent-1:#ffffff;
  --accent-2:#a1a1a1;
  --accent-3:#fafafa;
  --accent-4:#737373;

  --gtext-aurora:linear-gradient(135deg,#ffffff 0%,#a1a1a1 100%);
  --gtext-sky:linear-gradient(135deg,#ffffff 0%,#737373 100%);
  --gtext-flame:linear-gradient(135deg,#fafafa 0%,#525252 100%);
  --gtext-mint:linear-gradient(135deg,#ffffff 0%,#a3a3a3 100%);
}
```

**默认 slide 主题标记**:`data-theme="dark"`

**配套微调**:本主题下应**关闭 `.bg-blob` 动画**(把 opacity 设为 0)— Vercel 风不需要色彩漂浮:
```css
.bg-blob{display:none}
```

---

## 5. 🌿 OpenAI Warm

**适合**:AI 产品发布(ChatGPT 调性)、教育 / 研究内容、需要"现代但有温度"的 deck。
**调性**:米白主底 + 翠绿 accent + 橙红点缀。OpenAI 品牌页风。

```css
:root{
  --bg-base:#faf9f6;
  --bg-elev:#ffffff;
  --card:#ffffff;
  --card-elev:#f5f3ee;
  --card-border:rgba(40,30,20,0.08);
  --card-glow:rgba(40,30,20,0.02);
  --text:#1a1a1a;
  --text-2:rgba(26,26,26,0.7);
  --text-3:rgba(26,26,26,0.45);

  --accent-1:#10a37f;
  --accent-2:#7c3aed;
  --accent-3:#ea580c;
  --accent-4:#0ea5e9;

  --gtext-aurora:linear-gradient(135deg,#10a37f 0%,#0ea5e9 50%,#7c3aed 100%);
  --gtext-sky:linear-gradient(135deg,#0ea5e9 0%,#10a37f 100%);
  --gtext-flame:linear-gradient(135deg,#f59e0b 0%,#ea580c 100%);
  --gtext-mint:linear-gradient(135deg,#10a37f 0%,#84cc16 100%);
}
```

**默认 slide 主题标记**:`data-theme="light"`

---

## 推荐选择参考

| 如果是... | 推荐主题 |
|---|---|
| 不知道选啥 / 第一次用 | 🌑 Apple Dark |
| 消费品 / 浅色官网风 | ☀️ Apple Light |
| AI 大模型 / 未来感 / 沉浸 | 🌌 Vision Aurora |
| 开发者工具 / SaaS / 克制科技 | ⬛ Vercel Mono |
| AI 工具 / 研究内容 / 温暖科技 | 🌿 OpenAI Warm |

---

## 主题切换硬规则

- ✅ **一份 deck 只用一套主题**,不要中途换色
- ✅ **`data-theme` 与主题搭配**:Apple Dark / Vision Aurora / Vercel Mono = `data-theme="dark"`;Apple Light / OpenAI Warm = `data-theme="light"`
- ❌ **禁止混搭**(例如 bg 取 Apple Dark,accent 取 OpenAI Warm)— 会彻底违和
- ❌ **禁止用户给任意 hex 值** — 委婉拒绝并展示 5 套让选
- ❌ **不要直接修改 template.html 其他地方的颜色** — 所有散落颜色都走 var(),改 :root 一处即可

---

## 主题节奏(本 skill 特殊规则)

guizang 强制 light/dark 交替,但**本 skill 不要求**。Bento PPT(Apple keynote)通常**全程统一一种主题**(全 dark 或全 light),靠**卡片密度 + hero 页**制造节奏,而不是靠主题色切换:

- ✅ 推荐:整个 deck 用同一个 `data-theme`,卡片密度交替(单卡 hero ↔ 4-7 卡稠密)
- ⚠️ 可选:个别 hero 页用相反主题作"反差"(例如全 dark deck 中插入 1 页 light 大引用),但全 deck 不超过 2 页

详细的密度节奏规则见 `layouts.md` 的"密度节奏规划"。
