+++
date = '2026-04-27T20:18:46+08:00'
draft = false
math = true
title = '分析力学 003'
tags = ['物理', '分析力学']
categories = ['分析力学']
description = "从拉格朗日到哈密顿"
summary = "从拉格朗日到哈密顿"
+++

Tip: 分析力学的往期内容戳[这里](https://blogs.starspress.org/categories/%E5%88%86%E6%9E%90%E5%8A%9B%E5%AD%A6/)

### 1. 能量函数与广义能量守恒

我们讨论一下系统拉格朗日量$L = L(t, \mathbf q, \mathbf{\dot q})$随时间的演化. 

$$
\frac{\mathrm d L}{\mathrm dt} = \frac{\partial L}{\partial t} + \frac{\partial L}{\partial q^{\alpha}}\dot{q^{\alpha}} + \frac{\partial L}{\partial \dot{q}^{\alpha}}\ddot{q^{\alpha}}
$$

利用分部积分法：

$$
\frac{\partial L}{\partial \dot{q}^{\alpha}}\ddot{q^{\alpha}} = \frac{\mathrm d }{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} \right) - \frac{\mathrm d }{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}} \right)\dot{q^{\alpha}} 
$$

回代：

$$
\frac{\mathrm d L}{\mathrm dt} = \frac{\partial L}{\partial t} + \frac{\partial L}{\partial q^{\alpha}}\dot{q^{\alpha}} + \frac{\mathrm d }{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} \right) - \frac{\mathrm d }{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}} \right)\dot{q^{\alpha}}
$$

整理一下可以得到：

$$
\frac{\mathrm d}{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} - L \right) + \left[ \underbrace{ \frac{\mathrm d}{\mathrm d t}\left(\frac{\partial L}{\partial \dot q^\alpha}\right) - \frac{\partial L}{\partial q^\alpha} }_{0} \right] \dot{q^{\alpha}} + \frac{\partial L}{\partial t} = 0
$$

即

$$
\frac{\mathrm d}{\mathrm dt} \left( \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} - L \right)  = - \frac{\partial L}{\partial t}
$$

我们定义$h(t, \mathbf q, \mathbf{\dot q}) = \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} - L$. 在采用物理坐标$(x, y)$的牛顿力学中：$L = \dfrac{1}{2}m \mathbf{\dot x}^2 - V(\mathbf x)$，代入表达式得$h(t, \mathbf x, \mathbf{\dot x}) = \dfrac{1}{2}m \mathbf{\dot x}^2 + V(\mathbf x)$，为系统的总能量. 因此，我们称$h(t, \mathbf q, \mathbf{\dot q}) = \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} - L$为这个物理系统的**能量函数**. 

我们还会定义**共轭动量**$p_\alpha = \dfrac{\partial L}{\partial \dot{q}^{\alpha}}$，这个定义也是自然的，因为它在在采用物理坐标$(x, y)$的牛顿力学中会退化为$\mathbf p = m \mathbf{\dot x}$的形式. 此时，能量函数可以写成$h(t, \mathbf q, \mathbf{\dot q}) = p_\alpha \dot{q^{\alpha}} - L$. 

当系统的拉格朗日量不显含时间时，即$\dfrac{\partial L}{\partial t} = 0$时，我们有

$$
\frac{\mathrm dh}{\mathrm dt} = 0
$$

即$h$为一个常函数. 我们称之为**广义能量守恒**，称现在的物理系统是一个**保守系统**.

### 2. $Hamilton$力学

#### 2.1 $Lagrange$力学的不足

我们之前介绍过，我们可以利用拉格朗日量$L = L(t, \mathbf q, \mathbf{\dot q})$将系统的演化归结为一个关于广义坐标的二阶微分方程

$$
\frac{\mathrm d}{\mathrm d t}\left(\frac{\partial L}{\partial \dot q^\alpha}\right) - \frac{\partial L}{\partial q^\alpha} = 0
$$

从而求出位形空间中系统的运动方程. 但是这个方法稍微有一点缺陷：我们知道，一个质点的运动由其广义坐标$\mathbf q$与广义速度$\mathbf{\dot q}$确定. 而在位形空间中，我们只能得到系统的广义坐标信息$\mathbf q$，而无法直接得到系统的广义速度$\mathbf{\dot q}$. 另一方面，如果我们将广义坐标与广义速度张成一个空间$(\mathbf q, \mathbf{\dot q})$，称为**速度相空间**，并试图在速度相空间中确定系统的演化时，我们又会发现，由于存在一个自然的约束$\dfrac{\mathrm d}{\mathrm dt}\mathbf q = \mathbf{\dot q}$，广义速度时刻要受到广义坐标的束缚. 因此速度相空间中并不是每一个点都是有意义的.[^1]

归根结底，出现这种问题是因为在$Lagrange$力学中，我们选取的参数$(\mathbf q, \mathbf{\dot q})$ 虽然相互独立，但是它们的地位并不是平等的. 我们不禁想问这样一个问题：我们能否找到一组合适且地位平等参数来描述物理系统的演化呢？



#### 2.2 $Legendre$变换

描述一个平面曲线需要哪些参数？

最自然的想法一定是：我们用一对坐标$(x, y)$来记录曲线上每一个点的位置，这一系列点组成的集合即为这条平面曲线. 用数学语言描述就是：曲线$\Gamma = \left\{ (x, y) \mid P(x, y) \right\}$，其中$P(x, y)$为坐标$(x, y)$之间的关系. 但是除此之外，我们还有另外一种方法. 

设想这样一个例子：一根刚性连杆的两端分别接在两个相互垂直的滑轨上. 连杆的两端可以在滑轨上自由滑动. 如左图. 

![](/images/Blog3.1.png)

很容易想象：连杆在滑动的过程中可以扫出一条曲线，且连杆时刻与这根曲线相切，如右图. 

这给我们提供了一个新的描述一根平面曲线的思路：因为切线包含了函数在切点附近的所有信息，因此我们可以用函数各点处的切线来描述这一根平面曲线. 而确定一根切线只需要两个参数：斜率$p$与负纵截距$I$. 或许我们可以通过这个方法，将原曲线由$y = f(x)$的形式（描述各点的坐标）改写成$I = f^*(p)$的形式（描述各点切线的斜率与负纵截距）.

我们可以尝试一下这个方法：已知函数$y = f(x)$，其在$x = x_0$处的切线为：

$$
y = f'(x_0)(x - x_0) + f(x_0) \Rightarrow y = f'(x_0)x + f(x_0)-f'(x_0)x_0
$$

其斜率$p_0 = f'(x_0)$，负纵截距$I_0 = f'(x_0)x_0 - f(x_0)$. 我们可以将$x_0$反解出来，得到$x_0 = x(p_0)$，再代入负纵截距的表达式，我们得到

$$
I_0 = p_0 x(p_0) - f(x(p_0))
$$

由于这个式子对曲线上所有点均成立，因此可以写成

$$
I = p x(p) - f(x(p))
$$

我们将其定义为曲线$y = f(x)$的$Legendre$变换.

当然，这种形式的$Legendre$变换有诸多的限制条件，例如$y = f(x)$必须为性质足够好的严格下凸函数. 但是这种形式的变换已经足够我们使用了. 



#### 2.3 $Hamilton$力学

##### 2.3.1 哈密顿量$Hamiltonian$

我们在想：我们能否通过$Legendre$变换，更换一组地位平等的参数，以描述物理系统的演化呢？

对于拉格朗日量$L = T - V$，其动能项是一个关于广义速度的二次型[^2]，而其势能项不包含广义速度. 因此，拉格朗日量是一个关于广义速度的严格下凸函数，符合$Lengendre$变换的使用条件.

因此，对于拉格朗日量$L = L(t, \mathbf q, \mathbf{\dot q})$，我们固定$t$与$\mathbf q$为一个定值，对$\mathbf{\dot q}$进行$Lengendre$变换，可以得到：

$$
H = \frac{\partial L}{\partial \dot{q}^{\alpha}} \dot{q}^{\alpha} - L(t, \mathbf q, \mathbf{\dot q})
$$

我们定义广义动量$p_\alpha = \dfrac{\partial L}{\partial \dot{q}^{\alpha}}$，那么上式可以写成

$$
H(t, \mathbf q, \mathbf p) = p_{\alpha} \dot{q}^{\alpha} - L(t, \mathbf q, \mathbf{\dot q})
$$

其中$\mathbf {\dot q} = \mathbf{\dot q}(\mathbf p)$为广义动量的函数. 

我们定义：$H(t, \mathbf q, \mathbf p) = p_{\alpha} \dot{q}^{\alpha} - L(t, \mathbf q, \mathbf{\dot q})$ 为物理系统的哈密顿量$Hamiltonian$.

我们发现，哈密顿量$H(t, \mathbf q, \mathbf p) = p_{\alpha} \dot{q}^{\alpha} - L(t, \mathbf q, \mathbf{\dot q})$与能量函数$h(t, \mathbf q, \mathbf{\dot q}) = \frac{\partial L}{\partial \dot{q}^{\alpha}}\dot{q^{\alpha}} - L$在形式上完全一致. 事实上，根据共轭动量的定义$p_\alpha = \dfrac{\partial L}{\partial \dot{q}^{\alpha}}$，原则上我们可以反解出$\dot q^\alpha = \dot q^\alpha (p_\alpha)$，再代回能量函数的表达式即可得到哈密顿量.

尽管哈密顿量在形式上含有广义速度，但是这里的广义速度其实是从广义动量的定义式反解出来的一个关于广义动量的函数. 如果你对此感到疑惑的话，我们可以尝试让哈密顿量对广义速度进行求导：

$$
\frac{\partial H}{\partial \dot q^\alpha} = p_\alpha - \underbrace{\frac{\partial L}{\partial \dot q ^\alpha}}_{=p_\alpha} = 0
$$

故哈密顿量中不直接包含广义速度.  从中我们也可以得出广义动量与广义速度相互独立，因为

$$
\frac{\partial H}{\partial \dot q^\alpha} = \frac{\partial H}{\partial p_\alpha} \cdot \frac{\partial p_\alpha}{\partial \dot q^\alpha} = 0
$$

其中$\dfrac{\partial H}{\partial p_\alpha} \neq 0$（因为哈密顿量显含广义动量），因此有$\dfrac{\partial p_\alpha}{\partial \dot q^\alpha} = 0$，即广义动量与广义速度相互独立. 这样就保证了广义坐标与广义动量地位的平等性.

我们将一个物理系统的广义坐标与广义动量张成的空间$(\mathbf q, \mathbf p)$称作**动量相空间**，简称**相空间**. 由于参数$(\mathbf q, \mathbf p)$与参数$(\mathbf q, \mathbf{\dot q})$的效果完全一致，均可描述物理系统的状态，而前者两个参数的地位又是平等的. 因此，**我们便可以用相空间中的一个点唯一地确定一个物理系统的状态**.

当$L = T - V$时，我们可以得到$H = T + V$[^3].



##### 2.3.2 $Hamilton$正则运动方程

我们知道，拉格朗日量的演化服从$Euler-Lagrange$方程. 那么哈密顿量的演化又满足什么方程呢？我们不妨将哈密顿量对时间$t$，广义坐标$\mathbf q$与广义动量$\mathbf p$求个偏导试试.

对时间求偏导：

$$
\frac{\partial H}{\partial t} = - \frac{\partial L}{\partial t}
$$

对广义坐标求偏导：

$$
\frac{\partial H}{\partial q^\alpha} = p_\alpha \frac{\partial \dot q^\alpha}{\partial q^\alpha} + \frac{\partial p_\alpha}{\partial q^\alpha}\dot q^\alpha - \frac{\partial L}{\partial q^\alpha}
$$

由于$p_\alpha, q^\alpha, \dot q^\alpha$的相互独立性

$$
\frac{\partial H}{\partial q^\alpha} = - \frac{\partial L}{\partial q^\alpha}
$$

又由$Euler-Lagrange$方程：$\dfrac{\partial L}{\partial q^\alpha} = \dfrac{\mathrm d}{\mathrm dt}\left( \dfrac{\partial L}{\partial \dot q^\alpha} \right) = \dot p_\alpha$,因此有

$$
\frac{\partial H}{\partial q^\alpha} = - \dot p_\alpha
$$

对广义动量求偏导：

$$
\frac{\partial H}{\partial p_\alpha} = \dot q^\alpha - \frac{\partial L}{\partial p_\alpha} = \dot q^\alpha
$$

因此，我们将方程组

$$
\left\{
\begin{aligned}
\
\frac{\partial H}{\partial t} &= - \frac{\partial L}{\partial t} \\
\frac{\partial H}{\partial q^\alpha} &= - \dot p_\alpha \\
\frac{\partial H}{\partial p_\alpha} &= \dot q^\alpha
\end{aligned}
\right.
$$

称作 **$Hamilton$ 正则运动方程** . 物理系统的演化均服从这一方程组. 

我们还可以用很多方法得到哈密顿正则运动方程，比如最小作用量原理或者对哈密顿量取微分等等，在这里不加赘述. 



##### 2.3.3 已知演化路径的动力学问题

在我们此前对最小作用量原理的推导中，我们讨论的都是这样的动力学问题：已知物理系统演化的初末状态，利用最小作用量原理求解系统演化的具体路径. 但其实，在一些情况下，我们知道物理系统究竟是怎样演化的，只是想要知道系统演化的结果. 我们可以用最小作用量原理来讨论这个问题. 

此时系统的作用量：

$$
S = \int_{t_0}^{t} L \mathrm dt
$$

$$
\delta S = \int_{t_0}^{t} \delta L \mathrm dt = \int_{t_0}^{t} \mathrm dt\left[ \frac{\partial L}{\partial q^\alpha}\delta q^\alpha + \frac{\mathrm d}{\mathrm dt}\left( \frac{\partial L}{\partial \dot q^\alpha}\delta q^\alpha \right) - \frac{\mathrm d}{\mathrm dt}\left( \frac{\partial L}{\partial \dot q^\alpha}\right) \delta q^\alpha  \right]
$$

$$
= \int_{t_0}^{t} \mathrm dt\left[ \frac{\partial L}{\partial q^\alpha}\delta q^\alpha  - \frac{\mathrm d}{\mathrm dt}\left( \frac{\partial L}{\partial \dot q^\alpha}\right) \delta q^\alpha  \right] + \left. \left( \frac{\partial L}{\partial \dot q^\alpha}\delta q^\alpha \right) \right|_{t_0}^{t}
$$

由于系统演化的物理路径已经确定，故$ \dfrac{\partial L}{\partial q^\alpha}  - \dfrac{\mathrm d}{\mathrm dt}\left( \dfrac{\partial L}{\partial \dot q^\alpha}\right) = 0$恒成立. 又由于起始状态确定，因而$\delta q^\alpha(t_0) = 0$ . 因此，上式可以化为：

$$
\delta S = \frac{\partial L}{\partial \dot q^\alpha}\delta q^\alpha \Rightarrow \delta S = p_\alpha \delta q^\alpha
$$

我们思考一下$S$和什么参数有关. 首先，由于$L = L(t, \mathbf q, \mathbf{\dot q})$，因此$S$至多和$(t, \mathbf q, \mathbf{\dot q})$有关. 其中，和时间$t$有关是显然的，因为我们讨论的就是物理系统随时间的演化结果；此外，由于物理系统演化路径已经确定，因此我们一定可以从$Euler-Lagrange$方程中求解出广义坐标$\mathbf q = \mathbf q(t)$与广义速度$\mathbf{\dot q} = \mathbf{\dot q}(t)$的关系，所以我们只需要知道系统的广义坐标$\mathbf q$即可. 所以，$S = S(t, \mathbf q)$. 故有：

$$
\delta S = \frac{\partial S}{\partial q^\alpha} \delta q^\alpha
$$

我们可以得到

$$
p_\alpha = \frac{\partial S}{\partial q^\alpha}
$$

进一步，对$S$求时间的全导数

$$
\frac{\mathrm d S}{\mathrm d t} = \frac{\partial S}{\partial t} + \frac{\partial S}{\partial q^\alpha}\dot q^\alpha
$$

同时我们还有$\dfrac{\mathrm dS}{\mathrm dt} = L = p_\alpha q^\alpha - H$，$p_\alpha = \dfrac{\partial S}{\partial q^\alpha}$，代入

$$
\frac{\partial S}{\partial t} + H(t, \mathbf q, \mathbf p) = 0
$$

称为$Hailton-Jacobi$方程.



##### 2.3.4 力学量随时间的演化

假设一个力学量$F$，其与系统所处的状态$(\mathbf q, \mathbf p)$以及时间$t$相关. 我们

考虑一下其关于时间的演化

$$
\frac{\mathrm dF}{\mathrm dt} = \frac{\partial F}{\partial t} + \frac{\partial F}{\partial q^\alpha}\dot q^\alpha + \frac{\partial F}{\partial p_\alpha}\dot p_\alpha
$$

其中，由于$\dfrac{\partial H}{\partial p_\alpha} = \dot q^\alpha , \dfrac{\partial H}{\partial q^\alpha} = - \dot p_\alpha$，可以得到

$$
\frac{\mathrm dF}{\mathrm dt} = \frac{\partial F}{\partial t} + \frac{\partial F}{\partial q^\alpha}\frac{\partial H}{\partial p_\alpha} - \frac{\partial F}{\partial p_\alpha}\frac{\partial H}{\partial q^\alpha}
$$

在这里，我们引入一个更方便的记号：$Poisson$括号$\left[ F, G \right]_{PB} = \dfrac{\partial F}{\partial q^\alpha}\dfrac{\partial G}{\partial p_\alpha} - \dfrac{\partial F}{\partial p_\alpha}\dfrac{\partial G}{\partial q^\alpha}$. 这样，这个式子就可以写成

$$
\frac{\mathrm dF}{\mathrm dt} = \frac{\partial F}{\partial t} +\left[ F, H \right]_{PB}
$$

**つづく**









[^1]: 比如，速度相空间中，曲线$\{ q = t, \dot q =t^2 \}$就是没有意义的. 因为$\dfrac{\mathrm d}{\mathrm dt}q = 1 \neq t^2 = \dot q$.

[^2]: 推导过程简单而繁琐，我在这里就不赘述了. 

[^3]: 我们可以通过物理坐标下$T = \dfrac{1}{2}m \mathbf{\dot x}^2, \mathbf p = m \mathbf{\dot x}$，得出$H(t, \mathbf x, \mathbf{\dot x}) = m \mathbf{\dot x} \cdot \mathbf{\dot x} - \left( \dfrac{1}{2}m \mathbf{\dot x}^2 - V(\mathbf x) \right) = \dfrac{1}{2}m \mathbf{\dot x}^2 + V(\mathbf x) = T+V$，然后再利用坐标变换$\mathbf x = \mathbf x (\mathbf q)$变换成广义坐标的形式.
