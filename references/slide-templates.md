# Slide 构建规则

## 设计 token 优先

所有风格变量集中在 `:root` 的 CSS 变量里，slide 内部只引用变量，不写死色值/字号。这样改一处即可全局换风格。

```css
:root {
  --color-primary: #1A1A2E;
  --color-accent:  #E94560;
  --color-bg:      #F5F5F5;
  --color-surface: #FFFFFF;
  --color-text:    #16213E;
  --color-muted:   #6B7280;

  --font-display: "Playfair Display", serif;
  --font-body:    "Inter", system-ui, sans-serif;

  --fs-title: clamp(2.5rem, 5vw, 4rem);
  --fs-h2:    clamp(1.5rem, 3vw, 2.25rem);
  --fs-body:  clamp(1rem, 1.6vw, 1.25rem);

  --space: 8px;
  --radius: 0px;
  --shadow: none;
}
```

## 结构约定

- 每页是一个 `.slide`，固定 16:9 宽高比，居中显示。
- 一次只显示一页（`.slide.active`），用键盘 `←/→` 或点击翻页。
- 页码指示器放右下角。
- 字体优先用 Google Fonts，`<link>` 放在 `<head>`。

## 页型模板

- **封面页**：大标题 + 副标题 + 作者/日期，常用满版背景色或强调色。
- **章节页**：大号章节序号 + 章节名，留白多。
- **要点页**：标题 + 3-5 条要点，要点可配小图标或序号。
- **图文页**：左右或上下分栏，一边图一边文字。
- **数据页**：大号数字 + 标签，突出强调色。
- **结尾页**：致谢/联系方式，呼应封面风格。

## 翻页脚本（最小实现）

```html
<script>
  const slides = [...document.querySelectorAll('.slide')];
  let i = 0;
  const show = n => {
    i = Math.max(0, Math.min(slides.length - 1, n));
    slides.forEach((s, idx) => s.classList.toggle('active', idx === i));
    document.querySelector('#page').textContent = `${i + 1} / ${slides.length}`;
  };
  addEventListener('keydown', e => {
    if (e.key === 'ArrowRight' || e.key === ' ') show(i + 1);
    if (e.key === 'ArrowLeft') show(i - 1);
  });
  addEventListener('click', () => show(i + 1));
  show(0);
</script>
```

## 质量要求

- 单文件可分享：CSS 内联，仅外链字体。
- 响应式：用 `clamp()` 让字号随视口缩放。
- 可打印：`@media print { .slide { page-break-after: always; } }`。
- 无障碍：文字对比度达标，图片带 `alt`，语义化标签。
- 风格忠实：配色、字体、间距、细节都要对得上参考，不要退化成通用模板。
