# ReportUESTC-电子科技大学课程报告模板

[![](https://img.shields.io/badge/license-LPPL-blue)](https://www.latex-project.org/lppl/) [![](https://img.shields.io/github/last-commit/x-magus/ThesisUESTC)](https://github.com/x-magus/ThesisUESTC/zipball/master) [![](https://img.shields.io/github/issues/x-magus/ThesisUESTC)](https://github.com/x-magus/ThesisUESTC/issues)

## 项目说明

本项目提供用于排版电子科技大学课程报告的LaTeX模板类，旨在帮助电子科技大学的学生高效地完成课程报告的写作。模板基于原UESTC学位论文模板简化而来，去除了学位论文的复杂功能，专门用于课程报告的排版需求。

### 原作者信息

原始毕业论文模板由电子科技大学物理电子学院2014级硕士研究生**王稳**（wangwen1192@outlook.com）编写。

原项目地址：https://github.com/bdebye/thesisuestc.git

### 课程报告版本修改者

课程报告模板（report-uestc）基于原版thesis-uestc模板修改而来，由**XingGou516**（xingfeiceng@gmail.com）进行简化和改编。

---

## 目录

- [模板特点](#模板特点)
- [快速开始](#快速开始)
- [详细使用说明](#详细使用说明)
- [示例文件](#示例文件)
- [注意事项](#注意事项)
- [版权说明](#版权说明)

# 课程报告模板使用指南

## 模板特点

课程报告模板（report-uestc）是在原UESTC学位论文模板基础上精简而来的轻量级版本，主要特点：

### 保留的功能
- 基本的文档格式和排版
- 章节标题样式
- 图表支持
- 参考文献管理（支持BibTeX和手动录入）
- 数学公式
- 算法环境
- 中英文混排
- 摘要和关键词
- 目录生成

### 移除的功能
- 复杂的学位论文封面和扉页
- 独创性声明和论文使用授权
- 学位类型选项（bachelor/master/doctor等）
- 外文资料原文和译文
- 攻读学位期间取得的成果
- 复杂的双语页眉和罗马数字页码
- 奇偶页不同的页眉设置
- 致谢部分

### 简化的功能
- 统一使用阿拉伯数字页码
- 简化的封面样式（保留校徽和校名）
- 简化的命令参数（不再需要中英文双语参数）
- 统一的页眉"电子科技大学课程报告"

## 快速开始

### 1. 基本环境

使用模板需要系统安装任意一种TeX环境，如[TeXLive](http://mirror.ctan.org/systems/texlive/Images/)、[MacTeX](https://www.tug.org/mactex/mactex-download.html)和[MiKTeX](https://miktex.org/download)，安装有 SimSun 和 SimHei 字体（宋体和黑体）以及 Times New Roman 英文字体。

### 2. 文档类导入

```latex
\documentclass{report-uestc}
```

### 3. 基本信息设置

```latex
\title{综述报告}
\author{张三}
\school{计算机科学与工程学院}
\major{计算机科学与技术}
\advisor{李教授}
\studentnumber{202112345678}
\date{\the\year 年\the\month 月\the\day 日}
```

### 4. 编译方法

**推荐使用latexmk（自动编译）：**
```bash
latexmk example.tex
```

**手动编译：**
```bash
xelatex example.tex
xelatex example.tex  # 第二次编译以生成正确的目录和引用
```

**包含BibTeX参考文献时：**
```bash
xelatex example.tex
bibtex example.aux
xelatex example.tex
xelatex example.tex
```

## 详细使用说明

### 文档结构

```latex
\begin{document}

% 生成封面
\makecover

% 中文摘要（可选）
\begin{chineseabstract}
摘要内容...
\chinesekeyword{关键词1，关键词2，关键词3}
\end{chineseabstract}

% 英文摘要（可选）
\begin{englishabstract}
Abstract content...
\englishkeyword{Keyword1, Keyword2, Keyword3}
\end{englishabstract}

% 目录
\reporttableofcontents

% 正文开始
\reportcontent

\chapter{绪\hspace{6pt}论}
\section{第一节}
...

% 参考文献（BibTeX方式）
\nocite{*}  % 可选：显示所有未引用的文献
\reportbibliography{reference}

% 或使用手动方式
\begin{reportthebibliography}
\bibitem{ref1} ...
\end{reportthebibliography}

\end{document}
```

### 封面信息

使用 `\makecover` 命令生成简化的封面，包含：
- 学校名称和校徽
- 报告标题
- 学院、专业、学号、姓名、指导教师、日期

所有信息通过以下命令设置：

| 命令 | 说明 |
|---|---|
| `\title{标题}` | 报告标题 |
| `\author{姓名}` | 作者姓名 |
| `\school{学院}` | 学院名称 |
| `\major{专业}` | 专业名称 |
| `\advisor{教师}` | 指导教师 |
| `\studentnumber{学号}` | 学号 |
| `\date{日期}` | 日期 |

### 摘要

**中文摘要：**
```latex
\begin{chineseabstract}
本文对数据库新技术进行了全面的综述...
\chinesekeyword{数据库，分布式系统，NoSQL}
\end{chineseabstract}
```

**英文摘要：**
```latex
\begin{englishabstract}
This paper provides a comprehensive review...
\englishkeyword{Database, Distributed Systems, NoSQL}
\end{englishabstract}
```

### 目录

使用 `\reporttableofcontents` 生成目录。

### 正文

使用 `\reportcontent` 标记正文开始。支持的章节层次：
- `\chapter{}`：章
- `\section{}`：节  
- `\subsection{}`：小节
- `\subsubsection{}`：小小节

### 参考文献

**BibTeX方式（推荐）：**
```latex
\nocite{*}  % 可选：显示所有文献
\reportbibliography{reference}
```

**手动方式：**
```latex
\begin{reportthebibliography}
\bibitem{ref1} 作者. 标题[J]. 期刊, 年份, 卷(期): 页码.
\end{reportthebibliography}
```

**引用方式：**
- `\cite{key}`：普通引用 [1]
- `\citing{key}`：上标引用 ¹

### 图表

**插入图片：**
```latex
\begin{figure}[h]
\centering
\includegraphics[width=0.8\textwidth]{图片文件名}
\caption{图片标题}
\label{fig:label}
\end{figure}
```

**插入表格：**
```latex
\begin{table}[h]
\centering
\caption{表格标题}
\label{tab:label}
\begin{tabular}{ccc}
\hline
列1 & 列2 & 列3 \\
\hline
数据1 & 数据2 & 数据3 \\
\hline
\end{tabular}
\end{table}
```

### 数学公式

**行内公式：** `$E = mc^2$`

**行间公式：**
```latex
\begin{equation}
E = mc^2
\label{eq:einstein}
\end{equation}
```

### 附录

```latex
\reportappendix
\chapter{附录标题}
内容...
```

单独附录：
```latex
\reportsingleappendix
\section{附录内容}
```

## 示例文件

完整示例请参考 `example.tex` 文件。

## 注意事项

1. 必须使用XeLaTeX编译引擎
2. 需要安装中文字体（Windows: SimSun/SimHei，macOS: Songti SC/STHeiti）
3. 图片文件默认放在 `pic/` 目录下
4. `report-uestc.bst` 和 `report-uestc.cls` 需要在同一目录

## 版权说明

本课程报告模板基于原UESTC学位论文模板修改，原模板采用LaTeX Project Public License (LPPL)。

- **原作者：** 王稳 (wangwen1192@outlook.com)
- **修改者：** XingGou516 (xingfeiceng@gmail.com)
- **修改内容：** 将学位论文模板简化为课程报告模板

- **原项目地址：** https://github.com/bdebye/thesisuestc.git
