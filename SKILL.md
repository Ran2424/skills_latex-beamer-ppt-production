---
name: latex-beamer-ppt-production
description: Use this skill only when explicitly requested by the user. Use it when creating, revising, restructuring, compiling, validating, or exporting LaTeX Beamer slides in this Tongji Beamer project, especially for paper talks, project updates, proposals, course presentations, and report-style decks. Before editing slide files, first draft a page-level deck outline and ask the user to confirm or revise it.
---

# Latex Beamer PPT Production

在这个项目里制作或修改 LaTeX Beamer PPT 时使用本技能。

## 目标

产出的幻灯片必须同时满足：

- 保持当前 Tongji Beamer 模板风格
- 能用 XeLaTeX 稳定编译并导出 PDF
- 结构清楚，页序合理，适合口头汇报
- 每页只表达一个重点
- 开始正式制作前，先给用户一份可修改的目录初稿

## 适用任务

本技能适用于以下几类任务：

- 论文汇报
- 项目进展汇报
- 方案或开题汇报
- 课程展示
- 综述或读书报告
- 已有 deck 的重写、扩写、压缩或修订

如果用户只是要普通 Markdown 提纲，不要直接进入 LaTeX 制作。

## 技能目录

- `SKILL.md`：工作规则
- `assets/template/`：Tongji Beamer 模板副本
- `references/content-to-slides.md`：把材料重构成页级表达时可参考

优先查看这些模板文件：

- `assets/template/main.tex`
- `assets/template/contents/introduction.tex`
- `assets/template/contents/body.tex`
- `assets/template/contents/summary.tex`
- `assets/template/beamercolorthemetongji.sty`
- `assets/template/beamerfontthemetongji.sty`
- `assets/template/beamerouterthemetongji.sty`
- `assets/template/latexmkrc`

## 必做前置步骤

开始写任何 `tex` 文件前，必须先给用户一份“目录初稿”，让用户确认或修改。

这份目录初稿至少要包含：

- 汇报标题
- 使用场景或听众
- 预计总页数
- 一级章节目录
- 每一部分预计页数
- 是否需要参考文献页、致谢页、附录页

如果用户给的信息还不完整，也要先基于现有材料给出一版可修改的初稿，不要停在空泛提问。

只有以下两种情况可以进入正式制作：

- 用户明确确认目录初稿
- 用户明确说“你直接定”或等价表述

如果用户修改目录，以用户版本为准。

## 标准工作流

### 阶段 1：理解任务

1. 确认 deck 是新建、续写、改写，还是压缩已有内容。
2. 识别材料来源：论文、项目文档、报告、笔记、已有 `tex`、已有 PPT outline。
3. 确认约束：时长、页数、听众、语言、是否要讲相关工作、是否要参考文献。

### 阶段 2：先给用户目录初稿

1. 先输出一版目录初稿，不要直接开始写页内容。
2. 目录初稿要写到页级粒度，至少说明每部分预计放什么。
3. 目录初稿应优先写成适合口头汇报的叙事顺序，而不是机械照搬原文目录。
4. 如果是论文类汇报，默认覆盖：背景、问题、方法、实验或案例、结论。
5. 如果是项目或方案类汇报，默认覆盖：背景、目标、方案、进展或结果、下一步。

### 阶段 3：确认后再制作

1. 用户确认目录后，再决定改哪些文件。
2. 内容修改优先落在 `contents/*.tex`。
3. 样式修改只在用户明确要求时再动 `.sty` 文件。
4. 如果是新 deck，优先复用模板结构，不要从零乱搭。

### 阶段 4：逐页写作

1. 先写标题页和结构页，再写正文。
2. 每页先确定“这一页要让听众记住什么”，再写文字和图。
3. 引言、背景、贡献、总结类页面优先用结构型版式。
4. 架构、流程、结果、对比、案例类页面优先用图文型版式。
5. 写完初稿后，统一检查术语、页间衔接和页序。
6. 文案收束阶段可使用 Humanizer Zh 优化措辞，但不要改动技术含义。

### 阶段 5：编译与验证

1. 必须实际编译，不接受只改不验。
2. 默认编译命令：

```bash
latexmk -xelatex -interaction=nonstopmode main.tex
```

3. 如果默认命令失败，再用手动兜底：

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

4. 交付前必须确认 `main.pdf` 已更新成功。

## 目录初稿模板

对用户给出的第一版目录，优先使用这种格式：

```md
# 目录初稿

- 标题：
- 场景：
- 预计总页数：

## 1. 第一部分（X 页）
- 第 1 页：
- 第 2 页：

## 2. 第二部分（X 页）
- 第 3 页：
- 第 4 页：
```

如果材料还不完整，也要给出可落地的初稿，而不是只问“你想怎么做”。

## 常见目录模式

### 论文汇报

推荐顺序：

- 研究背景
- 问题定义与动机
- 方法与关键机制
- 实验设置
- 结果与分析
- 结论与局限

### 项目进展汇报

推荐顺序：

- 背景与目标
- 本阶段任务
- 已完成工作
- 当前结果或样例
- 风险与下一步

### 方案或开题汇报

推荐顺序：

- 背景与问题
- 目标与范围
- 方案设计
- 实施路径或实验设计
- 预期结果与计划

### 课程展示或综述

推荐顺序：

- 主题引入
- 核心概念
- 方法或案例分类
- 重点案例展开
- 总结

## 页面版式

正文优先使用以下三类版式。

### 版式 1：结构型双模块页

适合：

- 背景
- 意义
- 任务拆解
- 贡献总结
- 结论归纳

参考文件：

- `assets/template/contents/introduction.tex`

特点：

- 顶部是页标题
- 主体是 1 到 2 个 `block`
- 每个 `block` 放 `itemize` 或 `enumerate`
- 每块控制在 3 到 5 条
- 每条尽量一句话说完

### 版式 2：结论先行的上文下图页

适合：

- 架构图
- 流程图
- 结果图
- 对比图
- 应用场景图

特点：

- 标题先点明结论
- 上方先给一句关键句
- 下半部分放主图
- 必要时图下补一句短解释

### 版式 3：对比或结果表页

适合：

- baseline 对比
- ablation
- 指标结果
- 方案对比
- 优缺点对照

特点：

- 先说结论，再给表格或对照项
- 表格不要过大
- 同页只保留一组主要比较
- 如果比较维度太多，拆成两页

## 写作规则

- 一页只讲一个重点。
- 标题尽量写成结论句或判断句，不要只写章节名。
- 宁可拆页，也不要把一页塞满。
- 中文句子尽量短。
- 正文不要写成大段文字。
- 列表页控制在 3 到 5 个要点。
- 图片页优先保留一张主图，不要堆很多小图。
- 如果一页需要同时解释图和大量文字，优先拆页。
- 同一概念前后叫法要一致。

## 论文类汇报额外要求

- 不要只复述摘要。
- 引言页如果承担背景或相关工作功能，必须把研究脉络讲清楚。
- 相关工作不要只列论文名，要说明已有方法做到了什么，还缺什么，本文补在哪里。
- 背景判断、相关研究归纳和“本文补位”这三类句子，默认要有文献支撑。
- 优先复用原文引言里已经使用的引用，不要随意换成无关文献。

## 图片与资源规则

- 图片使用相对路径。
- 优先放在 `contents/figure/` 或 `figure/`。
- 图优先使用清晰的 PDF、PNG、SVG 转换图。
- 图里如果已经标签很多，不要再配很长 caption。
- 如果图很复杂，可在图下补一句短解释。

## 参考文献规则

- 本项目使用 `biblatex` + `biber`。
- 不要运行 `bibtex`。
- 引用使用 `\cite{key}`。
- 参考文献在 `main.tex` 里通过 `\printbibliography` 输出。

## 编辑边界

- 内容改动优先放在 `contents/*.tex`。
- 模板风格改动放在 `.sty`。
- 除非用户明确要求，不要重做整套视觉样式。
- 除非用户明确要求，不要打乱现有 deck 已经稳定的章节节奏。

## 验证清单

交付前逐项确认：

- 用户已确认目录初稿，或已明确授权你直接定目录
- `main.pdf` 已重新生成
- 没有缺失图片路径
- 没有缺失引用键
- 没有明显溢出、截断、过小字号
- 页序合理
- 标题层次一致
- 每页所用版式和内容类型匹配
- 最终 PDF 与目录初稿一致，或已按用户反馈修订
