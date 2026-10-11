# MIT18.01_note · 单变量微积分中文复习笔记

![GitHub stars](https://img.shields.io/github/stars/wsthtk/MIT18.01_note?style=flat-square)
![GitHub last commit](https://img.shields.io/github/last-commit/wsthtk/MIT18.01_note?style=flat-square)
![Obsidian](https://img.shields.io/badge/obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-0366d6)

> 基于 MIT OpenCourseWare 18.01SC《Single Variable Calculus》官方讲义整理的**中文精读、复习向** Markdown 笔记，Obsidian 打开即用。

## 课程信息

- **课程**：MIT 18.01SC Single Variable Calculus（Fall 2010）
- **主讲**：Prof. David Jerison
- **规模**：共 101 个 Session，主课程约 28.5 小时
- **组织方式**：按 Lecture 整理，每个 Lecture 对应多个 Session
- **原始课程**：https://ocw.mit.edu/courses/18-01sc-single-variable-calculus-fall-2010/

## 为什么会有这个仓库

MIT 18.01 是最经典的微积分公开课之一，但官方讲义是全英文 PDF，对中文学习者不友好。本项目把每节课的官方笔记重新整理为结构化的中文复习笔记：保留数学推导的完整骨架，同时压缩到适合考前速刷的长度。

## 特性

- **复习向精炼**：每讲只保留核心定义、定理、推导骨架与易错点
- **个人重点导航**：每讲开头置顶你自己标记的重点（锚点跳转列表）
- **思考与问答**：正文"补充"入口 ↔ 文末 AI 问答区，保留提问原话与完整解答
- **英文术语标注**：重要术语首次出现处标注英文原文
- **每讲思维导图**：文末附独立 SVG 思维导图（存放于“图片”目录下）
- **LaTeX 公式**：行内 `$...$`，块级 `$$...$$`，严格区分
- **Obsidian Callout**：重点 / 注意 / 技巧用 callout 高亮
- **AI 辅助整理**：整理提示词公开在 `MIT18.01/提示词.md`，欢迎复用
- **课程地图**：完整 Session 索引见 `MIT18.01/map.md`

## 目录结构

```
MIT18.01_note/
├── README.md
└── MIT18.01/
    ├── Unit 1/                  # Unit 1 Differentiation 微分
    │   ├── 图片/                # 本单元图片素材（含每讲思维导图 SVG）
    │   ├── lecture 1.md         # Lecture 1（Session 1-2）
    │   ├── lecture 2.md         # Lecture 2（Session 3-5）
    │   ├── lecture 3.md         # Lecture 3（Session 6-8）
    │   ├── lecture 4.md         # Lecture 4（Session 9-12）
    │   └── lecture 5.md         # Lecture 5（Session 13-15）
    ├── 提示词.md                 # AI 整理笔记的提示词（可复用）
    └── map.md                   # 课程地图：全部 Session 索引

```

> 目前进度：**Unit 1 进行中**（已完成 Lecture 1–5，即 session 1 ~ 15），后续持续更新。

## 课程单元（18.01SC 完整规划）

| Unit | 主题 | 状态 |
| --- | --- | --- |
| Unit 1 | Differentiation 微分 | 🔄 进行中 |
| Unit 2 | Applications of Differentiation 微分应用 | ⏳ 待开始 |
| Unit 3 | The Definite Integral and its Applications 定积分及应用 | ⏳ 待开始 |
| Unit 4 | Techniques of Integration 积分技巧 | ⏳ 待开始 |
| Unit 5 | Exploring the Infinite 无穷级数与逼近 | ⏳ 待开始 |
| Unit 6 | Solving Differential Equations 常微分方程 | ⏳ 待开始 |

## 学习建议

来自学习过程中的实测经验（详见 `map.md`）：

- **直接看 YouTube 上的完整 Lecture**，课程自带的 Clip 没啥用
- 每个 Clip 下面有官方笔记，可以截图后一起喂给 AI 整理
- Session 下面的 solution 文件已经包含了 problem 文件，不用单独找
- 一个 Lecture 对应多个 Session，整理时按 Lecture 归档更高效
- 主课程约 28.5 小时，勤奋一点一个月可以学完

## 快速开始

1. `git clone https://github.com/wsthtk/MIT18.01_note.git`，或直接下载 ZIP
2. 用 [Obsidian](https://obsidian.md) 打开仓库文件夹（Open folder as vault）
3. 无需额外插件：公式（MathJax）、Callout SVG 嵌入显示均为 Obsidian 内置能力

GitHub 网页端可直接显示嵌入的 SVG 图片

## 笔记规范

每篇笔记遵循统一格式：

| 规范项 | 约定 |
| --- | --- |
| 定位 | 复习向，适当精炼，不照搬讲义全文 |
| 个人重点 | 开头设 `# 重点`，用跳转链接列出你标记的重点（`[标题](#锚点)` 指向正文）|
| 公式 | 行内 `$...$`，块级 `$$...$$`，严格区分、不可混用 |
| 术语 | 重要术语标注英文原文 |
| 图片 | 先用文字简单描述占位，后续自行补充（图片放对应 Unit 的 `图片/` 目录） |
| 强调块 | Obsidian Callout 语法（`> [!note]` 等） |
| 思考与问答 | 正文在对应处留 `### 补充` 入口（`[补充 N](lecture x.md#补充 N)`）；文末以 `# 补充 N` 区块存放你的提问原话与 AI 回答，编号互相对应 |
| 思维导图 | 每讲文末附独立 SVG （引用方式：`![](./图片/xxx.svg)`）" |


## 如何贡献

- 发现勘误：开 Issue，或直接提 PR
- 想补充内容：欢迎新增例题、直观解释、记忆技巧
- 排版建议：跟随上面的「笔记规范」即可

## 版权与许可

- 本仓库笔记基于 MIT OpenCourseWare 18.01SC《Single Variable Calculus》官方材料整理
- MIT OCW 官方材料采用 **CC BY-NC-SA 4.0**（署名—非商业性使用—相同方式共享）许可
- 因此本项目以相同许可 **CC BY-NC-SA 4.0** 发布：欢迎自由分享，但**请勿用于商业用途**，转载须署名并注明来源

## 致谢

感谢 MIT OpenCourseWare 提供免费开放的高质量课程资源，感谢 David Jerison 教授的精彩讲授。

---

⭐ 如果这份笔记对你有帮助，欢迎 Star & Fork～
