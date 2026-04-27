+++
date = '2026-04-22T20:04:37+08:00'
draft = false
math = true
title = '分析力学 002'
tags = ['物理', '分析力学']
categories = ['分析力学']
description = "泛函、变分法与最小作用量原理"
summary = "泛函、变分法与最小作用量原理"
+++

Tip: 分析力学的往期内容戳[这里](https://blogs.starspress.org/tags/%E5%88%86%E6%9E%90%E5%8A%9B%E5%AD%A6/)

### 0. 从最速降线问题讲起......

1696年6月，著名数学家$Johann \ Bernoulli$在一份科学期刊上发布了这样一个问题：

> 在铅直平面上两点A，B之间要连一条曲线，使得不受摩擦的质点在重力的作用下由静止开始沿这条曲线由A运动到B所需要的时间最少？

这个问题被称为最速降线问题. 我们不妨使用现代的数学方法来研究一下这个问题. 

以质点的初始位置为原点，在平面中建立平面直角坐标系$xOy$，$x$轴以曲线延伸方向为正方向，$y$轴以竖直向下为正方向. 设运动起点、终点分别为$(0, 0), (x_0, y_0)$

由机械能守恒定律，有：

$$
mgy = \frac{1}{2}mv^2 \Rightarrow v = \frac{\mathrm ds}{\mathrm d t}= \sqrt{2gy}
$$

其中

$$
\mathrm d s = \sqrt{1 + \left(y'\right)^2} \mathrm d x
$$

代入得：

$$
\mathrm d t = \sqrt{\frac{1 + \left(y'\right)^2}{2gy}} \mathrm d x \Rightarrow
$$

$$
t(y, y') = \int_{0}^{x_0} \sqrt{\frac{1 + \left(y'\right)^2}{2gy}} \mathrm d x
$$

我们遇到一个很尴尬的问题：求解这个问题，相当于要找到一个函数$y = y(x)$，使得$t(x, y, y')$取得最小值. 这与我们从前见过的问题截然不同. 我们以往讨论的问题中，函数的值取决于函数自变量所取的值；而在这里，影响$t$大小的已不再是某一个变量的取值，而是某个函数$y = y(x)$的具体形式. 因此，我们需要一个新的数学工具来帮助我们处理这个问题. 

### 1. 泛函与变分法

#### 1.1 泛函

设一个集合$\mathcal{F} = \left\{  f \mid f : X \rightarrow Y \right\}$（$X$与$Y$为两个数集），存在映射$S:\mathcal{F} \rightarrow \mathbb{C}$. 我们称$S$为一个**泛函**. 这是数学家们讲的怪话，而我们只需要知道一件事即可：**泛函是作用在函数上的“函数”**.

当然，泛函在数学上说不定有什么更加高深的定义方法. 但是这是数学家的工作，我们可以不用管他，只挑选我们感兴趣的那一部分内容就行. 事实上，在物理学中，我们最常讨论的泛函都具有以下形式：

$$
S = \int_{t_1}^{t_2} L(x, y, y', y'', \dots, y^{(n)}) \mathrm d x
$$

其中$y = y(x)$. 我们称泛函$L = L(x, y, y', y'', \dots, y^{(n)})$为泛函$S$的被积函数[^1].

因此上面的问题就变成了：已知这样一个泛函$S[y]$，我们应该如何求出其极值，以及取到极值时函数$y = y(x)$的形式？

#### 1.2 变分法

我们来（用物理一点的方法）回忆一下我们是如何求解一元函数极值的必要条件的：

我们有一个性质足够好的一元函数$y = y(x)$，它的极值点为$x = x_0$. 我们在它的极值点左右取一个很小的区间，并想象有一个质点从区间的一端移向另一端. 我们很容易想到，在极值点处，质点的速度完全与$x$轴平行，换言之，质点在极值点处的运动不会造成函数值$y$的增加. 用数学家的车轱辘话讲就是

$$
\left. \frac{\mathrm d y}{\mathrm d x} \right|_{x=x_0} = 0
$$

非常美妙的起点. 那我们能否讲这个方法用于泛函$S$上呢？能的兄弟能的：如果我对泛函$S$取一个微小的变化$\delta S$，再令$\delta S = 0$不就成了吗. 

但是我们发现一个问题：由于泛函$S$里不止包含了自变量$x$，还包含了函数$y$及其导数. 因此，我们必须要想办法刻画函数$y$的变化. 

一个很自然的想法是：我取$x$的一个微小变化$\mathrm d x$，这样$y$也会相应有一个$\mathrm d y$的变化. 只不过这个方法并不可行，因为$\mathrm d y$描述的只是函数$y = y(x)$的**值**的微小变化，而真正影响$S[y]$的是函数$y = y(x)$的具体**形式**. [^2]

那成，我们就让$y = y(x)$的形式发生一点微小的变化，体现在几何上就是将$y = y(x)$的图像“拨动”一点点，得到一个新的函数$\tilde{y}$.

![图源：《经典力学》，高显编著，科学出版社出版](/images/Blog2.1.png "图源：《经典力学》，高显编著，科学出版社出版")
我们与函数的微分相似，我们定义

$$
\delta y = \tilde {y} - y
$$

为函数$y = y(x)$的**变分**，我们很容易得到变分运算时线性的. 同样地可以定义泛函$S$的变分：

$$
\delta S = S[y + \delta y] - S[y]
$$

或者写成

$$
\delta S = \int_{t_1}^{t_2}\left( L[y + \delta y] - L[y] \right)\mathrm d x = \int_{t_1}^{t_2} \delta L \mathrm d x

$$

我们仿照函数的导数，设$\delta L = \dfrac{\delta S}{\delta y}\delta y$，我们称形式上的记号$\dfrac{\delta S}{\delta y}$为$S$的 **“泛函导数”**

这样我们只需要让$\dfrac{\delta S}{\delta y}$即可！可喜可贺可口可乐......

...等等，这$\dfrac{\delta S}{\delta y}$到底是一泡啥玩意啊......

当我们对这一坨数学玩意感到手足无措的时候，我们可以发挥一下我们物理学家的传统艺能——联想. （虽然数学家们会感到很生气，但是我们不去管他）

对于一元函数，我们可以对它做泰勒展开. 哪对一个泛函凭什么就不行？说干就干.

我们稍微“拨动”一下泛函$S$，得到$\tilde{S} = S[y + \epsilon\ \delta y]$，把它对$\epsilon \ \delta y$展开：

$$
S[y + \epsilon \ \delta y] = S[y] + \epsilon \ \delta S + \frac{1}{2!} \epsilon^2 \ \delta^2 S + \dots
$$

从另一方面，我们还可以把$\epsilon$视为一个变量，在$\epsilon = 0$处对它进行展开：

$$
S[y + \epsilon \ \delta y] = S[y] + \epsilon \left. \left( \frac{\mathrm d \tilde S}{\mathrm d \epsilon} \right) \right|_{\epsilon = 0} + \frac{1}{2!} \epsilon^2 \left. \left( \frac{\mathrm d^2 \tilde S}{\mathrm d \epsilon^2} \right) \right|_{\epsilon = 0} + \dots
$$

对比一下各项系数，巧了，我们可以得到：

$$
\delta S = \left. \left( \frac{\mathrm d \tilde S}{\mathrm d \epsilon} \right) \right|_{\epsilon = 0} =\int_{t_1}^{t_2} \left. \frac{\mathrm d}{\mathrm d \epsilon}L(x, y+\epsilon \delta y,y' + \epsilon \delta y', \dots )\right|_{\epsilon = 0} \mathrm d x = \int_{t_1}^{t_2}\mathrm d x \left( \frac{\partial L}{\partial y}\delta  y + \frac{\partial L}{\partial y'}\delta  y'+ \dots \right)
$$

所以我们就有

$$
\delta L = \frac{\partial L}{\partial y}\delta  y + \frac{\partial L}{\partial y'}\delta  y'+ \dots + \frac{\partial L}{\partial y^{(n)}}\mathrm d y^{(n)}
$$

由于$x$是一个变量，它的变分$\delta x = 0$（我们没办法对一个变量进行形式上的变化，对吧）. 因此，$L$的变分还可以写成以下的形式：

$$
\delta L = \frac{\partial L}{\partial x}\delta  x + \frac{\partial L}{\partial y}\delta  y + \frac{\partial L}{\partial y'}\delta  y'+ \dots + \frac{\partial L}{\partial y^{(n)}}\mathrm d y^{(n)}
$$

这和$L$的全微分$\mathrm d L = \dfrac{\partial L}{\partial x}\mathrm d  x + \dfrac{\partial L}{\partial y}\mathrm d  y + \dfrac{\partial L}{\partial y'}\mathrm d  y'+ \dots + \dfrac{\partial L}{\partial y^{(n)}}\mathrm d y^{(n)}$有着惊人的结构一致性. 这就给了我们一种计算泛函变分的方法.

我们考虑一种简单的情形：对于泛函

$$
S = \int_{t_1}^{t_2}\mathrm dx \ L(x, y, y')
$$

其变分

$$
\delta S = \int_{t_1}^{t_2}\mathrm dx \left( \frac{\partial L}{\partial y}\delta  y + \frac{\partial L}{\partial y'}\delta  y' \right)
$$

而由下图可知：变分的导数等于导数的变分

![](/images/Blog2.2.png)

因此，第二项我们可以利用分部积分法写成

$$
\frac{\partial L}{\partial y'}\delta  y' = \frac{\partial L}{\partial y'} \frac{\mathrm d}{\mathrm dx}(\delta y) = \frac{\mathrm d}{\mathrm dx}\left( \frac{\partial L}{\partial y'}\delta y \right) - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right)\delta y
$$

回代：

$$
\delta S = \int_{t_1}^{t_2}\mathrm dx \left( \frac{\partial L}{\partial y}\delta  y + \frac{\partial L}{\partial y'}\delta  y' \right) 
$$

$$
=  \int_{t_1}^{t_2}\mathrm dx \left[ \frac{\mathrm d}{\mathrm dx}\left( \frac{\partial L}{\partial y'}\delta y \right) + \frac{\partial L}{\partial y}\delta  y - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right)\delta y\right]
$$

$$
= \left. \left( \frac{\partial L}{\partial y'}\delta y \right)\right|_{t_1}^{t_2} + \int_{t_1}^{t_2}\mathrm dx \left[ \frac{\partial L}{\partial y} - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right)\right]\delta  y
$$

我们称$\left. \left( \dfrac{\partial L}{\partial y'}\delta y \right)\right|_{t_1}^{t_2}$为泛函$S$的**边界项**，称$\dfrac{\partial L}{\partial y'}\delta y$为被积函数的**全导数项**. 当泛函$S_1$与$S_2$仅相差边界项时，或者被积函数$L_1$与$L_2$仅相差全导数项时，我们记为$S_1 \simeq S_2, L_1 \simeq L_2$.

继续.

在最速降线问题中，积分上下限是确定的. 如果对于这样一个泛函，其积分限$t_1, t_2$确定，即$\delta t_1 = \delta t_2 = 0$. 那么S的边界项$\left. \left( \dfrac{\partial L}{\partial y'}\delta y \right)\right|_{t_1}^{t_2} = 0$. 此时

$$
\delta S = \int_{t_1}^{t_2}\mathrm dx \left[ \frac{\partial L}{\partial y} - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right)\right]\delta  y = \int_{t_1}^{t_2} \mathrm dx \frac{\delta S}{\delta y}\delta y 
$$

即

$$
\frac{\delta S}{\delta y} = \frac{\partial L}{\partial y} - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right)
$$

泛函$S$取极值时，$\dfrac{\delta S}{\delta y} = 0$，即

$$
\frac{\partial L}{\partial y} - \frac{\mathrm d}{\mathrm dx} \left( \frac{\partial L}{\partial y'} \right) = 0
$$

称为$Euler-Lagrange$方程. 通过这个方程，我们可以求解出$S$取极值时，$y = y(x)$的表达式.



### 2. 最小作用量原理

这个式子我们越看越眼熟...

在[上一篇](https://blogs.starspress.org/posts/analmech_001/#213-%E6%96%B9%E7%A8%8B)，我们还介绍过另一个$Euler-Lagrange$方程

$$
\frac{\mathrm d}{\mathrm d t}(\frac{\partial L}{\partial \dot q^\alpha}) - \frac{\partial L}{\partial q^\alpha} =0
$$

它们具有极其相似的结构. 这让我们不禁想象：我们如果构造这样一个泛函

$$
S = \int_{t_1}^{t_2} \mathrm dt \ L(t, \mathbf q, \mathbf {\dot q})
$$

当物理系统的初末状态$t_1, t_2$确定时，若泛函$S$取到了极值，那么便可自然得出分析力学中的$Euler-Lagrange$方程.

也就是说，当物理系统的初末状态确定时，物理系统的演化路径一定可以使得这样的泛函$S$取到极值.

我们称这样的泛函$S$为**作用量**，这样的原理称作**最小作用量原理**[^3].

最小作用量原理不仅仅适用于牛顿力学与确定的初末状态. 事实上，任何物理理论的演化均服从最小作用量原理.





[^1]: 你别管为什么物理学家要管一个**泛函**叫被积**函数**，问就是我们乐意.（其实是因为我学的那个版本就这么叫）

[^2]: 因为我们讨论的$S$是一个定积分式，要遍历积分区间内所有$x$的取值. 因此讨论某一个$\mathrm d x$带来的影响是没有意义的. 

[^3]: 这个时候，作用量$S$可能处于极大值、极小值或者鞍点值. 因此，这个原理称为**稳恒作用量原理**可能更为合适.
