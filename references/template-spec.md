# 同济模板规范

模板采用用户提供的源工程封面、章节提纲和正文母版。画幅为16:9（约16 cm × 9 cm），文档类为 `ctexbeamer`，默认11pt、`fontset=none`。主题文件保留Tongji-Beamer的版权和LPPL声明。

## 文件职责

| 文件 | 职责 |
|---|---|
| `main.tex` | 依赖、文件组织、封面与附录入口 |
| `metadata.tex` | 标题、副标题、作者、单位、日期 |
| `branding.tex` | 标识资源、插入命令与组合入口 |
| `beamerinnerthemetongji.sty` | 封面、章节提纲、列表 |
| `beamerouterthemetongji.sty` | 正文标题区与页码 |
| `beamerfontthemetongji.sty` | 字体与替代字体 |
| `beamercolorthemetongji.sty` | 主题颜色 |
| `layouts.tex` | 正文宏、出处与演讲备注 |
| `contents/*.tex` | 正文、附录与书目 |
| `figure/`、`reference.bib` | 图形与文献资源 |

## 封面

`main.tex` 在 `[plain]` frame 中调用 `\titlepage`。标题、副标题、作者、单位和日期读取 `metadata.tex`；日期默认 `\today`，也可指定汇报日期。

右上保留原图 `figure/tongji-cover.png`，高1.95 cm，距上边0.12 cm、右边0.15 cm；蓝带位于距上边2.42–6.03 cm。主标题28pt、副标题14pt，下方排列作者、单位、日期。

### 长标题

默认单行布局保持原样：标题中心距上边3.90 cm，副标题中心4.88 cm。双行标题在 `metadata.tex` 启用开关，副标题下移至5.43 cm；蓝带、字号、标识及作者区不变。

```tex
\TongjiLongTitletrue
\title[城际航空客流预测]{基于多源大数据的城际航空客流\\需求预测及场景分析研究}
\subtitle{预答辩}
```

先按语义手动分成两行，避免依赖字符数猜测换行。若仍超宽，只在该项目的标题内将字号调整至24–28pt，不横向压扁文字；未经授权不删改题目。超过两行或多行作者需单独排版并渲染核验，不继续下移副标题挤占作者区。回到单行时使用 `\TongjiLongTitlefalse`。

## 章节提纲

标题为“汇报提纲”，中文编号与章节名20pt。编号色块1 cm × 0.82 cm，右侧边框长10.25 cm；当前章节深红，其余主蓝。

章节写在正文 `\section{...}` 中，提纲通过 `.toc` 和 `\tableofcontents[part=0,hideallsubsections]` 生成。主报告每章开始调用 `[plain,noframenumbering]` 提纲。默认布局适合3–4章；更多章节或长名称需调整行距和宽度。使用 `\part` 时同步调整提纲过滤条件。

## 正文与页码

正文白底，标题黑色17pt，左侧灰竖条，下方细线；左右边距7 mm，主旨句11.3pt、出处8.2pt、页码6.8pt。标题细线终点距左边11.38 cm，标题与右上标识之间留出间距。

封面计入主报告并隐藏页码，章节提纲不计数。正文使用 `\insertframenumber/\insertmainframenumber`；`\appendix` 后采用 `A\insertframenumberinappendix`，书目接续附录编号。总数和附录编号由Beamer原生计数生成。

## 正文接口

```tex
\talknote{演讲者展开说明}
\reviewslide[可选结论条]{短标题}{可见主旨句}{主体图文}{出处或条件}
```

`\reviewslide` 在帧标题后保留 `\vspace{0mm}`，使主旨句进入正文；背景与结论条的作用域为单页。含verbatim的代码页使用原生 `[fragile]` frame。

主体支持列表、columns、TikZ、表格、公式和图片。图片按可用宽高等比缩放。普通引文使用 `\cite{key}`；`\sourcelist{key1,key2}{作者（年份）}` 显示出处并追加自动编号，键与可见作者对应。文献采用全文连续编号，默认显示DOI与网页链接；条目核验和分页见[引用核验](citations.md)。

## 标识接口

`main.tex` 加载主题后读取 `branding.tex`。默认封面调用 `\TongjiCoverBrand`，正文调用 `\TongjiHeaderBrand`：四色条＋0.18 cm间距＋高0.64 cm的独立校徽，总宽约2.03 cm，右边距0.45 cm。

四色条由TikZ绘制，色块边长0.24 cm、间隙为边长的0.35倍。独立校徽复用原工程的矢量曲线；蓝色插入文件、SVG与原稿分别保存在 `figure/branding/tongji-seal.pdf`、`tongji-seal.svg`、`tongji-seal-source.pdf`。同目录另有根据用户附件轮廓制作的完整校名蓝色和白色版本，以及附件原图。

```tex
\TongjiSeal[height=1cm]
\TongjiColorBars[.3cm] % 单个色块边长
\TongjiLogo[width=3cm]
\TongjiLogoWhite[width=3cm] % 深色背景用
```

资源路径由 `\TongjiSealFile`、`\TongjiLogoFile`、`\TongjiLogoWhiteFile`、`\TongjiCoverImageFile` 管理。改路径可替换资源，重定义组合入口可调整构成。例如只显示四色条：

```tex
\renewcommand{\TongjiHeaderBrand}{\TongjiColorBars}
```

标识保持宽高比，替换后检查标题和细线的间距。颜色与强调用法见[配色定义](color-palette.md)，示例页位于 `contents/appendix.tex` 和 `contents/palette.tex`。

## 字体

macOS优先使用Helvetica Neue、PingFang SC、宋体、Menlo、STIX Two Math、Arial Unicode MS；缺失时使用TeX Gyre Heros、Fandol及Latin Modern。更换系统或字体后重新编译并检查字形与换行。
