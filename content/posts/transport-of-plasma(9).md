---
title: "等离子体输运理论(9)"
date: 2026-08-15
draft: false
math: true
series: ['plasma-transport']
series_order: 9
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# Hermite 矩估计

## 准中性近似

### 特征时间尺度

**动理方程**：
$$
\partial_t f^a = \Phi^a + \mathscr{F}^a + \mathscr{K}^a
$$
上一章已经充分论述严格求解之不可能，因此要采取近似。

回忆第二章讨论的特征时间尺度，有：
$$
\frac{1}{\tau_H^a} \sim \frac{V_{Ta}}{L_H}
$$
$\tau_H^a$ 为流体力学特征时间，$L_H$ 为特征长度，且对于任意的流体力学量与电磁学量，有
$$
\frac{1}{L_H} \approx \mathrm{max} \left| \frac{\nabla A(x)}{A(x)} \right|
$$
梯度由仪器设备决定，一般很大，所以特征长度要小得多，则流体力学时间会很长。

### 前 Maxwell 方程组

只考虑慢变电磁场，我们可以将任意量分解为快变量与慢变量：
$$
A = A_S + A_F
$$
$$
\partial_t A_S = \Phi_S(A_S, A_F), \qquad \partial_t A_F = \Phi_F(A_S, A_F)
$$

使用这个假设可以将电荷密度 $\sigma$ 在方程组中忽略掉。考虑 Maxwell 方程组的两项：
$$
\nabla \times \boldsymbol{E} = \frac{1}{c} \partial_t \boldsymbol{B}
$$
$$
\nabla \times \boldsymbol{B} = \partial_t \boldsymbol{E} + \frac{4\pi}{c} \boldsymbol{j}
$$
得到估计：
$$
\frac{|E|}{L_H} \approx \frac{|B|}{c\tau_H}, \qquad \frac{|B|}{L_H} \approx \frac{|E|}{c\tau_H} + \frac{4\pi |j|}{c}
$$
可以推断出：
$$
\left| \frac{1}{c} \partial_t E \right| \approx \frac{|u|^2}{c^2} |\nabla \times B|
$$

在慢变电磁场中 $u \ll c$，则位移电流项可以忽略，因此得到了：

**前 Maxwell 方程组**：
$$
\begin{aligned}
&\nabla \cdot E = 4\pi \sigma \\
&\nabla \times E = -\frac{1}{c} \partial_t B \\
&\nabla \cdot B = 0 \\
&\nabla \times B = \frac{4\pi}{c} j
\end{aligned}
$$

在这个近似中，电流密度遵循：
$$
\nabla \cdot \boldsymbol{j} = 0
$$
再由电荷平衡方程 $\partial_t \sigma = \nabla \cdot \boldsymbol{j}$ 得到：
$$
\partial_t \sigma \approx 0
$$
从而我们知道电荷密度是一个慢变量。

### 局域准中性条件

等离子体不支持大面积电荷分离，因此在任意空间与任意时刻有：
$$
|n_e - n_i| \ll \frac{1}{2} |n_e + n_i|
$$
在变量替换的公式中有：
$$
\sigma \ll \frac{3}{m_i} \rho = e n_i
$$
$$
\sigma \ll \frac{Ze}{m_i} \rho = e n_e
$$
因此在流体力学方程中，含 $\frac{\sigma}{e}$ 项均可忽略，除了 $\sigma E$ 项。不过由估计：
$$
\frac{\sigma E}{\frac{1}{c} |\boldsymbol{j} \times \boldsymbol{B}|}
\approx \frac{(\nabla \cdot E)E}{|\nabla \times B|B}
\approx \frac{L_H^{-1} E^2}{L_H^{-1} B^2}
\approx \frac{u^2}{c^2} \ll 1
$$
也可以将其忽略。

其次假设：
$$
|\sigma u| \ll j
$$
那么电荷密度在广义 Ohm 定律中也可以忽略，最终只在 Poisson 方程中有效：
$$
\nabla \cdot E = 4\pi \sigma
$$
但是 Poisson 方程只起到一个定义的作用。

这样，在目前我们的讨论范围内去掉了电荷密度这个麻烦的慢变量。我们还差最后的碰撞项 $\mathscr{K}^a$。碰撞的效应是均匀弛豫至热平衡，每次碰撞的弛豫时间 $\tau_a$ 是一个内部分子参量，依赖于等离子体的密度与温度。在本卷中由于只研究慢变电磁场，可以认为弛豫时间 $\tau_a$ 远远小于流体力学时间 $\tau_H^a$。


## 局域等离体平衡

### 局域平衡态

我们把流体力学项和电磁场项都当作慢变函数忽略掉，则只剩下一个碰撞项：
$$
\partial_t f^a \approx \mathscr{K}^a = \mathscr{K}^{aa'} + \mathscr{K}^{a'a}
$$
其定态解：$\mathscr{K}^a = 0$。

这个解是 Maxwell 分布函数：
$$
f^{a eq} = n_a \left( \frac{m_a}{2\pi T} \right)^{3/2} \exp \left( -\frac{m_a |\boldsymbol{v} - \boldsymbol{u}|^2}{2T} \right)
$$
将其代入 Landau 碰撞项的具体表达：
$$
\begin{aligned}
&G_{mn}(g) \left( m_a^{-1} \partial_{1n} - m_\beta^{-1} \partial_{2n} \right) f^{\alpha eq}(v_1) f^{\beta eq}(v_2) \\
&= -\frac{1}{T} G_{mn}(g) (v_{1n} - v_{2n}) f^{\alpha eq}(v_1) f^{\beta eq}(v_2) = 0
\end{aligned}
$$
这里的分布函数是局域分布函数。注意到如果分布函数中的参量 $n_a, u, T$ 都是 $x, t$ 的函数，结论并不改变，这称为动理学中的局域平衡态，与均匀定常的热平衡态并不同。因为在此处虽然有 $\mathscr{K}^a = 0$，但是由于 $\partial_t f^a \approx \mathscr{K}^a$，$\partial_t f^a$ 并不严格为 0。

### 分离快慢过程

与气体动理论不同的是，等离体中存在质量差异悬殊的离子与电子，因此不同种类的碰撞在这里挑战了上述结论。碰撞过程分为快与慢过程，同种离子碰撞很快达到局域平衡，但是异种粒子的碰撞过程时间很长，因此异种粒子的碰撞需要按照类似慢过程的方式处理。

电子之间与离子之间的碰撞满足：
$$
\mathscr{K}^{ee} = 0, \qquad \mathscr{K}^{ii} = 0
$$
局域分布函数是：
$$
f^{a0}(v,x,t) = n_a(x,t) \left( \frac{m_a}{2\pi T_a(x,t)} \right)^{3/2} \exp \left( -\frac{m_a |v - u^a(x,t)|^2}{2T_a(x,t)} \right)
$$
局域电中性的条件：
$$
n_e \approx Z n_i
$$
在此之后的演化由慢过程决定，快过程的作用是保持等离体位于局域平衡态的附近。


## Hermite 矩展开

### 参考态

可以将等离体局域平衡态称为参考态，在其基础上加上偏差值：
$$
f^a(v;x,t) = f^{a0}(v;x,t) (1 + \widehat{\chi}^a(v;x,t))
$$
如果要使得参考态定义中的参考量与每个种类的密度、速度与温度的精确值相一致，那么需要对偏差做约束：
$$
\int d v \, f^{a0} \widehat{\chi}^a = 0
$$
$$
\int d v \, f^{a0} v_r \widehat{\chi}^a = 0
$$
$$
\int d v \, f^{a0} v_r^2 \widehat{\chi}^a = 0
$$

分布函数由无量纲数
$$
c = \left( \frac{m_a}{T_a(x,t)} \right)^{1/2} \left[ v - u^a(x,t) \right]
$$
而依赖于速度 $v$。这样所有的函数都可以由 $c$ 来表达。

等离体局域平衡分布为：
$$
f^{a0}(v;x,t) = n_a(x,t) \left( \frac{m_a}{T(x,t)} \right)^{3/2} \phi^{a0}(c;x,t)
$$
$$
\phi^{a0} = \phi^0(c) = (2\pi)^{-3/2} e^{-c^2}
$$
当参考态用变量 $c$ 表达时，它是均匀各向同性的定常态，但是参考态被认为是 $v$ 的函数时候没有这样的性质；且 $\phi^{a0}$ 不依赖于粒子的种类，归一化为：
$$
\int \phi^0 \, dc = 1
$$

这样可以重写分布函数的表达：
$$
f^a(v;x,t) = n_a(x,t) \left( \frac{m_a}{T_a(x,t)} \right)^{3/2} \phi^0(c) \left[ 1 + \chi^a(c;x,t) \right]
$$

约束条件改写：
$$
\int dc \, \phi^0 \chi^a = 0
$$
$$
\int dc \, \phi^0 c_r \chi^a = 0
$$
$$
\int dc \, \phi^0 c^2 \chi^a = 0
$$

### 确定 $\chi^a$ 的方法

由于 Hermite 多项式相对于 Gauss 权函数是正交的，因此采用张量 Hermite 多项式是合适的。$\chi^a$ 可以写作以下的形式：
$$
\chi^a(c;x,t) = A^a(c;x,t) + c_r B_r^a(c;x,t) + \left( c_r c_s - \frac{1}{3} c^2 \delta_{rs} \right) C_{rs}^a(c;x,t) + \cdots
$$
其中 $A^a$ 是标量函数，$B_r^a$ 是矢量函数，$C_{rs}^a$ 是零迹对称张量函数。所有这些函数除了 $x, t$ 外，仅依赖于 $c$ 的绝对值。

明确表示各向异性的方法是应用不可约张量 Hermite 多项式 $H^{(m)}_{r_1 \cdots r_q}$：
$$
\begin{aligned}
\chi^a(c;x,t) &= \sum_{n=0}^{\infty} h^{a(2n)}(x,t) H^{(2n)}(c) \\
&\quad + \sum_{n=0}^{\infty} h_r^{a(2n+1)}(x,t) H_r^{(2n+1)}(c) \\
&\quad + \sum_{n=1}^{\infty} h_{rs}^{a(2n)}(x,t) H_{rs}^{(2n)}(c) + \cdots
\end{aligned}
$$
其中 $h^{a(m)}$ 是分布函数的不可约 Hermite 矩。

### Hermite 矩

Hermite 矩与原分布函数的联系由方程：
$$
h_{r_1 \cdots r_q}^{a(m)}(x,t) = \int dc \, \phi^0(c) H_{r_1 \cdots r_q}^{(m)}(c) \chi^a(c;x,t)
$$
或是用完全无量纲分布函数计算 Hermite 多项式的平均值：
$$
h_{r_1 \cdots r_q}^{a(m)}(x,t) = \int dc \, \phi^0(c) \left[ 1 + \chi^a(c;x,t) \right] H_{r_1 \cdots r_q}^{(m)}(c)
$$
又由于正交性：
$$
(2\pi)^{-3/2} \int dc \, \exp\left( -\frac{1}{2} c^2 \right) H_{r_1 \cdots r_q}^{(m)}(c) = \delta_{m,0}
$$
知任何非零次 Hermite 多项式的平均值恒为 0。

### Hermite 矩截短

截短级数的表达式遵循以下原则：**只保留矢量与二阶对称张量部分**。
$$
\chi^a(c;x,t) \simeq c_r B_r^a(c;x,t) + \left( c_r c_s - \frac{1}{3} c^2 \delta_{rs} \right) C_{rs}^a(c;x,t)
$$

作者给出了三个近似：

（1）**十三矩近似**：
$$
c_r B_r^a(c;x,t) = h_r^{a(3)}(x,t) H_r^{(3)}(c)
$$
$$
\left( c_r c_s - \frac{1}{3} c^2 \delta_{rs} \right) C_{rs}^a(c;x,t) = h_{rs}^{a(2)}(x,t) H_{rs}^{(2)}(c)
$$

（2）**二十一矩近似**：
$$
c_r B_r^a(c;x,t) = h_r^{a(3)}(x,t) H_r^{(3)}(c) + h_r^{a(5)}(x,t) H_r^{(5)}(c)
$$
$$
\left( c_r c_s - \frac{1}{3} c^2 \delta_{rs} \right) C_{rs}^a(c;x,t) = h_{rs}^{a(2)}(x,t) H_{rs}^{(2)}(c) + h_{rs}^{a(4)}(x,t) H_{rs}^{(4)}(c)
$$

（3）**二十九矩近似**：
$$
c_r B_r^a(c;x,t) = h_r^{a(3)}(x,t) H_r^{(3)}(c) + h_r^{a(5)}(x,t) H_r^{(5)}(c) + h_r^{a(7)}(x,t) H_r^{(7)}(c)
$$
$$
\begin{aligned}
\left( c_r c_s - \frac{1}{3} c^2 \delta_{rs} \right) C_{rs}^a(c;x,t)
&= h_{rs}^{a(2)}(x,t) H_{rs}^{(2)}(c) + h_{rs}^{a(4)}(x,t) H_{rs}^{(4)}(c) \\
&\quad + h_{rs}^{a(6)}(x,t) H_{rs}^{(6)}(c)
\end{aligned}
$$

一般认为十三矩近似并不足够，而二十一矩近似极好，二十九矩近似对输运系数没有贡献。