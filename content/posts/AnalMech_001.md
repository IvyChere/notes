+++
date = '2026-04-20T23:51:43+08:00'
draft = false
math = true
title = '分析力学 001'
tags = ['物理', '分析力学']
categories = ['物理']
description = "从牛顿力学出发..."
summary = "从牛顿第二定律到拉格朗日方程"
+++

### 1. 牛顿第二定律

在牛顿力学的视角下，质点的运动规律都服从一个二阶微分方程

$$
\mathbf{F}=\mathrm{m}\mathbf{\ddot{x}}
$$

对于不同的力， $\mathbf{F}$ 的形式有所不同。但是只要代入求解上述的微分方程，再加上 $\textbf{x} $与 $\mathbf{\ddot{x}}$ 的初值条件，我们就可以得到这一个质点的运动方程$\mathbf{x} = \mathbf{x}(\mathrm{t})$ .

看起来，牛顿第二定律似乎足够我们解决大多数的动力学问题了. 但是对于具体的物理情景而言，情况似乎要复杂得多.

#### 1.1 物理坐标$(x, y)$下的单摆运动

例如，我们考虑匀重力场$\mathbf{g}$下一个摆长为$l$单摆的运动：

当它达到摆角$\theta$时，受到绳子的约束力为$\mathbf{T}$. 

由牛顿第二定律，在$x$轴与$y$轴方向上：

$$
\mathrm{T} \sin \theta = - \mathrm{m} \mathrm{\ddot{x}} \\
\mathrm{mg} - \mathrm{T} \cos \theta =\mathrm{m} \mathrm{\ddot{y}} 
$$

消去$\mathrm{T}$得到：

$$
\mathrm{\ddot{x}} + (\mathrm{\ddot{y}-g)\frac{x} {y}}= 0 \Rightarrow \mathrm{ \ddot{x} y + x(\ddot{y} - g) = 0}
$$

不幸的是，在这样的情形下，仅凭借牛顿第二定律无法帮助我们得到单摆的运动方程. 原因是显而易见的：在这个情景下，质点不是在整个空间内不受束缚地自由运动. 它的运动受到了几何上的**约束**$\mathrm{x^2+y^2} = l^2$，即摆绳不可自由伸长. 只有联立这两个方程，才能最终解出单摆的运动方程. 

对约束方程求二次导数：

$$
\mathrm{ x\dot{x} + y\dot{y} = 0} \Rightarrow \mathrm{\dot{y} = -\frac{x}{y} \dot{x}}\\
\mathrm{ \dot{x}^2 + x \ddot{x} + \dot{y}^2 + y \ddot{y} = 0 }
$$

消去$\mathrm{y, \dot{y}, \ddot{y}}$得到：

$$
\mathrm{\ddot{x} + \frac{x}{L^2 - x^2} \dot{x}^2 + \frac{g}{L^2} x \sqrt{L^2 - x^2} = 0}
$$

同理可得到$\mathrm{y}$分量的运动方程. 

#### 1.2 传统方法的不足

到这里，我们可以发现传统的牛顿第二定律在描述质点运动时的不足：

- 牛顿第二定律是矢量定律，必须要考虑各个分量上的运动。而由于约束的存在，某些分量上的运动又不是互相独立的
- 在物理坐标$(x, y)$下，哪怕对于某些简单的运动，其运动方程也极其复杂

这些问题可以归结为：**我们能否找到一组相互独立的坐标$(q^1, q^2)$，使得我们可以不考虑约束的存在，而直接利用牛顿第二定律求解运动方程？**

幸运的是，这样的坐标是存在的. 

容易发现，在极坐标系下，单摆的位置可以由半径与摆角$(\rho, \theta)$这一对坐标描述，而由于几何约束，$\rho \equiv l$. 因此，我们只需要考虑$\theta$方向的运动即可. 此时，由极坐标下的牛顿第二定律：$\mathrm{F}_{\theta} = \mathrm{m(\rho \ddot{\theta} + 2 \dot{\rho}\dot{\theta})}$可以得出：

$$
\mathrm{mg \sin \theta} = - \mathrm{m}l\ddot{\theta} \Rightarrow \ddot{\theta} + \frac{\mathrm{g}}{l} \sin \theta
$$


