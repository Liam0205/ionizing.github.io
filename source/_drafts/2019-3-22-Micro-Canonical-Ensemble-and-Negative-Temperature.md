---
title: 微正则系综与负温度的导出
tags:
	- Statistical Mechanics
	- Physical Chemistry
	- Negative Temperature
---

# 微正则系综

## 基本概念

微正则系综是指参量为 $N​$ $V​$ $E​$ 的体系，对应于宏观的孤立体系，即「在宏观看来」，体系的粒子数、体积、和内能都不改变。$\newcommand{\dif}{\mathop{}\mathrm{d}}​$ 

上一篇博文中我们已经知道，统计力学中存在两个假设，其中一个假设是：微正则系综中各个状态出现的概率相等，用数学语言表达就是：
$$
P_{\nu} = \frac{1}{\varOmega(N,V,E)}
$$
其中 $\nu$ 表示某个状态， $\varOmega(N, V, E)$ 表示系统参量为 $N$ 、 $V$ 、 $E$ 时所拥有的状态数。

由玻尔兹曼关系式，体系的熵可以表达为
$$
S = k\ln \varOmega(N, V, E)
$$

## 基本流程

使用正则系综研究某个体系时我们遵循下面的流程：

1. 求体系的微观态数 $\varOmega$ ；
2. 求体系的热力学量均值 $\langle X \rangle$ ；
3. 求体系的热力学量涨落（方差， $\langle (\delta X)^2 \rangle$ ）。

注：本文所讨论的对象都是在单组分理想气体的假设上进行的，即所研究体系只由同一种粒子组成，粒子之间**没有关联**。

## 三维势箱的例子

假想我们把理想气体放在一个长宽高均为 $a​$ 的密闭、绝热、体积不变的箱子中，这个箱子中的气体可以看作一个孤立体系，气体的粒子是自由粒子，它们之间的运动无关联。

我们假设这个 $a$ 是 m 的量级，即箱子为宏观尺度上的箱子，体系的粒子数为 $N$ ，体积为 $V$ ，内能为 $E$ 。

下面开始求这个体系的的状态数 $\varOmega(N, V, E)$。

### 当体系只有一个粒子时

如果体系只有一个粒子，那么粒子的能级为
$$
\epsilon_{n_x, n_y, n_z} = \frac{h^2}{8ma^2}(n_x^2 + n_y^2 + n_z^2)
$$
上面式子中

- $h$ —— 普朗克常量， $6.626\times 10^{-34}$ J*s ；
- $m$ —— 粒子质量，g ；
- $n_x$ , $n_y$ , $n_z$ —— $x$ , $y$ , $z​$ 方向上的量子数， $n_x, n_y, n_z \in N_+$ ，无量纲。（如果不明白这个公式如何推出来，可以参考[Particle in a box](https://en.wikipedia.org/wiki/Particle_in_a_box) ）

假设给定一个能级 $\epsilon$ ，那么在 $0 \sim \epsilon$ 之间这个粒子存在多少个状态呢？

显然这个数目应该等于所有所有满足

$$
n_x^2 + n_y^2 + n_z^2 \le \frac{8ma^2\epsilon}{h^2} \label{eq:4}
$$
的 \[$n_x$, $n_y$, $n_z$\] 组合的数量。

如何计算这个数量？当然编程用回溯法不难穷举出所有可能的组合，但是我们不需要知道所有组合具体是什么样，我们只需知道些组合的数量！

$n_x^2 + n_y^2 + n_z^2$ ，好熟悉的公式，这不就是三维空间中点 $(n_x, n_y, n_z)$ 到原点 $O$ 的距离平方吗？再次审视 $\eqref{eq:4}$ ，它表示的是一个球在第一卦限内的部分， $\eqref{eq:4}$ 取等号时所表示的面是八分之一个球面，球面半径为
$$
R = \sqrt{\frac{8ma^2\epsilon}{h^2}}
$$


我们的任务是求它们组合的个数，也就是求这八分之一球内部有多少个坐标全为正整数的点；当 $\epsilon$ 取值比较大时，球面部分的 aliasing 可以忽略，我们认为这八分之一球内坐标为整数的点的数量等于这八分之一球的体积。

于是问题变得简单起来，在 $0 \sim \epsilon$ 之间
$$
\begin{aligned}
\varPhi(\epsilon) &={} \frac{1}{8} \cdot \frac{4\pi}{3} R^3 \\
	&={} \frac{1}{8} \cdot \frac{4\pi}{3} \left( \frac{8ma^2\epsilon}{h^2} \right)^{\frac{3}{2}}
\end{aligned}
$$
那么在 $\epsilon \sim \epsilon + \dif \epsilon​$ 之间
$$
\begin{aligned}
	\varOmega(\epsilon) &={} \overline{\varOmega}(\epsilon) \dif \epsilon \\
		&={} \frac{\dif}{\dif \epsilon} \varOmega(\epsilon) \dif \epsilon \\
		&={} \frac{\dif}{\dif \epsilon} \frac{\pi}{6} \left( \frac{8ma^2\epsilon}{h^2} \right)^{\frac{3}{2}} \dif \epsilon \\
		&={} \frac{\pi}{6} \left( \frac{8ma^2}{h^2} \right)^{\frac{3}{2}} \cdot \frac{3}{2} \epsilon^{\frac{1}{2}} \dif \epsilon \\
		&={} \frac{\pi}{4} \left( \frac{8ma^2}{h^2} \right)^{\frac{3}{2}} \cdot \epsilon^{\frac{1}{2}} \dif \epsilon
\end{aligned}
$$
当然我们也可以直接用球面面积公式计算 $\varOmega(\epsilon)$ ，得到的结果和上面的一样。

### 当体系有 $N$ 个粒子时

我们认为这 $N$ 个粒子是[全同](https://en.wikipedia.org/wiki/Identical_particles)，即不可分辨的，同时我们要描述这个系统的某个状态需要知道所有粒子的量子数，所以体系的总量子数 $\{n\}$ 就从 3 个变成了 3 $N$ 个，此时能级的计算公式将变成
$$
E(\{n_j\}) = \frac{h^2}{8ma^2} \sum_{j=1}^{3N} n_j^2
$$
$\{n_j\}$ 所存在的空间不再是三维，而是 $3N$ 维，[谷歌](https://en.wikipedia.org/wiki/Volume_of_an_n-ball)告诉我们 $3N$ 维空间中球的体积公式为
$$
V_{3N}(R) = \frac{\pi^{3N/2}}{\Gamma(\frac{3N}{2} + 1)} \cdot R^{3N}
$$
其中 $\Gamma(\frac{3N}{2} + 1)$ 是一个 [Gamma 函数](https://en.wikipedia.org/wiki/Gamma_function) ， 

$$
\Gamma(x) = \int_{0}^{+\infty}t^{x-1} e^{-t} \dif t
$$

它满足

- $\Gamma(0) = 0$ ；
- $\Gamma(\frac{1}{2}) = \sqrt{\pi}​$ ；
- $\Gamma(x+1) = x\cdot\Gamma(x)$ 。（目前只需要这些性质，更深入的部分本人也没兴趣去研究）

那么在这个球的"第一卦限"内的体积为这个球的 $\frac{1}{2^{3N}}$ ，于是在 $0 \sim E 之间
$$
\varPhi(E) = \frac{1}{2^{3N} \cdot N!} V_{3N}(R)
$$

而
$$
\begin{aligned}
	R^2 &={} \sum_j n_j^2\\
	E(\{n_j\}) &={} \frac{h^2}{8ma^2} R^2
\end{aligned}
$$
上面式子导出
$$
R = \sqrt{\frac{8ma^2}{h^2}E}
$$
那么在 $E \sim \dif E$ 之间，体系的状态数为
$$
\begin{aligned}
\varOmega(E) &={} \frac{\dif}{\dif E} \varPhi(E) \dif E \\
	&={}  \frac{1}{2^{3N} \cdot N!} \cdot \frac{\pi^{3N/2}}{\Gamma(\frac{3N}{2} + 1)} \frac{\dif}{\dif E} \left( \frac{8ma^2}{h^2}E \right)^{\frac{3N}{2}} \dif E \\
	&={} \frac{1}{2^{3N} \cdot N!} \cdot \frac{\pi^{3N/2}}{\Gamma(\frac{3N}{2} + 1)} \left( \frac{8ma^2}{h^2} \right)^{\frac{3N}{2}} \cdot \frac{3N}{2} \cdot E^{\frac{3N}{2}} \frac{\dif E}{E} \\
	&={} \frac{1}{N!} \cdot \frac{1 }{ \Gamma(\frac{3N}{2})} \cdot \left( \frac{2 \pi ma^2}{h^2} \right)^{\frac{3N}{2}} E^{\frac{3N}{2}} \frac{\dif E}{E} \\
	&={} \frac{1}{N!} \cdot \frac{a^{3N}}{\Gamma(\frac{3N}{2})} \cdot \left( \frac{2 \pi mE}{h^2} \right)^{\frac{3N}{2}} \frac{\dif E}{E} \\
	&={} \frac{1}{N!} \cdot \frac{V^{N}}{\Gamma(\frac{3N}{2})} \cdot \left( \frac{2 \pi mE}{h^2} \right)^{\frac{3N}{2}} \frac{\dif E}{E}
\end{aligned}
$$
下面来解决 $\Gamma(\frac{3N}{2})$ 值的问题。

根据 $\Gamma(x+1) = x\Gamma(x)$ ，可以得到 $\Gamma(\frac{3N}{2}) = (\frac{3N}{2} - 1) \cdot \Gamma(\frac{3N}{2} - 1) = (\frac{3N}{2} - 1)!$ 

于是 $\Omega(E)​$ 中 $N! \cdot \Gamma(\frac{3N}{2})​$ 可以使用[斯特灵近似](https://en.wikipedia.org/wiki/Stirling%27s_approximation)来计算
$$
\begin{aligned}
	\verb|let|\quad X &={} N!\cdot \left(\frac{3N}{2} - 1\right)! \\
	\ln X &={}N\ln N - N + \left(\frac{3N}{2}-1\right) \ln \left(\frac{3N}{2}-1\right) - \left(\frac{3N}{2} - 1\right) \\
	&\sim{} N\ln N + \frac{3N}{2}\ln\frac{3N}{2} \\
	&\sim{} \frac{5N}{2}\ln N \\
\end{aligned}
$$
为了式子的简洁，我们把不需要关心的部分放到 $f(N)$ 中，表示含 $N$ 的系数， $\varOmega(E)$ 可以化简为
$$
\ln \varOmega(E) = f(N) + N\ln V + \frac{3N}{2}\ln E + \ln\frac{\dif E}{E}
$$
此时使用热力学基本公式的变形
$$
\dif \ln \varOmega = \beta \dif E + \beta p\dif V - \beta \mu\dif N
$$
可以得到以下热力学量
$$
\begin{aligned}
	\beta &={} \frac{1}{kT} = \left(\frac{\partial \ln\varOmega}{\partial E}\right)_{N, V} = \frac{3N}{2} \cdot \frac{1}{E} \\
	&\Longrightarrow {} E = \frac{3}{2} NkT ;\\
	p\beta &={} \frac{p}{kT} = \left(\frac{\partial \ln\varOmega}{\partial V}\right)_{N, E} = \frac{N}{V} \\
	&\Longrightarrow {} p = \frac{NkT}{V} \\
	&\Longrightarrow {} pV = NkT = \frac{NRT}{N_A} = nRT . \\
\end{aligned}
$$
这和理想气体状态方程相吻合（如果不吻合问题就很大了）。