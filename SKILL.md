---
name: latex-beamer-ppt-production
description: Use only when explicitly requested to create, recreate from a PPT, revise, compile, or validate LaTeX Beamer slides with the bundled Tongji template.
---

# LaTeX Beamer PPT Production

使用同济模板制作学术汇报：原图封面、章节高亮提纲、黑色标题与灰竖条正文母版。正文页眉由自绘四色条和独立矢量校徽组成。

## 工作流程

1. **识别任务**：新建或结构重写先给页级提纲，包含标题、听众、时长、章节、逐页任务与页数，以及参考文献/附录/致谢安排；用户确认或授权自行决定后制作。PPT复刻沿用原稿结构，局部修订直接按已有授权处理，不重复要求确认提纲。
2. **准备工程**：新建时将 `assets/template/` 复制到交付目录；已有工程就地编辑，沿用其内容和资源。
3. **制作页面**：在 `metadata.tex` 维护汇报信息，在 `contents/` 写正文和章节，在 `branding.tex` 配置标识。双行长标题启用 `\TongjiLongTitletrue`，在语义边界换行。使用相对资源路径，保留同济封面、章节提纲、字体、配色与页眉样式。
4. **管理引用**：有外部来源时统一维护 `reference.bib`，用 `\cite` 自动编号；核对引用与条目，缺失信息标为待核。用户要求完整参考文献时在文末展示，不手写各页编号。
5. **编译核验**：执行 `make build`，检查缺字、溢出、未解析引用并渲染PDF；核对长标题间距、原稿内容、标识、页码和引用对应关系。
6. **交付**：提供当前源文件生成的PDF和可编辑工程，说明验证结果及仍待补全的来源。

## 按任务读取

- 文件职责、封面、提纲、页码与标识接口：[模板规范](references/template-spec.md)。
- 按已有PPT逐页复刻、提取原图及重建流程图：[PPT复刻](references/ppt-recreation.md)。
- 整理文献、统一编号或补文末书目：[引用核验](references/citations.md)。
- 叙事顺序、页级表达与学术证据：[内容拆页](references/content-to-slides.md)。
- 色值、层级用色与红色加粗：[配色定义](references/color-palette.md)。
- 依赖、编译命令与检查项目：[编译和核验](references/build-and-verify.md)。

内容修改集中在正文；布局、母版、字体和颜色分别在对应文件维护。视觉调整沿用用户已确定的封面、校徽和四色条样式。
