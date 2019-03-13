---
title: 简单理解 Hatree-Fock 方法
date: 2019-01-18 23:11:20
tags: First Principle Calculation
---

# 多原子分子体系S-方程的描述

## Hamiltonian 算符

在非相对论近似下，分子体系满足多体 Schrodinger 方程：
$$
\hat { H } \Phi = \varepsilon \Phi
$$
其中 $\hat{H}$ 是分子体系的 Hamiltonian 算符，$\Phi$ 是分子体系的波函数。

设一个分子体系含 $M$ 个核，$N$ 个电子，则它的 Hamiltonian 可以写成

$$
\begin{align*}
\hat { H } ={}& \hat { T } _ { e } + \hat { T } _ { N } + \hat { V } _ { N e } + \hat { V } _ { e e } + \hat { V } _ { N N } \\
={}& - \sum _ { i = 1 } ^ { N } \frac { 1 } { 2 } \nabla _ { i } ^ { 2 } - \sum _ { \alpha = 1 } ^ { M } \frac { 1 } { 2 M _ { \alpha } } \nabla _ { \alpha } ^ { 2 } - \sum _ { i = 1 } ^ { N } \sum _ { \alpha = 1 } ^ { M } \frac { Z _ { \alpha } } { r _ { i \alpha } } + \sum _ { i = 1 } ^ { N } \sum _ { j > i } ^ { N } \frac { 1 } { r _ { i j } } + \sum _ { \alpha = 1 } ^ { M } \sum _ { \beta > \alpha } ^ { M } \frac { Z _ { \alpha } Z _ { \beta } } { R _ { \alpha \beta } }
\end{align*} \tag{2}
$$

式子中 $\alpha, \beta$ 表示原子核的标号，$Z_{\alpha}$ 表示核电荷数，$M_{\alpha}$ 表示原子核的质量（原子单位制）， $i,j$ 表示电子的标号。

### Born-Oppenheimer 近似

Born-Oppenheimer 近似：电子的质量远远小于核的质量，故核的运动相对于电子是相当缓慢的，因此研究电子的运动行为时认为核是不动的，就好比放牛时牛和它周围的牛蝇运动一样。

经过 Born-Oppenheimer 近似，电子与核的运动被解耦，它们被分开处理，分子的波函数可以写成电子波函数和核波函数乘积的形式，即
$$
\Phi = \Psi _ { e l } \Psi _ { N } \notag
$$
于是电子运动和核的运动分别描述为
$$
\begin{cases}
\left( \hat { T } _ { e } + \hat { V } _ { N e } + \hat { V } _ { e e } \right) \Psi _ { e l } = E _ { e l } \Psi _ { e l }\\
\left(\hat { T } _ { N } + \hat { V } _ { N N }\right) \Psi _ { N } = \left( \varepsilon - E _ { e l } \right) \Psi _ { N }
\end{cases} \label{eq:oppenheimer}
$$

$\eqref{eq:oppenheimer}$ 式中第一个方程即为电子的运动方程，也是量子化学主要研究的问题。

### 平均场近似

忽略电子之间的瞬时运动关联，每个电子视为在核与其他电子建立的平均势场中运动。每个电子的状态用一个分子轨道（分子波函数）描述，即
$$
\hat { h } ( 1 ) \psi _ { i } ( 1 ) = \varepsilon _ { i } \psi _ { i } ( 1 ) \label{eq:mo}
$$
其中 $\{ \psi_i \}$ 为分子轨道（MO）； $\{ \epsilon_i \}$ 为轨道能 。

其中单电子算符 $ \hat { h } ( 1 ) = - \frac { 1 } { 2 } \nabla _ { 1 } ^ { 2 } + \sum _ { a } - \frac { Z _ { a } } { r _ { 1 a } } + \hat { v } _ { e f f } ( 1 ) $ ， $\hat { v } _ { e f f } ( 1 )$ 是等效单电子势，即其他电子对该电子相互作用的等效作用势。

总电子的波函数用行列式波函数（Slater 行列式）描述，总电子能量为

$$
E _ { e l } = \left\langle \Psi \left| H _ { e l } \right| \Psi \right\rangle
$$

###  LCAO 近似

分子轨道取为某些合理的原子轨道线性组合：
$$
\psi _ { i } = \sum _ { v } c _ { v i } \varphi _ { v } \label{eq:lcao}
$$
$\eqref{eq:lcao}$ 中$c_{vi}$ 表示原子轨道的系数， $\varphi_v$ 表示原子轨道。

注：这里的分子轨道指自旋轨道，区别于空间轨道。（自旋轨道 = 空间轨道 * 自旋， $\psi_i = \varphi_i \eta_i$）

## 行列式波函数

由于电子具有交换反对称性，简单乘积波函数
$$
\Phi = \prod_i \psi_i
$$
不能描述这个性质，故必须使用 Slater 行列式描述体系的波函数，即：
$$
\begin{align}
\Psi \left( q _ { 1 } , \cdots , q _ { N } \right) ={}& \frac { 1 } { \sqrt { N ! } } \nonumber
\begin{vmatrix} \begin{array} { c c c } { \psi _ { 1 } \left( q _ { 1 } \right) } & { \cdots } & { \psi _ { 1 } \left( q _ { N } \right) } \\ { \psi _ { 2 } \left( q _ { 1 } \right) }& \cdots & { \psi _ { 2 } \left( q _ { N } \right) } \\ { \vdots }& \ddots & { \vdots } \\ { \psi _ { N } \left( q _ { 1 } \right) }& \cdots & { \psi _ { N } \left( q _ { N } \right) } \end{array} \end{vmatrix} \\ \nonumber
={}& | \psi _ { 1 } \psi _ { 2 } \cdots \psi _ { N } \rangle \\
={}&  \frac { 1 } { \sqrt { N ! } } \sum _ { n = 1 } ^ { N ! } ( - 1 ) ^ { P _ { n } } \hat { P } _ { n } \left\{ \psi _ { 1 } \left( q _ { 1 } \right) \psi _ { 2 } \left( q _ { 2 } \right) \cdots \psi _ { N } \left( q _ { N } \right) \right\}  \label{eq:slater}
\end{align}
$$


- $\hat{P}$ 算符是交换算符， $\hat{P}_{12}$ 表示将 1, 2 号轨道上的电子互换；
- $\eqref{eq:slater}$ 中的每个电子的分子轨道都满足正交归一性： $ \left\langle \psi _ { i } | \psi _ { j } \right\rangle = \int \psi _ { i } ^ { * } ( 1 ) \psi _ { j } ( 1 ) d q _ { 1 } = \delta _ { i j } $ （即每个电子只能占据一个轨道）；
- 如果两个行列式波函数的自旋轨道不完全相同，则它们正交。

## 库仑作用与交换作用

### 库仑作用

库仑作用是指两个电子（无论自旋是否相同）之间存在的静电相互作用：
$$
\begin{aligned} J _ { 1 s 2 s } & = \int \frac { \left| \psi _ { 1 } ( 1 ) \right| ^ { 2 } \cdot \left| \psi _ { 2 } ( 2 ) \right| ^ { 2 } } { r _ { 12 } } d q _ { 1 } d q _ { 2 } \\ & = \int \frac { \left| \varphi _ { 1 s } ( 1 ) \right| ^ { 2 } \cdot \varphi _ { 2 s } \left. ( 2 ) \right| ^ { 2 } } { r _ { 12 } } d \vec { r } _ { 1 } d \vec { r } _ { 2 } \int \left| \eta _ { 1 } ( 1 ) \right| ^ { 2 } d \omega _ { 1 } \int \left| \eta _ { 2 } ( 2 ) \right| ^ { 2 } d \omega _ { 2 } \end{aligned}
$$

### 交换作用

以 He​ 体系为例：
$$
\Psi ( 1,2 ) = \frac { 1 } { \sqrt { 2 } } \left| \begin{array} { l l } { \psi _ { 1 } ( 1 ) } & { \psi _ { 1 } ( 2 ) } \\ { \psi _ { 2 } ( 1 ) } & { \psi _ { 2 } ( 2 ) } \end{array} \right|
$$
则它的能量期待值为：
$$
\begin{aligned}
E ={}& \frac { 1 } { 2 } \left\langle \psi _ { 1 } ( 1 ) \psi _ { 2 } ( 2 ) - \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) \left| \hat { h } ( 1 ) + \hat { h } ( 2 ) + \frac { 1 } { r _ { 12 } } \right| \psi _ { 1 } ( 1 ) \psi _ { 2 } ( 2 ) - \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) \right\rangle \\
={}& \frac { 1 } { 2 } \left\{ 2 \times \left( \varepsilon _ { 1 s } ^ { 0 } + \varepsilon _ { 2 s } ^ { 0 } + J _ { 1 s 2 s } \right) - 2 \times \left[ \left\langle \psi _ { 1 } ( 1 ) | \hat { h } ( 1 ) | \psi _ { 2 } ( 1 ) \right\rangle \left\langle \psi _ { 2 } ( 2 ) | \psi _ { 1 } ( 2 ) \right\rangle +\right. \right. \\
& \left. \left. \left\langle \psi _ { 1 } ( 1 ) | \psi _ { 2 } ( 1 ) \right\rangle \left\langle \psi _ { 2 } ( 2 ) | \hat { h } ( 2 ) | \psi _ { 1 } ( 2 ) \right\rangle + \left\langle \psi _ { 1 } ( 1 ) \psi _ { 2 } ( 2 ) \left| \frac { 1 } { r _ { 12 } } \right| \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) \right\rangle \right]  \right\}\\
={}& \frac { 1 } { 2 } \left\{ 2 \times \left( \varepsilon _ { 1 s } ^ { 0 } + \varepsilon _ { 2 s } ^ { 0 } + J _ { 1 s 2 s } \right) - 2 \times \left[ 0 + 0 + \left\langle \psi _ { 1 } ( 1 ) \psi _ { 2 } ( 2 ) \left| \frac { 1 } { r _ { 12 } } \right| \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) \right\rangle \right] \right\} \\
={}& \varepsilon _ { 1 s } ^ { 0 } + \varepsilon _ { 2 s } ^ { 0 } + J _ { 1 s 2 s } - K _ { 1 s 2 s }
\end{aligned}
$$
上式中的 $K_{1s 2s} = \left\langle \psi _ { 1 } ( 1 ) \psi _ { 2 } ( 2 ) \left| \frac { 1 } { r _ { 12 } } \right| \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) \right\rangle$ 即为交换能。

交换作用是指**同自旋**的两个电子之间存在的相互作用：
$$
\begin{aligned}
K _ { 1s 2s } ={}& \int \frac { \psi_ { 1 } ( 1 ) ^* \psi _ { 2 } ( 2 ) ^* \psi _ { 2 } ( 1 ) \psi _ { 1 } ( 2 ) } { r _ { 12 } } d q _ { 1 } d q _ { 2 } \\
={} & \int \frac { \varphi _ { 1 s } ( 1 ) ^ { * } \varphi _ { 2 s } ( 2 ) ^* \varphi _ { 2 s } ( 1 ) \varphi _ { 1 s } ( 2 ) } { r _ { 12 } } d \vec { r _ { 1 } } d \vec { r _ { 2 } } \int \eta _ { 1 } ( 1 ) ^ { * } \eta _ { 2 } ( 1 ) d \omega _ { 1 } \int \eta _ { 2 } ( 2 ) ^ { * } \eta _ { 1 } ( 2 ) d \omega _ { 2 }
\end{aligned}
$$

- 当 $\psi_1, \psi_2$ 同自旋， $\eta_1 = \eta_2$ ，$K \neq 0$ ($K>0$)；

- 当 $\psi_1, \psi_2$ 反自旋， $\eta_1 \neq \eta_2$ ，$K = 0$ 。

  这一项可以通过求 Slater 行列式的能量期待值得到。

**注**：$J_{11} - K_{11} = 0$ ，电子不存在自相关作用。

### 行列式波函数的 Pros

1. 行列式波函数部分地考虑了同自旋电子间的运动关联（不允许电子占据同一个自旋轨道）；
2. 同自旋电子间存在交换作用，它使总能量降低；
3. 多电子原子中，$n, l$ 相同的简并轨道上的电子，将分占磁量子数 $m$ 不同的轨道，并使其自旋平行（Hund 规则）

## Slater-Condon 规则

Slater-Condon 规则即为 Slater 行列式矩阵元的计算规则，

$$
\left\langle \Psi ^ { \prime } | \hat { O } | \Psi \right\rangle = \int \left[ \left( \Psi ^ { \prime } \right) ^* \hat { O } \Psi \right] d q _ { 1 } \cdots d q _ { N } = ?
$$

### 准备

1. 算符：

   1. 单电子算符：$ \hat { O } _ { 1 } = \sum _ { n } \hat { h } ( n ) $ ；
   2. 双电子算符： $ \hat { O } _ { 2 } = \sum _ { n < m } \frac { 1 } { r _ { n m } } $ 。

2. 行列式：

   1. 对角矩阵元：
      $$
      | \Psi ^ { \prime } \rangle = | \Psi \rangle \nonumber
      $$

   2. 非对角矩阵元 1:
      $$
      \begin{aligned} 
      | \Psi \rangle & = | \psi _ { 1 } \cdots \psi _ { k } \cdots \psi _ { N } \rangle \\ 
      | \Psi ^ { \prime } \rangle & = | \psi _ { 1 } \cdots \psi _ { a } \cdots \psi _ { N } \rangle \quad \text{单激发组态} \end{aligned}
      $$

   3. 非对角矩阵元 2:
      $$
      \begin{array} { l } { | \Psi \rangle = | \cdots \psi _ { k } \cdots \psi _ { l } \cdots \rangle } \\ { | \Psi ^ { \prime \prime } \rangle = | \dots \psi _ { a } \cdots \psi _ { b } \cdots \rangle } \quad \text{双激发组态} \end{array} \nonumber
      $$





### 规则

1. 重叠：

   1. 对角矩阵元：
      $$
      \langle \Psi | \Psi \rangle = 1
      $$

   2. 单激发态&双激发态：
      $$
      \left\langle \Psi ^ { \prime } | \Psi \right\rangle = 0
      $$

2. 单电子算符：

   1. 对角矩阵元：
      $$
      \left\langle \Psi \left| \hat { O } _ { 1 } \right| \Psi \right\rangle = \sum _ { i } \left\langle \psi _ { i } | \hat { h } | \psi _ { i } \right\rangle = \sum _ { i } \langle i | \hat { h } | i \rangle
      $$

   2. 单激发态：
      $$
      \left\langle \Psi ^ { \prime } \left| \hat { O } _ { 1 } \right| \Psi \right\rangle = \left\langle \psi _ { a } | \hat { h } | \psi _ { k } \right\rangle = \langle a | \hat { h } | k \rangle
      $$

   3. 双激发态：
      $$
      \left\langle \Psi ^ { \prime } \left| \hat { O } _ { 1 } \right| \Psi \right\rangle = 0
      $$

3. 双电子算符：

   1. 对角矩阵元：
      $$
      \begin{aligned} \left\langle \Psi \left| \hat { O } _ { 2 } \right| \Psi \right\rangle & = \frac { 1 } { 2 } \sum _ { i = 1 } ^ { N } \sum _ { j = 1 } ^ { N } \left\langle \psi _ { i } \psi _ { j } | \psi _ { i } \psi _ { j } \right\rangle - \left\langle \psi _ { i } \psi _ { j } | \psi _ { j } \psi _ { i } \right\rangle \\ & = \frac { 1 } { 2 } \sum _ { i = 1 } ^ { N } \sum _ { j = 1 } ^ { N } \langle i j | i j \rangle - \langle i j | j i \rangle \end{aligned}
      $$

   2. 单激发态：
      $$
      \left\langle \Psi ^ { \prime } \left| \hat { O } _ { 2 } \right| \Psi \right\rangle = \sum _ { i = 1 } ^ { N } \langle i a | i k \rangle - \langle i a | k i \rangle
      $$

   3. 双激发态：
      $$
      \left\langle \Psi ^ { \prime } \left| \hat { O } _ { 2 } \right| \Psi \right\rangle = \langle a b | k l \rangle - \langle a b | l k \rangle
      $$







# Hatree-Fock 方程

Hatree-Fock 方程（非正则形式）：
$$
\left[ \hat { h } ( 1 ) + \sum _ { j = 1 } ^ { N } \left( \hat { J } _ { j } ( 1 ) - \hat { K } _ { j } ( 1 ) \right) \right] \psi _ { i } ( 1 ) = \sum _ { j = 1 } ^ { N } \varepsilon _ { i j } \psi _ { j } ( 1 ) \label{eq:hf_ununitary}
$$
其中，库伦算符和交换算符：
$$
\begin{align}
\hat { J } _ { j } ( 1 ) \psi _ { i } ( 1 ) = \left[ \int \psi _ { j } ^ { * } ( 2 ) \frac { 1 } { r _ { 12 } } \psi _ { j } ( 2 ) d q _ { 2 } \right] \psi _ { i } ( 1 ) \\
 \hat { K } _ { j } ( 1 ) \psi _ { i } ( 1 ) = \left[ \int \psi _ { j } ^ { * } ( 2 ) \frac { 1 } { r _ { 12 } } \psi _ { i } ( 2 ) d q _ { 2 } \right] \psi _ { j } ( 1 )
 \end{align}
$$
$\eqref{eq:hf_ununitary}$ 中 $\hat { h } ( 1 ) + \sum _ { j = 1 } ^ { N } \left( \hat { J } _ { j } ( 1 ) - \hat { K } _ { j } ( 1 ) \right)$ 可用 Fock 算符 $\hat{f}(1)$ 简写代替。

经过 Unitary 变换， $\eqref{eq:hf_ununitary}$ 可以变换为正则形式，即：
$$
\hat { f } ( 1 ) \psi _ { i } ( 1 ) = \varepsilon _ { i } \psi _ { i } ( 1 )
$$

**注：$\eqref{eq:fock}$ 中的 $\hat { h } ( 1 ) = - \frac { 1 } { 2 } \nabla _ { 1 } ^ { 2 } - \sum _ { \alpha } \frac { Z _ { \alpha } } { r _ { 1 \alpha } } $ 表示核 Hamiltonian 项，是单电子算符，与 $\eqref{eq:mo}$ 中 $\hat{h}(1)$ 的含义有所区别，请注意区分。**

## Fock 算符的性质

Fock 算符：
$$
\hat{f}(1) = \hat { h } ( 1 ) + \sum _ { j = 1 } ^ { N } \left( \hat { J } _ { j } ( 1 ) - \hat { K } _ { j } ( 1 ) \right) \label{eq:fock}
$$

- Fock 算符是等效单电子的哈密顿算符，它的本征函数式分子轨道，本征值为轨道能；
- Fock 算符是 Hermitian 算符（因为交换算符和库仑算符都是 Hermitian 算符，动能项以及核势能项也都是 Hermitian 算符）；
- Fock 算符是分子点群的对称算符，分子轨道属于分子点群的不可约表示；
- Fock 算符之和 $\sum _ { n = 1 } ^ { N } \hat { f } ( n ) = \hat { H } ^ { H F } \neq \hat { H } _ { e l }$ ，它将电子间的作用重复计入。

## 轨道能与电子总能量

### 轨道能

$$
\varepsilon _ { i } = \left\langle \psi _ { i } | \hat { f } | \psi _ { i } \right\rangle
= \varepsilon _ { i } ^ { 0 } + \sum _ { j } ^ { N } \left( J _ { i j } - K _ { i j } \right) \label{eq:orb_en}
$$

$\eqref{eq:orb_en}$ 中：

- $\varepsilon_i^0$ 为 $\hat{h}(1)$ 的本征值， $\varepsilon_i$ 为第 $i$ 个轨道的轨道能；
- $J_{ij}=\langle ij|ij\rangle = \int dq_{1}dq_{2}\psi _{i}^{\star}(1)\psi _{j}^{\star}(2)\frac {1}{r_{12}}\psi _{i}(1)\psi _{j}(2)$ ；
- $K_{ij} = \langle ij|ji \rangle = \int dq_{1}dq_{2} \psi _ { i } ^ { \star } ( 1 ) \psi _ { j } ^ { \star } ( 2 ) \frac { 1 } { r _ { 12 } } \psi _ { j } ( 1 ) \psi _ { i } ( 2 )$ 。

### 电子总能量

$$
E _ { 0 } = \sum _ { i } ^ { N } \varepsilon _ { i } ^ { 0 } + \frac { 1 } { 2 } \sum _ { i } ^ { N } \sum _ { j } ^ { N } \left[ J _ { i j } - K _ { i j } \right] \label{eq:ele_en}
$$

$\eqref{eq:ele_en}$ 中第二项的 $\frac{1}{2}$ 表示去除因双重求和重复计入的交换能和库仑能 。

**注：分子轨道能之和不等于电子总能**
$$
\sum _ { i } ^ { N } \varepsilon _ { i } = \sum _ { i } ^ { N } \varepsilon _ { i } ^ { 0 } + \sum _ { i } ^ { N } \sum _ { j } ^ { N } \left[ J _ { i j } - K _ { i j } \right] \neq E _ { 0 } 
$$

## Koopmans 定理

假如从占据轨道 $\psi_k$ 上电离一个电子而其他轨道不变，则分子的电离势为 $-\varepsilon_k$ 。假定在空轨道 $\psi_r$ 上亲和一个电子而其他轨道不变，则分子的电子亲和势为 $\varepsilon_r$ ，简言之：当不考虑轨道弛豫时电离能/亲和能近似等于被电离/亲和电子的轨道能。

### 电离能

电离前：

$$
\begin{align}
&| \Psi _ { 0 } ^ { N } \rangle = | \psi _ { 1 } \cdots \psi _ { k } \cdots \psi _ { N } \rangle \nonumber \\
&E _ { 0 } = \left\langle \Psi _ { 0 } ^ { N } | \hat { H } | \Psi _ { 0 } ^ { N } \right\rangle = \sum _ { i } ^ { N } \varepsilon _ { i } ^ { 0 } + \frac { 1 } { 2 } \sum _ { i } \sum _ { j } \left( J _ { i j } - K _ { i j } \right) \nonumber
\end{align}
$$

电离后：
$$
\begin{align}
 | \Psi _ { k } ^ { N - 1 } \rangle ={}& | \psi _ { 1 } \cdots \psi _ { k - 1 } \psi _ { k + 1 } \cdots \psi _ { N } \rangle  \nonumber \\
 E _ { k } ^ { + } ={}& \left\langle \Psi _ { k } ^ { N - 1 } | \hat { H } | \Psi _ { k } ^ { N - 1 } \right\rangle = \sum _ { i \neq k } \varepsilon _ { i } ^ { 0 } + \frac { 1 } { 2 } \sum _ { i \neq k } \sum _ { j \neq k } \left( J _ { i j } - K _ { i j } \right) \nonumber
\end{align}
$$

则电离能：
$$
\begin{align}
I.P. ={}& E _ { k } ^ { + } - E _ { 0 } \\
={}& - \varepsilon _ { k } ^ { 0 } - \frac { 1 } { 2 } \left[ \sum _ { j } \left( J _ { k j } - K _ { k j } \right) + \sum _ { i } \left( J _ { i k } - K _ { i k } \right) \right] \\
={}& - \varepsilon _ { k } ^ { 0 } - \sum _ { j } \left( J _ { k j } - K _ { k j } \right) = - \varepsilon _ { k }
\end{align}
$$

### 亲和能

与电离能同理， 
$$
E . A . = E _ { 0 } - E _ { r } ^ { N + 1 } = - \varepsilon _ { r } ^ { 0 } - \sum _ { j } \left( J _ { r j } - K _ { j r } \right) = - \varepsilon _ { r }
$$

Koopmans 定理提供了一种近似求解 $I.P$ 与 $E.A.$ 的方法，但它不考虑电离/亲和后的轨道弛豫和电子的相关效应（事实上整个 Hatree-Fock 近似也没有考虑相关效应），这样求得的电离能与亲和能有误差。

# Roothan 方程

Roothan 方程的本质是将 Hatree-Fock 方程的分子轨道用一系列基函数展开得到的方程。

## 限制性与非限制性自旋轨道

限制性自旋轨道：假设同一个分子轨道分为两个自旋相反的自旋轨道，它们的空间轨道部分完全相同。限制性自旋轨道一般用于描述闭壳层的电子行为。
$$
\psi _ { a } \left( q _ { 1 } \right) \longrightarrow \left\{ \begin{array} { l } { \varphi _ { i } \left( \vec { r } _ { 1 } \right) \alpha \left( \omega _ { 1 } \right) } \\ { \varphi _ { i } \left( \vec { r } _ { 1 } \right) \beta \left( \omega _ { 1 } \right) } \end{array} \right.
$$
非限制性自旋轨道：同一个分子轨道中自旋轨道的空间轨道部分不同。
$$
\psi _ { a } \left( q _ { 1 } \right) \longrightarrow \left\{ \begin{array} { l } { \varphi _ { i } \left( \vec { r } _ { 1 } \right) \alpha \left( \omega _ { 1 } \right) } \\ { \varphi _ { i } ^ {\color{red} \prime } \left( \vec { r } _ { 1 } \right) \beta \left( \omega _ { 1 } \right) } \end{array} \right.
$$
非限制性自旋轨道一般用于描述开壳层的电子行为。

## 空间轨道的 HF 方程

空间轨道的 Hatree-Fock 方程为：
$$
\hat { f } \left( \vec { r } _ { 1 } \right) \varphi _ { i } \left( \vec { r } _ { 1 } \right) = \varepsilon _ { i } \varphi _ { i } \left( \vec { r } _ { 1 } \right) \label{eq:hf_space}
$$
其中空间轨道的 Fock 算符为：
$$
\begin{aligned} { f \left( \vec { r } _ { 1 } \right) = \hat { h } \left( \vec { r } _ { 1 } \right) + \sum _ { j = 1 } ^ { N / 2 } 2 \hat { J } _ { j } \left( \vec { r } _ { 1 } \right) - \hat { K } _ { j } \left( \vec { r } _ { 1 } \right) } \\ { \hat { J } _ { j } \left( \vec { r } _ { 1 } \right) \varphi _ { i } \left( \vec { r } _ { 1 } \right) = \left[ \int \frac { \varphi _ { j } ^ { * } \left( \vec { r } _ { 2 } \right) \varphi _ { j } \left( \vec { r } _ { 2 } \right) } { r _ { 12 } } d \vec { r } _ { 2 } \right] \varphi _ { i } \left( \vec { r } _ { 1 } \right) } \\ { \hat { K } _ { j } \left( \vec { r } _ { 1 } \right) \varphi _ { i } \left( \vec { r } _ { 1 } \right) = \left[ \int \frac { \varphi _ { j } \left( \vec { r } _ { 2 } \right) \varphi _ { i } \left( \vec { r } _ { 2 } \right) } { r _ { 12 } } d \vec { r _ { 2 } } \right] \varphi _ { j } \left( \vec { r } _ { 1 } \right) } \end{aligned}
$$
上面式子中 $ \hat{K} $ 项前面没有 2 是因为该波函数为限制性自旋波函数，体系为闭壳层，自旋向上和自旋向下的电子个数相同，恰好有一半的空间轨道有电子占据，且这些空间轨道都已经占满，故只有自旋平行的电子之间有交换作用（即只有 $\frac{N}{2}$ 个电子之间有交换作用）。

分子轨道的轨道能（自旋轨道）：
$$
\varepsilon_i =   \varepsilon _ { i } ^ { 0 } + \sum _ { j } ^ { N } \left( J _ { i j } - K _ { i j } \right)
$$
分子轨道的轨道能（空间轨道，闭壳层限制性）：
$$
\varepsilon_i = \varepsilon _ { i } ^ { 0 } + \sum _ { j } ^ { N / 2 } \left( 2 J _ { i j } - K _ { i j } \right)
$$
电子总能量（自旋轨道）：
$$
E_0= \sum _ { i } ^ { N } h _ { i i } + \frac { 1 } { 2 } \sum _ { i } ^ { N } \sum _ { j } ^ { N } J _ { i j } - K _ { i j }
$$
电子总能量（空间轨道，闭壳层限制性）：
$$
E _ 0 = \sum _ { i } ^ { N / 2 } 2 h _ { i i } + \frac { 1 } { 2 } \sum _ { i } ^ { N / 2 } \sum _ { j } ^ { N / 2 } 2 J _ { i j } - K _ { i j }
$$
上式中第二项前的 $\frac{1}{2}$ 表示已经减去重复计入的空间轨道的相互作用。

## Roothaan 方程

引入一组**已知**的基函数将空间轨道展开：
$$
\varphi _ { i } = \sum _ { v = 1 } ^ { m } C _ { vi } \chi _ { v } \quad i = 1,2 , \cdots , m  \label{eq:roothaan_base}
$$
将 $\eqref{eq:roothaan_base}$ 代入 $\eqref{eq:hf_space}$ 可以得到：
$$
\hat { f } \left( \vec { r } _ { 1 } \right) \varphi _ { i } \left( \vec { r } _ { 1 } \right) = \varepsilon _ { i } \varphi _ { i } \left( \vec { r } _ { 1 } \right)  \quad i = 1,2 , \cdots , m
$$
上式左乘 $\chi_{\mu}^* (1)$ 并积分，得到：
$$
\sum _ { v } ^ { m } C _ { v i } \langle \chi _ { \mu } ( 1 ) | \hat { f } ( 1 ) | \chi _ { v } ( 1 ) \rangle = \varepsilon _ { i } \sum _ { v } ^ { m } C _ { v i } \langle \chi _ { \mu } ( 1 ) | \chi _ { v } ( 1 ) \rangle \quad i = 1,2 , \cdots , m
$$
令 $ S _ { \mu \nu } = \langle \chi _ { \mu } ( 1 ) | \chi _ { v } ( 1 ) \rangle = \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \chi _ { v } ( 1 ) $ ，

$ F _ { \mu v } = \langle \chi _ { \mu } ( 1 ) | \hat { f } ( 1 ) | \chi _ { v } ( 1 ) \rangle = \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \hat { f } ( 1 ) \chi _ { v } ( 1 ) $ 

由此可以得到方程组：
$$
\sum _ { v } ^ { m } F _ { \mu \nu } C _ { v i } = \varepsilon _ { i } \sum _ { v } ^ { m } S _ { \mu \nu } C _ { v i } \quad i = 1,2 , \cdots , m
$$
或者写成矩阵形式：
$$
\mathbf { F C } _ { i } = \varepsilon _ { i } \mathbf { S } \mathbf { C } _ { i } \quad i = 1,2 , \cdots , m
$$
合并写成矩阵方程：
$$
\mathbf { F C } = \mathbf { S } \mathbf { C } \boldsymbol { \varepsilon } \tag{*} \label{eq:roothaan}
$$
$\eqref{eq:roothaan}​$ 即为 Roothaan 方程。

其中：
$$
\mathbf { C } = \left( \begin{array} { c c c c } { C _ { 11 } } & { C _ { 12 } } & { \cdots } & { C _ { 1 m } } \\ { C _ { 21 } } & { C _ { 22 } } & { \cdots } & { C _ { 2 m } } \\ { C _ { 31 } } & { C _ { 32 } } & { \cdots } & { C _ { 3 m } } \\ { \vdots } & { \vdots } & { } & { \vdots } \\ { C _ { m 1 } } & { C _ { m 2 } } & { \cdots } & { C _ { m m } } \end{array} \right) ,\quad 
\boldsymbol { \varepsilon } = \left( \begin{array} { c c c c } { \varepsilon _ { 1 } } & { } & { } & { O } \\ { } & { \varepsilon _ { 2 } } & { } & { } \\ { } & { } & { \ddots } & { } \\ { O } & { } & { } & { \varepsilon _ { m } } \end{array} \right)
$$
它们分别表示分子轨道（空间轨道）和轨道能。

$C_{ij}$ 表示第 $j$ 个分子轨道（空间轨道）第 $i$ 个基函数的系数。

### 重叠矩阵

$$
S _ { \mu \nu } = \langle \chi _ { \mu } ^ { * } ( 1 ) | \chi _ { v } ( 1 ) \rangle = \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \chi _ { v } ( 1 )
$$

且
$$
S _ { \mu \nu } ^ { * } = \left[ \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \chi _ { v } ( 1 ) \right] ^ { * } = \int d \vec { r } _ { 1 } \chi _ { v } ^ { * } ( 1 ) \chi _ { \mu } ( 1 ) = S _ { v \mu }
$$
故 $\mathbf{S}$ 为一个 $m \times m$ 的 Hermitian 矩阵，且 $0 \leq \left| S _ { \mu\nu } \right| \leq 1$

### Fock矩阵

$$
\begin{aligned}
\mathbf{F} _ { \mu \nu } ={}& \langle \chi _ { \mu } ^ { * } ( 1 ) \hat { f } ( 1 ) \chi _ { v } ( 1 ) \rangle \\
={}& \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \hat { f } ( 1 ) \chi _ { v } ( 1 ) \\
={} & h _ { \mu v } ^ { c o r e } + \sum _ { j } ^ { N / 2 } \int d \vec { r } _ { 1 } \chi _ { \mu } ^ { * } ( 1 ) \left[ 2 \hat { J } _ { j } ( 1 ) - \hat { K } _ { j } ( 1 ) \right] \chi _ { v } ( 1 )
\end{aligned}
$$

令 $\varphi _ { j } = \sum _ { \sigma } ^ { m } C _ { \sigma j } \chi _ { \sigma }$ ，$ \varphi _ { j } ^ { * } = \sum _ { \lambda } ^ { m } C _ { \lambda j } ^ { * } \chi _ { \lambda } ^ { * } $  ，则
$$
\begin{aligned}
\int \chi _ { \mu } ^ { * } ( 1 ) \hat { J } _ { j } ( 1 ) \chi _ { v } ( 1 ) d \vec { r } _ { 1 } = \sum _ { \lambda } ^ { m } \sum _ { \sigma } ^ { m } C _ { \sigma j } C _ { \lambda j } ^ { * } \langle \mu v | \lambda \sigma \rangle \\
\int \chi _ { \mu } ^ { * } ( 1 ) \hat { K } _ { j } ( 1 ) \chi _ { v } ( 1 ) d \vec { r } _ { 1 } = \sum _ { \lambda } ^ { m } \sum _ { \sigma } ^ { m } C _ { \sigma j } C _ { \lambda j } ^ { * } \langle \mu {\color{red} \sigma} | \lambda {\color{red} v} \rangle
\end{aligned}
$$
所以 Fock 矩阵的矩阵元可以进一步写成
$$
\begin{aligned}
F _ { \mu \nu } ={}& h _ { \mu \nu } ^ { c o r e } + \sum _ { \lambda , \sigma } ^ { m , m } \sum _ { j } ^ { N / 2 } C _ { \sigma j } C _ { \lambda j } ^ { * } [ 2 ( \mu v | \lambda \sigma ) - ( \mu \sigma | \lambda v ) ] \\
={}& h _ { \mu \nu } ^ { c o r e } + \sum _ { \lambda , \sigma } ^ { m , m } P _ { \sigma \lambda } [ 2 ( \mu v | \lambda \sigma ) - ( \mu \sigma | \lambda v ) ] \\
={}& h _ { \mu \nu } ^ { c o r e } + G _ { \mu \nu }
\end{aligned}
$$
$G_{\mu\nu}$ 矩阵即为 Fock 矩阵的双电子项，由密度矩阵 $P_{\sigma \lambda}$和基函数的双电子积分给出。 

### 密度矩阵

定义密度矩阵：
$$
P _ { \sigma \lambda } = \sum _ { j } ^ { N / 2 } C _ { \sigma j } C _ { \lambda j } ^ { * } = \sum _ { j } ^ { N / 2 } ( C ) _ { \sigma j } \left( C ^ { \dagger } \right) _ { j \lambda }
$$
$C$ 是分子轨道基函数的展开系数。

由于闭壳层的限制性，只有 $N/2$ 个空间轨道占有电子，且都占满，故密度矩阵通常等于
$$
P = C _ { 0 } C _ { 0 } ^ { \dagger } = \left( \begin{array} { c c c } { \vdots } & { } & { } \\ { c _ { \sigma 1 } } & { \dots } & { c _ { \sigma N / 2 } } \\ { \vdots } & { } & { } \end{array} \right) \left( \begin{array} { c c c } { } & { c _ { \lambda 1 } ^ { * } } \\ { \ldots } & { \vdots } & { \cdots } \\ { } & { c _ { \lambda N / 2 } ^ { * } } \end{array} \right)
$$

## 基的幺正化

Roothaan 方程 $\mathbf { F C } = \mathbf { S } \mathbf { C\varepsilon } $  不是标准的矩阵本征值方程，如果 $\mathbf{S}  = 1$，则 $\mathbf { F C } = \mathbf { C } \varepsilon$  是标准的本征值方程。所以要对 Roothaan 方程进行  Unitary 变换使其满足标准本征值方程，才能进行求解。

构造变换矩阵 $\mathbf{X}​$ 使得 
$$
\mathbf { X } ^ { \dagger } \mathbf { S X } = \mathbf { S } ^ { \prime } = \mathbf { I }
$$

则构造变换后的 Fock 矩阵 $\mathbf{F}'$

$$
\mathbf { F } ^ { \prime } = \mathbf { X } ^ { + } \mathbf { F } \mathbf { X }
$$
继续假设原系数矩阵 $\mathbf { C } = \mathbf { X } \mathbf { C } ^ { \prime }$ ，此时得到变换后的 Roothaan 方程：
$$
\begin{aligned}
\mathbf { F X C } ^ { \prime } ={}& \mathbf { S X C ^ { \prime } \varepsilon } \\
\left( \mathbf { X } ^ { + } \mathbf { F } \mathbf { X } \right) \mathbf { C } ^ { \prime } ={}& \left( \mathbf { X } ^ { + } \mathbf { S X } \right) \mathbf { C } ^ { \prime } \boldsymbol { \varepsilon }\\
\mathbf { F } ^ { \prime } \mathbf { C } ^ { \prime } ={}& \mathbf { C } ^ { \prime } \boldsymbol { \varepsilon }
\end{aligned}
$$
此时对角化 Fock 矩阵 $\mathbf{F}'$ ，即可得到系数矩阵 $\mathbf C'$ 和本征值 $\boldsymbol{\varepsilon}$ 。 

## SCF 迭代步骤

1. 给定分子的初始信息（核位置 $\vec{R}_\alpha$，元素种类 $\{Z_{\alpha}\}$ ，电子个数 $N_{elec}$ ，以及基函数 $\left\{ \chi _ { v } \right\}$ ）；
2. 计算分子积分 $S _ { \mu \nu } , \quad h _ { \mu \nu } ^ { \text { core } } , \langle \mu v | \lambda \sigma \rangle$ ；
3. 幺正化 $\mathbf{S}$ 矩阵，得到变换矩阵 $\mathbf{X}$ ；
4. **猜**一个初始密度矩阵 $\mathbf{P}$ ；
5. 由密度矩阵 $\mathbf{P}$ 和双电子积分计算 $\mathbf{G}$ 矩阵；
6. 构造 Fock 矩阵 $ \mathbf { F } = \mathbf { h } ^ { \mathrm { core } } + \mathbf { G } $ ；
7. 计算变换后的 Fock 矩阵 $\mathbf { F } ^ { \prime } = \mathbf { X } ^ { + } \mathbf { F } \mathbf { X }$ ；
8. 对角化 $\mathbf{F}'$ 得到 $\mathbf{C}'$ 和 $\boldsymbol{\varepsilon}$ ；
9. 计算系数矩阵 $\mathbf { C } = \mathbf { X } \mathbf { C } ^ { \prime }$ ；
10. 构造密度矩阵 $\mathbf{P}$ ： $P _ { \mu } = \sum _ { j } ^ { N / 2 } C _ { \mu } C _ { v j } ^ { * }$ ；
11. 验证密度矩阵 $\mathbf{P}$ 和能量 $\varepsilon$ 是否收敛，若未收敛，返回步骤 5，用刚得到的密度矩阵 $\mathbf{P}$ 计算 $\mathbf{G}$ 矩阵；
12. 计算已经收敛，迭代结束，计算能量期待值与其它性质。

## 基本计算结果

1. 轨道能与电子能量；
2. 势能面、构型优化、振动频率分析；
3. 单电子性质（如分子偶极矩）；
4. 电荷密度计算等。

# 总结

Hatree-Fock 方法的几个关键点：

1. 使用 Slater 行列式描述分子的波函数；
2. 使用基函数将分子轨道展开，便于计算；
3. 使用自洽场方法迭代计算；
4. $J_{11} - K_{11} = 0$ ，没有自相关作用。
