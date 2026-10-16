# 编译与核验

## 依赖和命令

需要XeLaTeX、latexmk、biber，以及ctex、Beamer、biblatex-gb7714-2015、TikZ、unicode-math和模板字体。文献使用biblatex＋biber。

在工程目录执行 `make build`，其流程为：

```bash
latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
cp build/main.pdf main.pdf
```

`latexmkrc` 配置biber与PDF 1.7。编译文件留在 `build/`。目录、页码和引用由latexmk组织多轮更新。

手动排错时，先创建 `build/`，依次执行：

```bash
xelatex -interaction=nonstopmode -halt-on-error -output-directory=build main.tex
biber --input-directory=build --output-directory=build main
xelatex -interaction=nonstopmode -halt-on-error -output-directory=build main.tex
xelatex -interaction=nonstopmode -halt-on-error -output-directory=build main.tex
```

## 检查项目

| 检查 | 内容 |
|---|---|
| 最终日志 | 编译错误、引用、图片、缺字、Overfull hbox/vbox和重编译提示 |
| 信息一致 | 封面字段、章节名称、高亮、正文总数与附录编号；复刻时核对原稿页序及新增页数 |
| 视觉布局 | 单行/双行封面的标题与副标题、标题与标识、图内文字、来源和页脚的间距及可读性 |
| 引用对应 | 全文连续编号、正文与文末条目匹配、DOI/链接有效、待核材料明确标注；见[引用核验](citations.md) |
| 产物对应 | PDF生成时间、页数、元数据与当前源文件 |

用Poppler或PyMuPDF渲染全部页面，查看总览并放大检查封面、提纲、密集正文、公式与书目。叠加图形、缩放和字体替代的效果通过渲染确认。

修改模板计数或目录逻辑时，在副本中验证章节改名、正文增删与附录变化；修改标识接口时验证资源替换和组合入口。

修改封面布局时，在副本中分别编译默认短标题与双行长标题＋非空副标题，检查蓝带内文字不重叠且作者区不变。修改引用配置时，检查重复引用沿用同一编号，书目分页后编号不重置；缺字和未解析引用须解决后再交付。

## 交付

交付PDF和可编辑源工程，编译诊断文件可另存。技能维护模板源文件，具体汇报及验证产物保存在对应交付目录。
