# 预设文件格式 (Preset Format)

每个被保存的风格存为 `presets/<kebab-name>.md`，结构固定如下，方便下次直接读取并套用。

## 文件模板

```markdown
---
name: apple-keynote
title: Apple Keynote 极简
keywords: [极简, 留白, 科技, 无衬线, 浅色]
source: 来源参考的简述（图片/网址/品牌）
created: 2026-06-17
---

# Style Spec

- 原型: 极简留白 + 企业专业
- 基调: 克制 / 高级 / 理性

## CSS 变量

\`\`\`css
:root {
  --color-primary: #1D1D1F;
  --color-accent:  #0071E3;
  --color-bg:      #FFFFFF;
  --color-surface: #F5F5F7;
  --color-text:    #1D1D1F;
  --color-muted:   #6E6E73;

  --font-display: "SF Pro Display", -apple-system, sans-serif;
  --font-body:    "SF Pro Text", -apple-system, sans-serif;

  --fs-title: clamp(2.5rem, 5vw, 4.5rem);
  --fs-h2:    clamp(1.5rem, 3vw, 2.25rem);
  --fs-body:  clamp(1rem, 1.6vw, 1.25rem);

  --space: 8px;
  --radius: 18px;
  --shadow: 0 4px 24px rgba(0,0,0,0.06);
}
\`\`\`

## 细节备注

- 图像: 满版高清产品图, 留白居中构图
- 字体: 超大标题 + 细体正文, 字距略宽
- 动效(网页): 克制淡入 + 视差
```

## 规则

- frontmatter 的 `name` 必须和文件名一致（kebab-case）。
- `keywords` 用于匹配用户的口头描述，尽量覆盖配色、字体、基调、原型。
- CSS 变量块要能直接粘进 `assets/slide-template.html` 的 `:root` 使用。
- 一个预设 = 一个文件，保持单一职责，便于增删改。
