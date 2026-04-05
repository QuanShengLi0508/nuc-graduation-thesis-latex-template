# NUC Graduation Thesis LaTeX Template

这个目录里的 `main.tex` 是根据中北大学当前 `docx` 文档提炼出来的毕业设计说明书 / 毕业论文 LaTeX 模板，已经尽量还原了这些关键格式：

- A4 纸张
- 前置部分上边距 3 cm，正文页边距 2.5 cm
- 正文默认小四宋体，1.5 倍行距
- 一级标题 `1` 用小三黑体加粗
- 二级标题 `1.1` 用小四黑体加粗
- 三级标题 `1.1.1` 用小四黑体
- 目录到三级标题
- 目录标题用 4 号黑体居中
- 参考文献标题用小三黑体加粗居中，条目用小四宋体
- 封面、摘要和正文骨架已改为空白模板
- 目录结构参考了 `毕业设计04--说明书目录.doc`

## 编译方式

在当前目录运行：

```bash
latexmk -xelatex main.tex
```

如果只想手动编译，也可以：

```bash
xelatex main.tex
xelatex main.tex
```

## 开源时怎么处理字体

这个模板已经按“仓库可开源、效果可尽量还原”的方式处理字体：

- 仓库里不要求强行捆绑专有字体
- `main.tex` 会优先读取 `fonts/local/` 里的授权字体文件
- 如果 `fonts/local/` 没有，再去找本机系统字体
- 再找不到时，只对预览用开源字体兜底，并在编译日志里给出 warning

当前字体搜索顺序大致如下：

- 正文宋体：`fonts/local/simsun.ttc` -> `fonts/local/songti.ttc` -> `SimSun` -> `宋体` -> `STSong` -> `Songti SC`
- 黑体：`fonts/local/simhei.ttf` -> `fonts/local/heiti.ttf` -> `SimHei` -> `黑体` -> `Heiti SC`
- 楷体：`fonts/local/kaiti.ttf` -> `KaiTi` -> `楷体` -> `Kaiti SC` -> `STKaiti`
- 封面大标题：`fonts/local/cover-major.ttf` -> `方正大标宋简体` -> `FZDaBiaoSong-B06S`

如果你后续要把字体一起提供给别人下载，当前模板也兼容这种做法：

1. 把字体继续放在 `fonts/local/`。
2. 模板会优先读取这里的字体文件。
3. 没有这些字体时，再回退到本机系统字体。

## 本机上的“宋体”说明

你这台 macOS 机器上，WPS 里显示的“宋体”实际可以由系统的 `Songti.ttc` 提供。模板现在已经兼容这一点：

- 若检测到 `songti.ttc`，会明确使用其中的常规字重，避免误用过黑的字重
- 所以摘要正文不会再出现之前那种发粗的问题

## 你后续主要改哪里

1. 修改封面信息：直接改 `main.tex` 顶部这些命令

```tex
\newcommand{\graduationyear}{2026}
\newcommand{\studentname}{张三}
\newcommand{\studentid}{2026000000}
\newcommand{\college}{某某学院}
\newcommand{\majorname}{某某专业}
\newcommand{\advisorname}{某某老师}
\newcommand{\thesisdate}{2026 年 06 月}
```

2. 修改题目：改这几行

```tex
\newcommand{\thesistitlelinea}{论文题目第一行}
\newcommand{\thesistitlelineb}{论文题目第二行}
\newcommand{\thesistitlecn}{中文题目}
\newcommand{\thesistitleen}{English Title}
```

3. 写摘要：直接填写这些命令

```tex
\newcommand{\cnabstracttext}{中文摘要正文}
\newcommand{\cnkeywords}{关键词1, 关键词2, 关键词3}
\newcommand{\enabstracttext}{English abstract text}
\newcommand{\enkeywords}{keyword 1, keyword 2, keyword 3}
```

4. 写正文：当前正文骨架已经按目录范例留好，可直接改章节标题并填内容

5. 写参考文献：把 `\referencelist` 命令里的内容补上

## 说明

- 你这个原始 `docx` 的封面用了图片和文本框混排，LaTeX 这份模板已经尽量按视觉结构还原，但如果学院对封面位置要求极严，最后可以再按导出的 PDF 微调几个间距。
- 现在模板里的个人信息和示例论文内容已经清空，可以直接作为空白模板继续修改。
