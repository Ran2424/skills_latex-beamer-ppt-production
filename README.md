# latex-beamer-ppt-production

用于制作、编译和核验采用同济模板的LaTeX Beamer学术汇报。工作流程见[SKILL.md](SKILL.md)，模板位于[assets/template/](assets/template/)。

## 模板效果

以下预览由当前模板编译生成，总览选取前12页，包含封面、章节高亮提纲、正文和附录。

### 12页总览

![同济 Beamer 模板前12页总览](docs/previews/overview-12-pages.png)

### 封面

![同济蓝色封面](docs/previews/cover.png)

### 章节高亮提纲

![章节高亮提纲](docs/previews/agenda.png)

### 正文与流程图

![灰竖条标题、四色条校徽与流程图正文](docs/previews/body.png)

## 安装与调用

将本仓库放入 `~/.codex/skills/latex-beamer-ppt-production`，也可从仓库克隆：

```bash
git clone https://github.com/Ran2424/latex-beamer-ppt-production.git ~/.codex/skills/latex-beamer-ppt-production
```

调用 `$latex-beamer-ppt-production`，提供主题、听众、时长及材料。
