---
date: 2024-07-15
aliases:
  - LaTex数学语法
tags:
  - LaTex
  - Math
---
>希腊字母
$$
\delta,\lambda, \\
\Delta,\Lambda, \\
\Alpha,\Bata,   \\
\phi,\varphi,   \\
\epsilon,\varepsilon, \\
$$
![[Snipaste_2024-07-15_11-05-09 1.png]]
>上下标
$$
a^2,a_1, \\
x^{y+z},P_{i,j}, \\
$$
- 英文字母只有在表示变量(或单一字符的函数名称,如f(x))时才可使用斜体,其余情况都应使用罗马体(直立体) 。
$$
x_i,\\
x_{\rm i},x_{\text i}, \\
\rm{A B},\text{A B},   \\
\rm A B,\text A B,     \\
{\rm A} B  \\
\text{e},\text{i j}
$$
>分式与根式
$$
\frac{1}{2},\frac 1 2,\\
\frac 1 {x+y}, \\
\frac {\dfrac 1 x +1}{y+1}
$$
$$
\sqrt 2,\sqrt{x+y},\sqrt[3]x
$$
>普通运算符
$$
+-,\\
\times,\cdot,\div,\\
\pm,\mp,\\
><,\ge,\le,\gg,\ll,\ne,\approx,\equiv,\\
\cap,\cup,\in,\notin,\subset,\subseteq,\subsetneq,\\varnothing,\\
\forall,\exists,\nexists,\\
\because,\therefore,\\
\mathbb R,\R,\Q,\N,\Z_+
\mathcal F,\mathscr F
$$

$$
\cdots,\vdots,\ddots
$$$$
\infty,\partial,\nabla,\propto,\degree
$$
$$
\sin x,\sec x,\cosh x,\\
\log_2 x,\ln x,\lg x, \\
\lim_{x \to 0} \frac {x}{\sin x}, \lim\limits_{x \to 0} \frac {x}{\sin x},\\
\max x
$$
>大型运算符
$$
\sum,\prod,\\
\sum_i,\sum_{i=0}^N,\\
\frac{\sum_{i+1}^n x_i}{\prod_{i=1}^n x_i},\\
\frac{\sum\limits_{i+1}^n x_i}{\prod\limits_{i=1}^n x_i},\\

$$
$$
\int,\iint,\iiint,\oint,\oiint,\\
\int_{-\infty}^0 f(x)\,\text d x
$$
$$
a\, a,\\
a\ a, \\
a\quad a, \\
a\qquad a \\
$$
>标注符号

$$
\vec x,\overrightarrow {AB},\\
\bar x,\overline {AB}
$$![[Snipaste_2024-07-16_14-21-57.png]]

>箭头

$$
\leftarrow,\Rightarrow,\Leftrightarrow,\longleftarrow
$$
![[Snipaste_2024-07-16_14-24-47.png]]

>括号与定界符

$$
([])\{ \},\\
\lceil,\rceil,\lfloor,\rfloor,||, \\
\left(0,\frac 1 a\right], \\
\left.\frac {\partial f}{\partial x}\right|_{x=0}
$$
>多行公式

$$
\begin{align}
a&=b+c+d\\
&=e+f
\end{align}
$$
>大括号

$$
f(x)=

\begin{cases}

\sin x, & -\pi \le x \le \pi \\
0,  & \text{其他}

\end{cases}
$$
>矩阵

$$
\begin{matrix}

a & b & \cdots & c \\
\vdots & \vdots & \ddots & \vdots \\
e & f & \cdots & g

\end{matrix}
$$
$$
\begin{bmatrix}

a & b & \cdots & c \\
\vdots & \vdots & \ddots & \vdots \\
e & f & \cdots & g

\end{bmatrix}
$$
$$
\begin{pmatrix}

a & b & \cdots & c \\
\vdots & \vdots & \ddots & \vdots \\
e & f & \cdots & g

\end{pmatrix}
$$$$
\begin{vmatrix}

a & b & \cdots & c \\
\vdots & \vdots & \ddots & \vdots \\
e & f & \cdots & g

\end{vmatrix}
$$
$$
\mathbf A,\mathbf B^{\rm T}
$$