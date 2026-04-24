+++
date = '2026-04-22T20:04:37+08:00'
draft = true
math = true
title = '分析力学 002'
tags = ['物理', '分析力学']
categories = ['物理']
description = "泛函、变分法与最小作用量原理"
summary = "泛函、变分法与最小作用量原理"
+++

### 0. 从最速降线问题讲起......

1696年6月，著名数学家$Johann \ Bernoulli$在一份科学期刊上发布了这样一个问题：

> 在铅直平面上两点A，B之间要连一条曲线，使得不受摩擦的质点在重力的作用下由静止开始沿这条曲线由A运动到B所需要的时间最少？

我们不妨使用现代的数学方法来研究一下这个问题. 

以质点的初始位置为原点，在平面中建立平面直角坐标系$xOy$，$x$轴以曲线延伸方向为正方向，$y$轴以竖直向下为正方向. 设运动起点、终点分别为$(0, 0), (x_0, y_0)$

由机械能守恒定律，有：

$$
mgy = \frac{1}{2}mv^2 \Rightarrow v = \frac{\mathrm ds}{\mathrm d t}= \sqrt{2gy}
$$

其中

$$
\mathrm d s = \sqrt{1 + (y')^2} \mathrm d x
$$

代入得：

$$
\mathrm d t = \sqrt{\frac{1 + (y')^2}{2gy}} \mathrm d x \Rightarrow
$$

$$
t(x, y, y') = \int_{0}^{x_0} \sqrt{\frac{1 + (y')^2}{2gy}} \mathrm d x
$$

我们遇到一个很尴尬的问题：求解这个问题，相当于要找到一个函数$y = y(x)$，使得$t(x, y, y')$取得最小值. 这与我们从前见过的问题截然不同. 




