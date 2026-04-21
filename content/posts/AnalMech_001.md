+++
date = '2026-04-20T23:51:43+08:00'
draft = false
math = true
title = '分析力学 001 - 从牛顿力学出发'
tags = ['物理', '分析力学']
categories = ['物理']
+++

## 一、 牛顿第二定律

在牛顿力学的视角下，质点的运动规律都服从一个二阶微分方程

$$
\mathbf{F}=\mathrm{m}\mathbf{\ddot{x}}
$$

对于不同的力， $\mathbf{F}$ 的形式有所不同。但是只要代入求解上述的微分方程，再加上 $\textbf{x} $与 $\mathbf{\ddot{x}}$ 的初值条件，我们就可以得到这一个质点的运动方程$\mathbf{x} = \mathbf{x}(\mathrm{t})$ .

看起来，牛顿第二定律似乎足够我们解决大多数的动力学问题了. 但是对于具体的物理情景而言，情况似乎要复杂得多.



例如，我们考虑匀重力场$\mathbf{g}$下一个摆长为$l$单摆的运动：

当它达到摆角$\theta$时，受到绳子的约束力为$\mathbf{T}$. 

由牛顿第二定律，在$x$轴与$y$轴方向上：

$$
\mathrm{T} \sin \theta = - \mathrm{m} \mathrm{\ddot{x}} \\
\mathrm{T} \cos \theta - \mathrm{mg}=\mathrm{m} \mathrm{\ddot{y}} 
$$

消去$\mathrm{T}$得到：

$$
\mathrm{\ddot{x}} + (\mathrm{\ddot{y}+g})\tan \theta = 0
$$

不幸的是，在这样的情形下，仅凭借牛顿第二定律无法帮助我们得到单摆的运动方程. 原因是显而易见的：在这个情景下，质点不是在整个空间内不受束缚地自由运动. 它的运动受到了几何上的**约束**，即摆绳不可自由伸长。

$$
\mathrm{x^2+y^2} = l^2
$$

对其求二阶导数得：

$$
\mathrm{x \ddot{x} +(\dot{x})^2}+\mathrm{y \ddot{y} +(\dot{y})^2} = 0
$$




