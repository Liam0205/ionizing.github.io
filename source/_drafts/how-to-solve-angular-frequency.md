---
title: 如何求摆的角频率？
tags:
	- 物理学
	- 振动
categories: Physics
---

[TOC]

# 什么是摆？

## 什么样的运动称之为简谐运动？

让我们来先看一个例子：

<--有一单摆，即在一个细线下面悬挂一个可以视为质点的小球（忽略小球的自转），给小球一个很小的水平初速度，小球将在竖直平面内（忽略科里奥利力）做小角度的摆动并且忽略一切阻力。

设细线长为 $l$ ，小球质量为 $m$ ，重力加速度为 $g$ ，画出示意图如下：



很容易看出摆锤（小球）的重力势能是：
$$
E_{\rm p重} = mgl(1-\cos\theta)
$$
摆锤的速度
$$
v = l \omega = l\cdot\frac{\mathrm d \theta}{\mathrm d t} = l\dot{\theta}
$$
摆锤的动能
$$
E_{k} = \frac 12 m l^2 \dot{\theta}^2
$$
在摆动过程中没有外界能量输入，由能量守恒
$$
\begin{aligned}
E &= E_{\rm k} + E_{\rm p 重} \\
&= \frac 12 m l^2 \dot{\theta}^2 + mgl(1-\cos\theta)\\
&= \rm Constant
\end{aligned}
$$

即可解得
$$
\dot{\theta} = \pm \sqrt{\frac{2g}{l} (\frac{E}{mgl} - 1 + \cos\theta) }
$$

-->