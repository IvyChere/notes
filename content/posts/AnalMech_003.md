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


