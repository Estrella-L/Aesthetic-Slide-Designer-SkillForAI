---
name: dark-game-studio
title: 暗色创意工作室 (Dark Creative Studio)
keywords: [暗色, 深蓝, 蓝紫强调, 粗体大写, 网格, 创意机构, 游戏]
source: 用户截图提取（深色 creative agency 视觉，用于独立游戏工作室官网）
created: 2026-06-17
---

# Style Spec

- 原型: 深色 creative agency + 大写粗体冲击
- 基调: 现代 / 张力 / 科技潮流

## CSS 变量

```css
:root {
  --bg:       #0c0d14;
  --bg-soft:  #12131d;
  --bg-card:  #171825;
  --accent:   #4d5bff;
  --accent-2: #6f7bff;
  --text:     #f2f3f8;
  --muted:    #8a8da3;
  --line:     rgba(255,255,255,.07);

  --font-display: "Segoe UI", -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif;
  --font-body:    "Segoe UI", -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif;

  --fs-title: clamp(44px, 8vw, 104px);
  --fs-h2:    clamp(30px, 5vw, 46px);
  --fs-body:  clamp(1rem, 1.6vw, 16px);

  --space: 8px;
  --radius: 10px;
  --shadow: 0 8px 30px rgba(0,0,0,.4);
}
```

## 细节备注

- 标题: 超大粗体、全大写、字距收紧 (-1px)；可用镂空描边字 (`-webkit-text-stroke`) 做强调
- 装饰: 蓝色 `+` 符号作区块前缀；Hero 背景用淡网格 + 径向渐变光晕
- 强调色: 蓝紫 (#4d5bff)，用于按钮、图标描边、镂空框、hover 边框
- 卡片: 深色卡 + 细描边，hover 上浮 6px 并点亮强调色边框
- 图标: 内联 SVG 细线风格 (stroke 1.8, fill none)
- 动效(网页): hover 上浮 / 颜色过渡 .25–.3s，克制不浮夸
- 圆角按钮: 40px 胶囊形，大写 + 字距 1.5px
- 适合: 独立游戏工作室、创意机构、科技潮牌、暗色作品集
