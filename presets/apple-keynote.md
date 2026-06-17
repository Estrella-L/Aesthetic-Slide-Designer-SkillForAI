---
name: apple-keynote
title: Apple Keynote 极简
keywords: [极简, 留白, 科技, 无衬线, 浅色, 蓝色强调]
source: 示例预设（Apple 发布会视觉气质，仅复刻审美方向，非官方素材）
created: 2026-06-17
---

# Style Spec

- 原型: 极简留白 + 企业专业
- 基调: 克制 / 高级 / 理性

## CSS 变量

```css
:root {
  --color-primary: #1D1D1F;
  --color-accent:  #0071E3;
  --color-bg:      #FFFFFF;
  --color-surface: #F5F5F7;
  --color-text:    #1D1D1F;
  --color-muted:   #6E6E73;

  --font-display: "SF Pro Display", -apple-system, "PingFang SC", sans-serif;
  --font-body:    "SF Pro Text", -apple-system, "PingFang SC", sans-serif;

  --fs-title: clamp(2.5rem, 5vw, 4.5rem);
  --fs-h2:    clamp(1.5rem, 3vw, 2.25rem);
  --fs-body:  clamp(1rem, 1.6vw, 1.25rem);

  --space: 8px;
  --radius: 18px;
  --shadow: 0 4px 24px rgba(0,0,0,0.06);
}
```

## 细节备注

- 图像: 满版高清产品图，留白居中构图
- 字体: 超大标题 + 细体正文，字距略宽
- 动效(网页): 克制淡入 + 轻视差
- 适合: 产品发布、科技主题、需要高级克制感的演示
