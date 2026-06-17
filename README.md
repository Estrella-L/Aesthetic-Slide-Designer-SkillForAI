# Aesthetic Slide Designer

一个 Agent Skill：给它一张图片或一个网页，它会提取其中的**审美风格**（配色、字体、间距、情绪、细节），并据此生成一套风格统一的 HTML 幻灯片。提取过的风格还能命名保存，下次直接复用。

---

## 它能做什么

- 📸 **看图配风格**：丢一张设计稿/海报/UI 截图，复刻它的视觉气质。
- 🌐 **参照网页**：给一个 URL 或本地 HTML，提取该站点的审美。
- 🎞️ **生成 slide**：输出单文件 HTML 演示（16:9、键盘翻页、可打印、响应式）。
- 💾 **沉淀复用**：每次提取的风格存进 `presets/`，下次一句话即可调用。

---

## 安装

这个 skill 的 `SKILL.md` 格式与 Anthropic Agent Skills 通用，整个文件夹可直接搬运。

| 环境 | 放置位置 |
|------|----------|
| **Kiro** | `.kiro/skills/aesthetic-slide-designer/`（当前所在） |
| **Claude Code（全局）** | `~/.claude/skills/aesthetic-slide-designer/` |
| **Claude Code（项目）** | `<项目>/.claude/skills/aesthetic-slide-designer/` |
| **Claude.ai / 桌面端** | 先开启 Code execution，再把文件夹打包成 ZIP（根目录是 `SKILL.md`），在 Customize → Skills 上传并启用 |

> 放好后无需重启即被识别（Claude.ai 需上传 ZIP）。

**从本仓库快速安装到 Claude Code：**
```bash
git clone https://github.com/Estrella-L/Aesthetic-Slide-Designer-SkillForAI.git ~/.claude/skills/aesthetic-slide-designer
```

---

## 怎么用

直接在对话里描述需求并附上参考即可，无需手动点开 skill——agent 会根据 `SKILL.md` 的描述自动触发。

### 提取新风格 + 生成
```
[附一张图片]  按这张图的风格，帮我做 5 页关于「产品发布」的 slide
```
```
参照 https://example.com 的审美，做一套 4 页公司介绍 slide
```

### 复用已存风格
```
用 apple-keynote 风格做 6 页季度汇报
```
agent 会直接读取 `presets/apple-keynote.md`，跳过重新提取。

### 查看 / 管理已存风格
- 所有预设登记在 `presets/index.md`。
- 每个风格是 `presets/<name>.md`，含 Style Spec 与可直接套用的 CSS 变量。

---

## 工作流程（6 步）

agent 内部按这个顺序执行：

0. **查预设** — 先看 `presets/` 有没有现成可用的风格。
1. **采集参考** — 读图片或抓取网页。
2. **提取风格** — 按 `references/style-extraction.md` 整理出 Style Spec。
3. **确认内容** — 明确页数、每页要点。
4. **生成 slide** — 以 `assets/slide-template.html` 为骨架填入 token。
5. **自检** — 校验风格忠实度、翻页、对比度、打印。
6. **沉淀预设** — 新风格存进 `presets/` 并登记索引。

---

## 目录结构

仓库根目录即 skill 本体（`SKILL.md` 在根）：

```
.
├── SKILL.md                      # 入口：触发描述 + 主流程（agent 自动读）
├── README.md                     # 本文档（给人看）
├── references/
│   ├── style-extraction.md       # 风格提取清单 + 风格原型库
│   ├── slide-templates.md        # slide 构建规则与翻页脚本
│   └── preset-format.md          # 预设文件的标准格式
├── assets/
│   └── slide-template.html       # 可直接预览/复刻的 slide 骨架
└── presets/                      # 风格资产库（越用越多）
    ├── index.md                  # 预设索引表
    └── apple-keynote.md          # 示例预设
```

---

## 生成的 slide 怎么用

- 用浏览器打开输出的 `.html` 文件。
- `←` / `→`（或空格）翻页，右下角显示页码。
- 想导出 PDF：浏览器打印（Ctrl/Cmd+P），已设置每页一张。
- 想微调风格：改 HTML 顶部 `:root` 里的 CSS 变量，一处改全局生效。

---

## 小贴士

- 参考信息越完整（高清图 / 可访问的网页），复刻越准。
- 风格是"审美方向"的复刻，不抄袭具体内容或受版权保护的素材。
- 预设的持久化依赖文件写入权限：Kiro / Claude Code 本地环境可长期保留；Claude.ai 沙箱内可能不持久，建议手动下载留存。
