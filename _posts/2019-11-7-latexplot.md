---
layout: post
title: "LaTeX 作图方法简介"
tagline: "简单介绍 2 种 LaTeX 作图方法..."
#categories: 
#author: ""
#meta: ""
---
在使用 [$$\LaTeX$$](https://www.latex-project.org) 做笔记的时候，我们不免要画一些简单的示意图。这里简单介绍两种作图方式，可以很方便的画出简洁而美观的示意图。

### **TikZ 宏包**

<hr>

在导言区添上 `\usepackage{tikz}` 后就可以使用 [**TikZ** ](http://www.texample.net/tikz/) 宏包了。

画图的代码也很简单，我给出 2 个简单的例子，大家对照代码注释和生成的图看一看就可以了。

1. 坐标系：

	``` latex
	\begin{figure}[ht]
	
	  \centering
	  \label{fg:1}
	  
	  \begin{tikzpicture}[scale=0.9]
	    \draw[step=1,color=gray!40] (-4, -4) grid (4, 4); % 网格 help lines
	    	
	    \coordinate (O) at (0, 0);
	    \fill (0, 0) circle (3pt); % 画点
	    \node[below left] at (O) {$O$};
	    \draw[thick, -stealth] (-5, 0) -- (5, 0);
	    \draw[thick, -stealth] (0, -5) -- (0, 5);
	    \node[below] at (5,0) {$x$};
	    \node[left] at (0,5) {$y$};
	
	    \fill[red] (0,0)--(-1,2)--(-2,0); % 填充颜色
	
	    \draw[color=gray!40] (0,0) circle (2); % (0, 0)代表圆心坐标， 后面 (2) 代表半径
	    \draw[thick, color=red] (2,0) arc (0:45:2);	
	    % (2, 0)弧的起点坐标，(0:45:2)分别代表始末角度和圆的半径
			
	    \draw[color=gray!40] (0,0) ellipse (2 and 1); % 代表半长轴和半短轴
	    \draw[thick, color=green] (2,0) arc (0:90:2 and 1);
	
	    \draw[thick, blue] (-4,1) .. controls (-3,1.4) and (-2,1.7) .. (-1,4); 
	    % 4个点坐标画贝塞尔曲线
	
	    \coordinate (A) at (3, 3);
	    \draw[thick, dotted, -latex] (0, 0) -- (A);
	    \node[above right] at (A) {$A$};
	
	    \coordinate (B) at (3, -3);
	    \draw[thick, dashed, ->] (0, 0) -- (B);
	    \node[above right] at (B) {$B$};
	
	    \node at (-2.5, -3) {$Hello, world!$};
	  \end{tikzpicture}
	  
	  \caption{TikZ creating graphics.}
	  
	\end{figure}
	```
	将其编译后生成的图像：
	<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/tikz1.png" alt="TikZ" width="500"/>

2. 长方体：

	``` latex
	\begin{figure}[ht]
	  
	  \centering
	  \label{fg:2}
	
	  \begin{tikzpicture}
	    % 8个顶点
	    \coordinate (A) at (0,0) node[below left] at (A) {$A$};
	    \coordinate (B) at (5,0) node[below right] at (B) {$B$};
	    \coordinate (C) at (5,3) node[right] at (C) {$C$};
	    \coordinate (D) at (0,3) node[left] at (D) {$D$};
	
	    \coordinate (E) at (1,1) node[left] at (E) {$E$};
	    \coordinate (F) at (6,1) node[right] at (F) {$F$};
	    \coordinate (G) at (6,4) node[above right] at (G) {$G$};
	    \coordinate (H) at (1,4) node[above left] at (H) {$H$};
	
	    \fill (3,2) circle (1.5pt) node[below] at (3,2) {$O$};  % 原点
			
	    % 12条边
	    \draw (A) rectangle (C);
	    \draw[dashed] (E)--(F);
	    \draw (F)--(G)--(H);
	    \draw[dashed] (H)--(E);
	    \draw[dashed] (A)--(E);
	    \draw (B)--(F);
	    \draw (C)--(G);
	    \draw (D)--(H);
	
	    % 对角线
	    \draw[dashed] (A)--(G);
	    \draw[dashed] (B)--(H);
	    \draw[dashed] (E)--(C);
	    \draw[dashed] (D)--(F);
	
	  \end{tikzpicture}
	
	  \caption{A cuboid.}
	
	\end{figure}
	```
	将其编译后生成的图像和教科书上几乎一模一样：
	<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/tikz2.png" alt="TikZ" width="400"/>

### **Inkscape 作图**

<hr>

[**Inkscape**](http://www.inkscape.org) 是一款跨平台的开源矢量图形编辑软件，和专业的 [**Adobe Illustrator (AI)**](https://www.adobe.com/products/illustrator.html) 相比，功能虽然少了一些，但是更适合为 $$\LaTeX$$ 作简图。

1. 在 **Inkscape** 中绘制好矢量图，将需要的公式用 $$\LaTeX$$ 表达式写出来，比如
`$\int_0^\infty x\mathrm{d}x=0$`，保存图像时选择 **PDF** 格式，就会跳出一个选项框，其中的 `文字输出选项` 选择 `忽略 PDF 中的文本并创建 LaTeX 文件`，就会生成 `xxx.pdf` 和 `xxx.pdf_tex` 两个文件。

	<center class="half">
	    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/inkscape1.png" alt="Illustration of the colloid/swimmer system" title="Inkscape" width="300"/>

	<br><br>

2. 在 `tex` 文件的导言区加入：

	``` latex
	\usepackage{import}
	\usepackage{xifthen}
	\usepackage{pdfpages}
	\usepackage{transparent}
	
	\newcommand{\incfig}[1]{
	    \def\svgwidth{0.7\columnwidth}
	    \import{./figures/}{#1.pdf_tex}
	}
	``` 
	其中倒数第三行的图像宽度 0.7 可以按需求自行修改。

3. 在 `tex` 文件的正文区加入：

	``` latex
	\begin{figure}[ht]
	    \centering
	    \incfig{xxx}
	    \caption{Inkscape creating graphics.}
	    \label{fg:1}
	\end{figure}
	```
	其中 `xxx` 是图像文件名 (不带后缀) ，编译后图像文件中的 $$\LaTeX$$ 表达式就会自动被渲染在图像上，如下图所示：
	<center class="half">
    <img src="https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/inkscape2.png" alt="Illustration of the colloid/swimmer system" title="Inkscape" width="400"/>

### **结语**

<hr>

从此我们就可以用 $$\LaTeX$$ 画出简洁而美观的示意图了！🎉 🎉 🎉 

&ensp;

[<b><u>Go to the Home Page</u></b>]({{ site.url }}{{ site.baseurl }})

&ensp;

<center class="half">
<font color="#26975b"><b>Sponsor the author </b></font><font color="#08a2e4"><b>if you like the contents!</b></font><br/><br/>
</center>

<center class="half">
    <img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/WechatPay.png" width="251" style="margin-right:10px;margin-left:10px"/><img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/AliPay.png" width="250" style="margin-right:10px;margin-left:10px"/>
</center>

&ensp;