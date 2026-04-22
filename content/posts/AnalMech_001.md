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
\mathbf{F}=m\mathbf{\ddot{x}}
$$

对于不同的力， $\mathbf{F}$ 的形式有所不同。但是只要代入求解上述的微分方程，再加上 $\textbf{x} $与 $\mathbf{\ddot{x}}$ 的初值条件，我们就可以得到这一个质点的运动方程$\mathbf{x} = \mathbf{x}(\mathrm{t})$ .

看起来，牛顿第二定律似乎足够我们解决大多数的动力学问题了. 但是对于具体的物理情景而言，情况似乎要复杂得多.

#### 1.1 物理坐标$(x, y)$下的单摆运动

例如，我们考虑匀重力场$\mathbf{g}$下一个摆长为$l$单摆的运动：

当它达到摆角$\theta$时，受到绳子的约束力为$\mathbf{T}$. 

由牛顿第二定律，在$x$轴与$y$轴方向上：

$$
T \sin \theta = - m \ddot{x} \\
$$

$$
mg - T \cos \theta =m \ddot{y}
$$

消去$\mathrm{T}$得到：

$$
\ddot{x} + (\ddot{y}-g)\frac{x} {y}= 0 \Rightarrow \ddot{x} y + x(\ddot{y} - g) = 0
$$

不幸的是，在这样的情形下，仅凭借牛顿第二定律无法帮助我们得到单摆的运动方程. 原因是显而易见的：在这个情景下，质点不是在整个空间内不受束缚地自由运动. 它的运动受到了几何上的**约束**$\mathrm{x^2+y^2} = l^2$，即摆绳不可自由伸长. 只有联立这两个方程，才能最终解出单摆的运动方程. 

对约束方程求二次导数：

$$
x\dot{x} + y\dot{y} = 0 \Rightarrow \dot{y} = -\frac{x}{y} \dot{x} 
$$

$$
\dot{x}^2 + x \ddot{x} + \dot{y}^2 + y \ddot{y} = 0
$$

消去$\mathrm{y, \dot{y}, \ddot{y}}$得到：

$$
\ddot{x} + \frac{x}{L^2 - x^2} \dot{x}^2 + \frac{g}{L^2} x \sqrt{L^2 - x^2} = 0
$$

同理可得到$\mathrm{y}$分量的运动方程. 

#### 1.2 广义坐标与位形空间

##### 1.2.1 旧有方法的不足

到这里，我们可以发现传统的牛顿第二定律在描述质点运动时的不足：

- 牛顿第二定律是矢量定律，必须要考虑各个分量上的运动。而由于约束的存在，某些分量上的运动又不是互相独立的
- 在物理坐标$(x, y)$下，哪怕对于某些简单的运动，其运动方程也极其复杂

这些问题可以归结为：**我们能否找到一组相互独立的坐标$(q^1, q^2)$[^1]，使得我们可以不考虑约束的存在，而直接利用牛顿第二定律求解运动方程？**

幸运的是，这样的坐标是存在的. 

容易发现，在极坐标系下，单摆的位置可以由半径与摆角$(\rho, \theta)$这一对坐标描述，而由于几何约束，$\rho \equiv l$. 因此，我们只需要考虑$\theta$方向的运动即可. 此时，由极坐标下的牛顿第二定律：$\mathrm{F}_{\theta} = \mathrm{m(\rho \ddot{\theta} + 2 \dot{\rho}\dot{\theta})}$可以得出：

$$
\mathrm{mg \sin \theta} = - \mathrm{m}l\ddot{\theta} \Rightarrow \ddot{\theta} + \frac{\mathrm{g}}{l} \sin \theta
$$

简单又简洁. 

事实上，对于任意一个带约束的力学系统，我们都可以找到一组两两独立的新坐标$\mathbf{q}=(q^1, q^2, \dots, q^s)$. 我们在这组坐标下使用牛顿第二定律，便可求解出系统的运动方程，而不用考虑系统所受具体的约束. 这样的坐标称为 **“广义坐标”**. 区别于由世界中真实可感的物理坐标$\mathbf{x}=(x^1, x^2, \dots, x^N)$张成的“物理空间”，广义坐标张成的空间称为 **“位形空间”**，这是一个抽象的空间，其中的每一点都可以确定系统演化的某一个具体状态. 

##### 1.2.2 位形空间中的动力学

我们前面提到过，在物理空间中，根据牛顿第二定律$\mathbf{F} = m \mathbf{\ddot{x}}$，系统的演化都可以由多个二阶微分方程决定。我们只要知道$\mathbf{x}$与$\mathbf{\dot{x}}$的初值条件，就可以确定这个系统的运动方程. 也就是说，一个物理系统可以由某时刻的位置$\mathbf{x}$与速度$\mathbf{\dot{x}}$确定. 换言之，如果我要使用某个状态函数$S$来刻画一个物理系统的演化，只需要以$t$，$\mathbf{x}$与$\mathbf{\dot{x}}$作为参数即可. 

这个结论在位形空间中是否成立呢？要研究这个问题，我们只需要知道位形空间中牛顿第二定律的阶数即可.

为了书写方便，我们将引入$Einstein$求和约定：**当一个表达式中出现了重复的指标（包括上标、下标）相乘时，将这个重复指标视为求和索引，对表达式进行遍历求和**：

$$
p_i q_i :=\sum_{i=1}^{n} p_i q_i
$$

$$
r_{\mu\nu} s_\mu t_\nu:= \sum_{\mu=1}^{n}\sum_{\nu=1}^{n} r_{\mu\nu} s_\mu t_\nu
$$

考虑一个从物理空间到位形空间的变换$\mathbf{x=x(q)}$. 进而有$\mathbf{\dot{x}} = \frac{\partial \mathbf{x}}{\partial q^\alpha} \dot{q^\alpha}$，$\mathbf{\ddot{x}}= \frac{\partial \mathbf{x}}{\partial q^\alpha} \ddot{q^\alpha} + \frac{\partial^2 \mathbf{x}}{\partial q^\alpha q^\beta}\ddot{q^\alpha}\dot{q^\beta}$. 带入牛顿第二定律：

$$
\mathbf{F} = m(\frac{\partial \mathbf{x}}{\partial q^\alpha} \ddot{q^\alpha} + \frac{\partial^2 \mathbf{x}}{\partial q^\alpha q^\beta}\ddot{q^\alpha}\dot{q^\beta})
$$

也是一个二阶微分方程. 故在位形空间下，我们也只需要广义坐标$\mathbf{q}$与广义速度$\mathbf{\dot{q}}$就可以确定一个物理系统的演化. 



### 2. $D'Alembert$原理

约束的问题解决了. 可我们又遇到了一个新的问题：按照我们上面的做法，我们需要求出在某套广义坐标$\mathbf{q}$下牛顿第二定律的具体形式，才可以对运动学问题进行求解. 我们能否想办法绕过牛顿第二定律，找到某种可以一劳永逸的方法呢？

在讨论这个问题之前，我想先介绍另一道题. 

#### 2.1 虚位移、虚功

##### 2.1.1 虚位移

![](/images/Blog1.1.png)

如图所示：在一个光滑半球形的上方摆放一根不可伸长的匀质细绳，绳的质量为$m$，长为$l$. 绳的左端恰好竖直悬空；绳的右端恰好在半球形的最高点处，平行于地面. 重力加速度为$g$. 求绳右端的张力$T$. 
当然，我们可以将这根绳分割为无数个质量微元，对微元做受力分析，再将结果积分. 这是一个很自然的想法. 但是，我在这里将给出一个更加巧妙的方法：虚功法. 
假设在张力的作用下，绳子缓慢向右产生了一个虚位移$\delta x$（我们马上就会解释这是什么）. 此时，张力对绳做的功$\delta W = T \delta x$. 

这些功完全转化为了绳的重力势能$\delta E_p = (\delta m) gR = \frac{m}{l} \delta x gh$（可以视为将绳下端一个$\delta m$的质元切下，移动到了绳的上端）. 又：$l = \frac{\pi}{2}R$. 固我们可以得到$T = \frac{mgR}{l} = \frac{2mg}{\pi}$. 

在这道题里面，尽管绳子始终保持静止，我们仍然假设其发生了一个虚拟的位移$\delta x$，并以它为媒介结合绳的平衡状态求解出了一个常规方法难以求解的物理量. 在这里，我们要对这个虚位移$\delta x$做一个更加准确的阐释：**在某个确定的时刻上**，质点可以发生的**符合约束条件**的位移. 我们刻画位移的时候，往往会取一段极短的时间$\mathrm d t$，测量质点位置的变化$\mathrm d \mathbf r$；虚位移发生在某一个时刻$t$，因此虚位移$\delta \mathbf r$事实上是没有发生的. 

换言之，虚位移$\delta \mathbf r$既不刻画位置，也不描述移动......

闹着玩呢？

我们不妨换一个方法理解. 在某一个时刻$t$，我们给质点拍下一张照片. 从这张照片中，我们得到的信息只有质点所处的位置$\mathbf r$与质点所受的约束$\Phi(\mathbf r) = 0$（假设约束只与质点所处的位置有关，我们称之为**完整约束**；当约束还与质点的速度相关时，约束称为**非完整约束**）. 我们要根据这张照片，对质点接下来的运动进行预测. 此时，我们**猜测物体可能发生的位移**即为虚位移$\delta \mathbf r$.

既然我们可以从质点的约束“猜测”出质点的虚位移，是否说明虚位移和虚功之间存在某种关系呢？

设质点的位置为$\mathbf r$，系统的约束为$\Phi(\mathbf r) = 0$. 质点发生虚位移$\delta \mathbf r$时，由定义，质点的位置仍然符合约束条件，即

$$
\Phi (\mathbf{r + \delta r}) = 0
$$

展开

$$
\frac{\partial \Phi}{\partial \mathbf r} \cdot \mathbf{\delta r} = 0 \Rightarrow \nabla \Phi \cdot \mathbf{\delta r} = 0
$$

即：虚位移始终与几何约束的法向垂直. 或者说，虚位移始终沿几何约束的切向. 



##### 2.1.2 虚功原理

虚位移是一个非常有用的工具。一方面，我们可以求出力在虚位移上做的**虚功**$\delta W = \mathbf{F \cdot \delta r}$，将质点某时刻受到的力同做功——进而同能量联系起来；另一方面，由于虚位移并没有实际发生，因此质点的运动状态并没有发生改变. 特殊地，当质点处于平衡状态时，其所受合外力的虚功$\delta W = 0$. 我们称之为**虚功原理**.

可是，在绝大多数情况下，质点的运动都是非平衡的。事实上，对于一个质点而言，它往往受到自由外力$\mathbf F$，约束力$\mathbf R$（作用是将质点束缚在约束条件上）的作用. 难道我们就要就此抛弃虚功原理这个简洁高效的方法了吗？

这个时候法国物理学家$J. D'Alembert$ 跳了出来。他说，质点的运动满足牛顿第二定律

$$
\mathbf {F + R} = m\mathbf{\ddot{r}}
$$

这个质点的运动不满足平衡条件. 但是只要我们对这个式子进行简单的变形

$$
\mathbf{F + R} - m\mathbf{\ddot{r}} = 0
$$

这个时候，等式右边为0，质点的运动不就是平衡的了吗？我们管$\mathbf{f} = - m \mathbf{\ddot{r}}$叫做惯性力. 也就是说，对于一般的运动，质点所受的自由合外力$\mathbf F$，约束力$\mathbf R$与惯性力$-m\mathbf{\ddot r}$三力平衡.

......我说6，还能这么玩.

但是既然我们可以使用惯性力将一般的运动化为平衡的运动，那么我们是不是就可以利用虚功原理了呢？

说干就干. 此时，由虚功原理，合外力所做的虚功

$$
(\mathbf{F + R} - m\mathbf{\ddot r}) \cdot \mathbf{\delta r} = 0
$$

绝大多数情况下，约束力$\mathbf R$与几何约束垂直（我们称此时的约束为**理想约束**）. 由$\nabla \Phi \cdot \mathbf{\delta r}=0$可得，$\mathbf{R \cdot \delta r} = 0$. 故上式可以化为

$$
(\mathbf{F} - m \mathbf{\ddot{r}}) \cdot \mathbf{\delta r} = 0
$$

另一方面，既然都存在约束，那么更方便的选择一定是选取一组两两独立的广义坐标$\mathbf{q}=(q^1, q^2, \dots, q^s)$，再对系统进行描述. 广义坐标与物理坐标之间存在变换$\mathbf{r = r(q)}$，那么我们可以得到

$$
\mathbf{\delta r} = \sum_{\alpha = 1}^{s} \frac{\partial \mathbf{r}}{\partial q^\alpha} \delta q^\alpha
$$

牢记$Einstein$求和约定（见1.2.2），我们可以把它改写为

$$
\mathbf{\delta r} = \frac {\partial \mathbf{r}}{\partial q^\alpha} \delta q^\alpha
$$

从而有

$$
(\mathbf {F} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} - m \mathbf{\ddot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha})\delta q^\alpha =0
$$

由于广义坐标$\mathbf q = (q^1, q^2, \dots, q^s)$这$s$个变量两两独立，为使上面这个$s$项和式（牢记$Einstein$求和约定！）为$0$，则其中的每一项系数

$$
\mathbf {F} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} - m \mathbf{\ddot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} = 0
$$

多说一嘴，现在这个式子中已经不存在相乘的重复指标了，不符合$Einstein$求和约定的使用条件. 因此$q^\alpha$就是一个带指标的变量. 

为了简化这个等式的形式，我们定义$Q_\alpha = \mathbf {F} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}$，称之为**广义力（在$q^\alpha$上的分量）**[^2] .广义力的具体形式我们马上就会给出. 我们把上式改写成：

$$
Q_\alpha = m \mathbf{\ddot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}
$$

我们考虑等号右边，利用分部积分法可以得到：

$$
m \mathbf{\ddot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} = m \frac{\mathrm d}{\mathrm d t}(\mathbf{\dot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}) - m\mathbf{\dot r} \cdot \frac{\mathrm d}{\mathrm d t}(\frac {\partial \mathbf{r}}{\partial q^\alpha})
$$

其中：

$$
\mathbf{\dot r} = \frac{\partial \mathbf{r}}{\partial q^\beta}\dot q^\beta
$$

注意，这里有出现了重复指标$\beta$，注意$Einstein$求和约定！

从这里，我们可以得到一个结论：

$$
\frac{\partial \mathbf{\dot r}}{\partial \dot q^\beta} = \frac{\partial \mathbf{r}}{\partial q^\beta}
$$

而另一部分

$$
\frac{\mathrm d}{\mathrm d t}(\frac {\partial \mathbf{r}}{\partial q^\alpha}) = \frac{\partial}{\partial q^\beta}(\frac {\partial \mathbf{r}}{\partial q^\alpha}) \dot q^\beta = \frac{\partial}{\partial q^\alpha}[(\frac {\partial \mathbf{r}}{\partial q^\beta}) \dot q^\beta] = \frac{\partial \mathbf{\dot r}}{\partial q^\alpha}
$$

从而我们得到：

$$
m \mathbf{\ddot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} =\frac{\mathrm d}{\mathrm d t}(m\mathbf{\dot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}) - m\mathbf{\dot r} \cdot \frac {\partial \mathbf{\dot r}}{\partial q^\alpha}
$$

即

$$
Q_\alpha = \frac{\mathrm d}{\mathrm d t}(m\mathbf{\dot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}) - m\mathbf{\dot r} \cdot \frac {\partial \mathbf{\dot r}}{\partial q^\alpha}
$$

我们考虑系统的动能$T(\mathbf{\dot r}) = \frac{1}{2}m(\mathbf{\dot r})^2$

$$
\frac{\partial T}{\partial \dot q^\alpha} = \frac{\partial T}{\partial \mathbf{\dot r}} \cdot \frac {\partial \mathbf{\dot r}}{\partial \dot q^\alpha} = m\mathbf{\dot r} \cdot \frac {\partial \mathbf{\dot r}}{\partial \dot q^\alpha} = m\mathbf{\dot r} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha}
$$

$$
\frac{\partial T}{\partial q^\alpha} = \frac{\partial T}{\partial \mathbf{\dot r}} \cdot \frac {\partial \mathbf{\dot r}}{\partial q^\alpha} = m\mathbf{\dot r} \cdot \frac {\partial \mathbf{\dot r}}{\partial q^\alpha}
$$

因此，我们可以得到：

$$
Q_\alpha = \frac{\mathrm d}{\mathrm d t}(\frac{\partial T}{\partial \dot q^\alpha}) - \frac{\partial T}{\partial q^\alpha} 
$$

这个式子称为$D'Alambert$虚功原理.















[^1]: 出于某些原因，我们将坐标的指标写在字母的右上方，如$q^1, q^2, \dots, q^\alpha, \dots, q^s$. 当出现幂运算时（很少！），我们会写成$(q^1)^2, (q^2)^2, \dots, (q^s)^2$

[^2]: 这个定义是自然的. 因为自由外力做的虚功$\delta W_{\mathbf{F}} = \mathbf{F \cdot \delta r} = \mathbf {F} \cdot \frac {\partial \mathbf{r}}{\partial q^\alpha} \delta q^\alpha = Q_\alpha \delta q^\alpha$（最后两个等号使用了$Einstein$求和约定），即自由外力在物理坐标下的虚功等于广义力在广义坐标下的虚功. 
