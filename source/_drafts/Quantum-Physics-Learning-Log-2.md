---
title: 量子力学学习手记（二）——量子力学假设
date: 2017-08-15 16:08:32
tags:
   - 量子力学
categories: Quantum Mechanics
---

# 量子力学学习手记（2）—量子力学假设

**以下是在不考虑相对论的情况下进行的量子力学假设。** 

为了使问题简化，我们会先讨论自由度为 **1** 的系统状况，很自然地，这个系统包含一个粒子，并且该粒子存在于一维空间中，此时我们会进行一些假设，根据假设对这个系统进行相应的计算，取其结果与经典力学的结果进行对比；之后，我们会将假设推广到多维系统以及多个粒子的系统中去。

-----

接下来要阐述的是量子力学的四个基本假设与经典力学假设的对比：

## 假设 I

经典力学：	一个粒子在任意时刻下的状态由两个变量决定：$x(t)$ 和 $p(t)$ ，这就像在一个二维空间确定一个点需要两个坐标一样；

量子力学：	粒子的状态用希尔伯特空间中的向量 $\mid \psi(t) \rangle$ 表示。

## 假设 II

经典力学：	任何动力学变量 $\omega$ 都是 $x$ 和 $p$ 的函数： $\omega = \omega(x,p)$ ；

量子力学：	经典力学中的独立变量 $x$ 和 $p$ 在量子力学中由厄米算符 $X$ , $P$ 以及下面矩阵的元素代替：
$$
\langle x\mid X\mid x'\rangle = x\delta(x-x') \\\\
\langle x\mid P\mid x'\rangle = -i\hbar\delta(x-x')
$$
​			而经典力学中的非独立变量如$\omega(x,p)$ 则用下面的厄米算符表示：
$$
\Omega(X,P) = \omega(x\rightarrow X, p\rightarrow P)
$$

## 假设 III

经典力学：	如果粒子的状态由给定的 $x​$ 和 $p​$ 所确定，则对 $\omega​$ 的测量将产生一个值 $\omega(x,p)​$ ，并且该系统的状态不会被改变；

量子力学：	如果粒子的状态为 $\mid \psi \rangle$ ，则外界对于 $\Omega$ 的测量行为有 $P(\omega) \propto |\langle \omega \mid \psi\rangle|^2$ 的概率得到 $\Omega$ 的一个特征值 $\omega$ 。**并且由于测量行为，该系统的状态将会从 $\mid\psi\rangle$ 变为 $\mid \omega \rangle$ **。

## 假设 IV

经典力学：	变量随时间的变化规律满足哈密顿方程：
$$
\dot{x} = \frac{\partial \mathscr{H} }{\partial p} \\\\
\dot{p} = -\frac{\partial \mathscr{H} }{\partial x}
$$
量子力学：	状态向量 $\mid \psi(t) \rangle$ 服从薛定谔方程：
$$
i\hbar \frac{\mathrm d}{\mathrm dt}\mid \psi(t) \rangle = H\mid\psi(t)\rangle
$$
​			其中 $H(X,P) = \mathscr{H}(x\rightarrow X, p\rightarrow P)$ 是量子力学中的哈密顿算符，而 $\mathscr{H}$ 是经典理论中的哈密顿算符。



以上四个假设对于量子力学 **非常重要** ，每天早起背一遍都不为过。

------

下面我们来讨论这些假设。

## 