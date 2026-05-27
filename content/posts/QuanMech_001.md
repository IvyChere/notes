+++
date = '2026-05-21T00:25:51+08:00'
draft = false
math = true
title = '量子力学 001'
tags = ['物理', '量子力学']
categories = ['量子力学']
description = "量子力学史概要与量子力学的基本假设"
summary = "量子力学总览：量子力学的基本假设"
+++

### 1. 量子力学史简述

出于篇幅限制，我在这里不会完整的讲述量子力学史. 如果感兴趣的话可以看知乎网友的[这一篇](https://zhuanlan.zhihu.com/p/141464986)文章.



#### 1.1 能量量子化

1900 年，为解决黑体辐射问题，$M.\ Planck$从以下假设出发，推导并很好地解释了实验现象：

* 黑体由大量的谐振子组成，分别以频率$\nu$振动. 谐振子时刻在以电磁波的形式吸收或放出能量.

* 谐振子携带的能量是离散的，其所能吸收和释放的能量也是离散的，且与谐振子的频率成正比.

其中，谐振子所能吸收或释放的能量是某一个能量单元$\varepsilon$的整数倍，服从

$$
\varepsilon = h \nu
$$

这个能量单元称为**能量子**，简称**量子**. 其中，$h = 6.626 \times 10^{-23}\ J \cdot s$为常量，称为$Planck$常数.

1904 年，$A.\ Einstein$采取同样的思路，将光的能量量子化，称为**光量子**，并完美地解释了光电效应. 



#### 1.2 氢原子光谱与$Bohr$氢原子模型

##### 1.2.1 氢原子光谱

19 世纪末，人们便发现，对稀薄的$H_2$加热，气体会释放出特定颜色的荧光。这些荧光组成了氢原子的光谱.

![](/images/Quan1.1.png)

1885 年，瑞士的一位中学数学老师$J. \ Balmer$观察发现了部分谱线（对应频率为$\nu$）的分布规律：

$$
\nu \propto \left( \frac{1}{2^2} - \frac{1}{n^2} \right), \ n = 3, 4, 5, \dots
$$

服从这个规则的谱线称为氢原子光谱的$Balmer$系.

随后，人们又发现了$Paschen$系：

$$
\nu \propto \left( \frac{1}{3^2} - \frac{1}{n^2} \right), \ n = 4, 5, 6, \dots
$$

$Brackett$系：

$$
\nu \propto \left( \frac{1}{4^2} - \frac{1}{n^2} \right), \ n = 5, 6,7 , \dots
$$

等诸多线系. 这些规律被瑞典物理学家$J. \ Rydberg$总结为：

$$
\frac{1}{\lambda} = \mathrm {R}\left( \frac{1}{m^2} - \frac{1}{n^2} \right), m < n \in \mathbb {N^+}
$$

其中的$\mathrm R = 1.09737 \times 10^7 \ m^{-1}$为常数. 



##### 1.2.2 $Bohr$氢原子模型

尽管氢原子光谱的分布规律已经在实验上得到了简洁且准确的描述，但是这个公式始终没有得到经典理论的证明. 

1913 年$N.\ Bohr$从量子化的角度出发，建立了一套新的氢原子模型，史称$Bohr$理论.

这个理论基于以下几条假设：

* **定态假设：** 电子只能处于一系列离散的轨道上，每一个轨道代表一个确定的能量状态. 电子在轨道上绕原子核做匀速圆周运动，但是不向外辐射电磁波. 称这样的状态为“定态”. 电子在不同定态之间的转化称为“跃迁”. 

* **频率条件：** 对于两个定态$E_m, E_n\ (E_m>E_n)$ ：
  
  * 电子从$E_m$跃迁到$E_n$时（由高到低），辐射电磁波
  
  * 电子从$E_n$跃迁到$E_m$时（由低到高），吸收电磁波
  
  且吸收或释放的电磁波的能量为$E_m - E_n = h\nu$，$\nu$为电磁波的频率.

* **角动量量子化：** 在原子中，电子的轨道角动量满足特定条件：
  
  $$
  L_e = m_evr = n\hbar, \ n = 1, 2, 3,\dots
  $$
  
  其中$\hbar = \frac{h}{2\pi}$，$h$为$Planck$常数.

$Bohr$考虑某一处于定态$E_n$的原子，原子系数为$Z$，核外只有一个电子，其质量为$m$，带电$e$，在半径为$r_n$的轨道上绕原子核做匀速圆周运动.

电子所受的库仑力为$F = \dfrac{Ze^2}{4\pi\epsilon_0 r^2}$.由牛顿第二定律：

$$
\frac{Ze^2}{4\pi\epsilon_0 r_n^2} = m_e\frac{v_n^2}{r_n}
$$

将$L = m_ev_nr_n = n\hbar$代入：

$$
\begin{aligned}
&v_n = \frac{Ze^2}{4\pi\epsilon_0\hbar} \frac{1}{n}, \ n = 1, 2, 3, \dots \\
&r_n = \frac{4\pi\epsilon_0\hbar^2}{Z m_e e^2} n^2, \ n = 1, 2, 3, \dots
\end{aligned}
$$

将牛顿第二定律方程代入得电子的动能：

$$
T = \frac{1}{2}m_ev_n^2 = \frac{1}{4\pi\epsilon_0}\frac{Ze^2}{2r}
$$

电子的势能：

$$
V = -\frac{1}{4\pi\epsilon_0}\frac{Ze^2}{r}
$$

总能量：

$$
E_n = -\frac{1}{4\pi\epsilon_0}\frac{Ze^2}{2r} = -\frac{Zm_e e^4}{32\pi^2\epsilon_0^2\hbar^2} \frac{1}{n^2}, \ n = 1, 2, 3,\dots
$$

不同的定态有不同的名字

* $n=1$时，称为“基态”.

* $n \geq 2$时，分别称为“第$1$激发态”（$n=2$）、“第$2$激发态”（$n = 3$）、$\cdots$、"第$k$激发态"（$n = k+1$）. 统称为“激发态”.

* $n \rightarrow +\infty$时，电子脱离原子核，称为“电离态”.

当电子由定态$E_m$跃迁至$E_n$（$n < m$）时：

$$
h\nu = E_m - E_n = \frac{Zm_e e^4}{32\pi^2\epsilon_0^2\hbar^2} \left( \frac{1}{n^2} - \frac{1}{m^2} \right)
$$

由于$c = \lambda\nu$，即

$$
\frac{1}{\lambda} = \frac{m_e e^4 Z^2}{8 \varepsilon_0^2 h^3 c} \left( \frac{1}{n^2} - \frac{1}{m^2} \right), n < m \in \mathbb N^+
$$

其中$\mathrm R = \dfrac{m_e e^4 Z^2}{8 \varepsilon_0^2 h^3 c}$. 这个数据与实验结果吻合地很好.
