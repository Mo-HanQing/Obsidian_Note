---
date: 2024-07-14
aliases:
  - LaTex基本语法
tags:
  - LaTex
---

- 命令格式：
	- `\命令名{参数}`
- 文档类型：
	- `\documentclass{option}`
	- `option`：
		- `article`（普通文章）
		- `beamer`（幻灯片）
		- . . .
- 简体中文与英文混排：
	- `\documentclass[UTF8]{ctexart}`

- 示例

```LaTex
\documentclass[UTF8]{ctexart}

\usepackage{graphicx} %导入插入图片包

\title{文章标题}
\author{作者名字}
\date{\today} 	 %修改日期 \today 自动设置为当前日期


\begin{document} %begin之前的内容相当于html的head

\maketitle 		 %显示head信息

\section{这是第一个章节}

Hey				 %begin和end之间的内容相当于html的body
\textbf{Hi}		 %bold font
\textit{Hello}	 %italic
\underline{MoHanQing}

here 			 %一个enter是空格 两个enter是换行

\section{这是第二个章节}
\subsection{这是一个子章节}
\subsubsection{这是一个三级章节}

\begin{figure}
	\centering 											%将图片居中显示
	\includegraphics[width=0.5\textwidth]{reading-book} %引入图片并设置尺寸
	\caption{年轻人，你渴望力量吗？} 					   %设置图片标题
\end{figure}

\begin{itemize}  	%无序列表
	\item 列表项1
	\item 列表项2
\end{itemize}

\begin{enumerate} 	%有序列表
	\item 列表项1
	\item 列表项2
\end{enumerate}

$ E=mc^2 $ %		%行内公式

\begin{equation}	%独占一行
	E=mc^2
\end{equation}

\[E=mc^2\]			%独占一行

\begin{equation}
	d={k\varphi(n)=1}\over e
\end{equation}

\begin{table}
\center
\begin{tabular}{|p{2cm}|c|c|}	%表格 三列 "c"居中对齐 "|"添加竖直边框 "p"列宽
	\hline					%水平方向边框
	单元格1 & 单元格2 & 单元格3 \\
	\hline\hline			%双横线
	单元格4 & 单元格5 & 单元格6 \\
	\hline
	单元格7 & 单元格8 & 单元格9 \\
	\hline
\end{tabular}
\caption{表格标题}
\end{table}

\end{document}	  
```