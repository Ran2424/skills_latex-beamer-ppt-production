# 配色与强调

颜色在 `assets/template/beamercolorthemetongji.sty` 中定义。

## 主题颜色

| 名称 | Hex | RGB | 用途 |
|---|---|---|---|
| `TJBluePrimary` | `#365F9F` | 54,95,159 | 封面蓝带、提纲与结构色 |
| `TJBlueSecondary` | `#002060` | 0,32,96 | 次级强调 |
| `TJAgendaActive` | `#CC0000` | 204,0,0 | 提纲当前章节 |
| `Ink` | `#33404B` | 51,64,75 | 主旨与正文 |
| `Muted` | `#66717C` | 102,113,124 | 出处与说明 |

正文标题为黑色；竖条与细线使用 `black!48`，提纲边框 `black!25`，页码 `black!45`，结论条背景 `TJBluePrimary!10`。

## 四色与层级

四色条按下表顺序绘制。每种颜色同时提供一个层级别名，供页面内容选用。

| 色块名称 | 层级别名 | Hex / RGB | 建议用途 |
|---|---|---|---|
| `TJChipGray` | `TJLevelText` | `#4B4B4B` / 75,75,75 | 正文、说明、中性信息 |
| `TJChipBlue` | `TJLevelSecondary` | `#0070C0` / 0,112,192 | 二级标题、分组、局部强调 |
| `TJChipNavy` | `TJLevelPrimary` | `#334D80` / 51,77,128 | 一级标题、关键结构、主要判断 |
| `TJChipPale` | `TJLevelSoft` | `#82ACD3` / 130,172,211 | 辅助标记、边框、浅底 |

后两色采用原PNG在白底上的等效色。浅蓝适合浅底和辅助图形，正文小字选用深色。

```tex
\textcolor{TJLevelPrimary}{主要判断}
\textcolor{TJLevelSecondary}{次级强调}
```

## 红色与加粗

强调红为 `TJOptionalRed`：Hex `#C43C39`，RGB `196,60,57`。可与加粗配合，突出重点词语或关键句子。

```tex
\textcolor{TJOptionalRed}{\textbf{重点词语}}
\textcolor{TJOptionalRed}{\textbf{关键句子}}
```

`contents/palette.tex` 展示色样、调用名和用途。四色条使用四种基础色；提纲高亮与内容强调分别使用 `TJAgendaActive`、`TJOptionalRed`。

## 调整颜色

主题颜色集中在颜色主题文件中修改。具体研究图形的语义色在该工程图形文件中定义，跨页保持含义一致。

Logo的蓝色填充为 `#365F9F`，由独立矢量资源保存；换色时修改SVG并同步导出PDF。
