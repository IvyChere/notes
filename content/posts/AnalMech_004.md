+++
date = '2026-05-02T18:28:35+08:00'
draft = false
math = true
title = '分析力学 004'
tags = ['物理', '分析力学']
categories = ['分析力学']
description = "Poisson 括号"
summary = "Poisson 括号与矢量分析基础"
+++

Tip: 分析力学的往期内容戳[这里](https://blogs.starspress.org/tags/%E5%88%86%E6%9E%90%E5%8A%9B%E5%AD%A6/)

### 1. 矢量分析基础

> $Einstein$求和约定真的太好用了. 
> 
> ——沃夏 · 硕德

在讲矢量分析之前，我想先回顾一下我们老生常谈的$Einstein$求和约定. 

**当一个表达式中出现了重复的指标（包括上标、下标）相乘时，将这个重复指标视为求和索引，对表达式进行遍历求和**：

$$
p_i q_i :=\sum_{i=1}^{n} p_i q_i
$$

$$
r_{\mu\nu} s_\mu t_\nu:= \sum_{\mu=1}^{n}\sum_{\nu=1}^{n} r_{\mu\nu} s_\mu t_\nu
$$

在这里，重复的指标（也就是求和的指标），我们称为 **“哑指标”**，而不参与求和的指标我们称为 **“自由指标”**. 哑指标本身不表示什么特殊的意义，也就是说，哑指标的字母可以在不引起歧义的情况下自由替换. 这时很容易理解的，比如当$i = 1, 2, 3$时：

$$
p_i q_i :=\sum_{i=1}^{3} p_i q_i = p_1 q_1 + p_2 q_2 + p_3 q_3
$$

这个实际上的求和与我们的求和指标选取的字母无关，不管我们把$i$换成什么字母——$abc$也好$rst$也罢——这一个求和表示的都是等号最右边的那个表达式. 

我们选取哑指标的标准只有一个：**不与已存在的哑指标的字母一致**. 比如说，如果我们在第一个求和式选取了$ij$作为哑指标，那我们的第二个求和式就不要再使用$ij$了，而是选择其他字母（比如$mn$）. 当然，如果我们将和式化到了最简（至少不会产生歧义），我们可以把其中的某组哑指标（如$mn$）化为另一组哑指标（如$ij$，以保证结果的简洁. 



#### 1.1 $Kronecker$张量

在线性空间$\mathbb R^n$中，我们一定可以找到一组单位正交基向量$\left\{ \mathbf{e}_1, \mathbf{e}_2,\ \dots, \mathbf{e}_n \right\}$. 我们从中选取两个基向量$\mathbf{e}_i, \mathbf{e}_j$，当$i = j$时，$\mathbf{e}_i \cdot \mathbf{e}_j = 1$；否则，$\mathbf{e}_i \cdot \mathbf{e}_j = 0$. 

一生追求偷懒的数学家们把上面两个式子写成了一个统一的形式：

$$
\mathbf{e}_i \cdot \mathbf{e}_j = \delta_{ij}
$$

其中的$\delta_{ij}$称为$Kronecker$张量，遵循如下的定义：

$$
\delta_{ij} = \left\{
\begin{aligned}
1 &, \ i = j \\
0 &, \ i \neq j
\end{aligned}
\right.
$$

##### 1.1.1 性质

$Kronecker$张量有一些比较废话的性质，比如：

- $\delta_{ij} = \delta_{ji}$
  这是废话

- $\delta_{ij} A_j = A_i$
  这也是废话，因为当且仅当$j = i$时，$\delta_{ij}A_j$才不等于$0$

##### 1.1.2 应用

对于两个矢量$\mathbf A = A_i \mathbf e_i, \mathbf B = B_j \mathbf e_j$（记得不要选取重复的哑指标哦！）

$$
\mathbf A \cdot \mathbf B = (A_i \mathbf e_i) \cdot (B_j \mathbf e_j) = A_i B_j (\mathbf e_i \mathbf e_j) = \delta_{ij}A_i B_j
$$

当然，你也可以写成$\mathbf A \cdot \mathbf B = A_iB_i$. 在合适的时候选取合适的数量积表示方法可以帮助我们更好地解决问题. 

当然，有一点必须要格外注意：在$Kronecker$张量中，有些时候也会出现重复的指标，比如$\delta_{ii}$. 这种情况下千万不要忘记使用$Einstein$求和约定！



#### 1.2 $Levi-Civita$张量

我们一般会这么定义$Levi-Civita$张量$\epsilon_{ijk}$：

$$
\epsilon_{ijk} = \left\{
\begin{aligned}
1 &, \ ijk \ 为偶排列 \\
-1 &, \ ijk \ 为奇排列 \\
0 &, \ ijk \ 为其他情况
\end{aligned}
\right .
$$

其中，偶排列指的是逆序数为偶数的排列[^1]，奇排列指的是逆序数为奇数的排列. 

当然，如果你忘了逆序数是个什么逆天玩意也没关系. 我们可以说人话. 

当$ijk$三个值的顺序保持了$123$这三个数的相对位置不变时（即$ijk$取$123, 231, 321$时），$\epsilon_{ijk} = 1$.

当$ijk$三个值的顺序不能保证$123$这三个数的相对位置不变时（即$ijk$取$132, 321, 213$时），$\epsilon_{ijk} = -1$.

当$ijk$三个值出现了重复值的时候（如$ijk$取诸如$111, 112, 113, 122, \dots$这样的值时），$\epsilon_{ijk} = 0$.

[^1]: 逆序数就是你学习线性代数它教材第一章上来就甩到你脸上的东西

我们还可以推出$Levi-Civita$张量的行列式形式：

$$
\epsilon_{ijk} = 
\begin{vmatrix}
\delta_{1i} & \delta_{2i} & \delta_{3i} \\
\delta_{1j} & \delta_{2j} & \delta_{3j} \\
\delta_{1l} & \delta_{2k} & \delta_{3k}
\end{vmatrix}
$$

你可以使用$Kronecker$张量的缩并性+哑指标展开消去$Levi-Civita$张量来得到这个式子. 但是我在这里就不加推导了，只在这证明这两个形式的等价性.

- 当$ijk$存在重复指标时，上述行列式中存在两列完全相同. 因此$\epsilon_{ijk} = 0$.

- 当$ijk$成偶排列时，我们不妨先只考虑$ijk = 123$的情况：
  
  - 此时，$\epsilon_{ijk} = \det{\mathrm I_{3 \times 3}} = 1$，其中$\mathrm I_{3 \times 3}$为三阶单位矩阵.
  
  - 而我们对排列$123$进行偶数次交换（即对该行列式的各列进行偶数次交换，行列式的值不变），可以得到$ijk$取其他偶排列的情况，行列式的值不变. 
  
  - 因此，$ijk$成偶排列时，$\epsilon_{ijk} = 1$.

- 当$ijk$成奇排列时，同理，我们只需要对排列$123$取奇数次交换（行列式的值变为其相反数）即可得到所有奇排列的情况. 因此$\epsilon_{ijk} = -1$

行列式形式可以帮助我们更好地证明$Levi-Civita$张量的各个性质.

##### 1.2.1 性质




