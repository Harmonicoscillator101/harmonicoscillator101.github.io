---
title: "等离子体输运理论(7)"
date: 2026-08-08
draft: false
math: true
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# 等离体的宏观描述与矩的导出

## 局域分布函数

### 输运理论概念

**空间平移不变性**：
$$
f^a(\boldsymbol{q},\boldsymbol{v};t) = n_a \varphi^a(\boldsymbol{v};t)
$$
$n_a$ 表示离子数密度，$\varphi^a$ 为速度分布，满足归一化条件：
$$
\int \varphi^a(\boldsymbol{v};t) \, d\boldsymbol{v} = 1
$$

**宏观动力学函数**：
$$
B^a(\boldsymbol{x};t) = \int b^a(\boldsymbol{q},\boldsymbol{v};t) f^a(\boldsymbol{q},\boldsymbol{v};t) \, d\boldsymbol{q} \, d\boldsymbol{v}
$$
$b^a(\boldsymbol{q},\boldsymbol{v};t)$ 表示相空间中的任意函数。注意，$\boldsymbol{x}$ 不是相空间坐标而是物理空间坐标。

宏观动力学函数建立起了微观物理与宏观物理之间的关系。

**微观相空间函数的结构**：
$$
b^a(\boldsymbol{q},\boldsymbol{v};t) = \beta^a(\boldsymbol{v}) \delta(\boldsymbol{q} - \boldsymbol{x})
$$
其中 $\delta(\boldsymbol{q} - \boldsymbol{x})$ 是 Dirac delta 函数。

因此宏观动力学函数也可以写为：
$$
B^a(\boldsymbol{x};t) = \int \beta^a(\boldsymbol{v}) f^a(\boldsymbol{v};\boldsymbol{x},t) \, d\boldsymbol{v}
$$
其中分布函数已经由 Dirac 函数改变为局域速度分布函数：
$$
f^a(\boldsymbol{v};\boldsymbol{x},t) = \int \delta(\boldsymbol{q} - \boldsymbol{x}) f^a(\boldsymbol{q},\boldsymbol{v};t) \, d\boldsymbol{q}
$$
称其为函数场。

流体力学与电动力学中的局域密度，可以由宏观动力学函数表达为速度空间中的平均值，利用局域分布函数来计算。

---

## 等离体的宏观量

### 输运理论的矩

注意到动力学函数是三个速度分量的多项式：
$$
\beta^a(\boldsymbol{v}) = \sum_{r_1}^{s_1} \sum_{r_2}^{s_2} \sum_{r_3}^{s_3} a^a_{r_1 r_2 r_3} v_x^a v_y^a v_z^a
$$
且有 $s_1 + s_2 + s_3 = s$，相应的平均值被称为 $f^a(\boldsymbol{v};\boldsymbol{x},t)$ 的 $s$ 阶矩。

**1. 粒子局域数密度 $n_a(\boldsymbol{x},t)$**：
$$
n_a(\boldsymbol{x},t) = \int f^a \, d\boldsymbol{v}
$$
在全电离等离体中，数密度 $n_a$ 是守恒量的密度。

**2. 平均局域速度 $\boldsymbol{u}^a(\boldsymbol{x},t)$**：
$$
\Gamma^a(\boldsymbol{x},t) = n_a(\boldsymbol{x},t) \boldsymbol{u}^a(\boldsymbol{x},t) = \int \boldsymbol{v} f^a \, d\boldsymbol{v}
$$
其中 $\Gamma^a$ 是粒子流。

**3. 总平均动能密度 $n_a \mathscr{E}_a(\boldsymbol{x},t)$**：
$$
n_a \mathscr{E}_a(\boldsymbol{x},t) = \frac{1}{2} m_a \int \boldsymbol{v}^2 f^a \, d\boldsymbol{v}
$$

粒子 $a$ 的流体以平均速度 $\boldsymbol{u}^a$ 运动，具有宏观动能密度 $\frac{1}{2} m_a n_a |\boldsymbol{u}^a|^2$。虽然个体速度对整体速度的平均偏差为零，但是由于平方偏差的平均值不为零，因此存在一个种类 $a$ 的粒子的内能密度作为额外项：
$$
n_a \mathscr{E}_a = \frac{1}{2} m_a n_a |\boldsymbol{u}^a|^2 + n_a \epsilon_a(\boldsymbol{x},t)
$$

**内能密度**：
$$
n_a \epsilon_a = \frac{1}{2} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v}
$$
这个定义基于弱耦合条件满足时成立。

### 热力学相关量

**压强**：热力学平衡时，理想气体压强满足：
$$
P_a(\boldsymbol{x},t) = \frac{2}{3} n_a \epsilon_a = \frac{1}{3} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v}
$$

**温度**：热力学平衡时，理想气体满足：
$$
\epsilon_a = \frac{3}{2} k_B \overline{T}_a
$$
对其记号与单位进行修正，记为：
$$
T_a = k_B \overline{T}_a
$$

对其进行外推后得到种类 $a$ 的粒子温度 $T_a$：
$$
n_a T_a = \frac{1}{3} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v} = P_a
$$

至此，$n_a$、$\boldsymbol{u}^a$、$T_a$ 被称为**等离体的动力学变量**，构成等离体的二流体变量。我们最关注那些与流体力学与电动力学相关的量。

**质量密度 $\rho(\boldsymbol{x},t)$**：
$$
\rho(\boldsymbol{x},t) = \sum_a m_a n_a
$$

**质心速度 $\boldsymbol{u}(\boldsymbol{x},t)$**：
$$
\rho \boldsymbol{u} = \sum_a m_a n_a \boldsymbol{u}^a
$$
这具有等离体总动量密度的意义。

**电荷密度 $\sigma(\boldsymbol{x},t)$**：
$$
\sigma(\boldsymbol{x},t) = \sum_a e_a n_a
$$

**电流密度 $\boldsymbol{j}(\boldsymbol{x},t)$**：
$$
\boldsymbol{j}(\boldsymbol{x},t) = \sum_a e_a n_a \boldsymbol{u}^a
$$

**总能量密度 $\rho(\boldsymbol{x},t) \mathscr{E}(\boldsymbol{x},t)$**：
$$
\rho(\boldsymbol{x},t) \mathscr{E}(\boldsymbol{x},t) = \frac{1}{2} \rho u^2 + \rho \epsilon
$$

这个定义是非线性的，整体内能 $\epsilon$ 与各组分的内能 $\epsilon_a$ 的关系难以确定，关键在于其定义中的质心速度 $\boldsymbol{u}$ 与粒子的平均速度 $\boldsymbol{u}^a$ 的差异。

在这其中，总能量密度 $\rho \mathscr{E}$ 是唯一重要的流体力学量，因为它是守恒量。但是对于局部内能 $\epsilon_a$ 则不一样，因为在碰撞中会发生不同种类粒子之间能量的传递，只不过这个能量的传递极慢，在大部分情况下可以将其视为准守恒量。因此对于电子和离子，有两种不同的准守恒量 $\epsilon_e$ 与 $\epsilon_i$，对应不同的温度 $T_e$ 与 $T_i$。

**其他非流体力学量**：

种类 $a$ 的热流：
$$
\boldsymbol{q}^a(\boldsymbol{x},t) = \sqrt{\frac{5}{2}} m_a n_a \left( \frac{T_a}{m_a} \right)^{\frac{3}{2}} h^{a\{3\}}(\boldsymbol{x},t) = \frac{1}{2} m_a \int (\boldsymbol{v} - \boldsymbol{u}^a) |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v}
$$

耗散压强张量：
$$
\begin{aligned}
\pi_{rj}^a(\boldsymbol{x},t) &= \sqrt{2} n_a T_a h_{rj}^{a\{2\}} \\
&= m_a \int \left[ (v_r - u_r^a)(v_j - u_j^a) - \frac{1}{3} |\boldsymbol{v} - \boldsymbol{u}^a|^2 \delta_{rj} \right] f^a \, d\boldsymbol{v}
\end{aligned}
$$

作者附上了各个相关量的表格，在此不再列出。

---

## 回到动理方程

### 分解动理方程

$$
\partial_t f^a = \Phi^a + \mathscr{F}^a + \mathscr{K}^a
$$

其中自由流动项为：
$$
\Phi^a = -\boldsymbol{v} \cdot \nabla f^a
$$

电磁场项为：
$$
\mathscr{F}^a = -\frac{e_a}{m_a} \left( E_r(\boldsymbol{x},t) + \epsilon_{rmn} v_m B_n(\boldsymbol{x},t) \frac{\partial}{\partial v_r} f^a \right)
$$
其中 $E$ 与 $B$ 由 Maxwell 方程确定。如果忽略碰撞项，以上的这一部分已经完全定义了 Vlasov 方程。

所考虑的重点，也是最复杂的一项就是碰撞项 $\mathscr{K}^a$，它是系统演化的主要驱动。与一般的流体碰撞不同，等离体的碰撞除了外场之外还涉及自身所产生的平均电磁场作用，在弱耦合情况下它归结为 Landau 碰撞算符。

---

## 宏观量的演化方程

### 二流体的演化方程

首先处理数密度的演化方程。分布函数直接对速度积分得到：
$$
\partial_t \int f^a \, d\boldsymbol{v} = \partial_t n_a = \int (\Phi^a + \mathscr{F}^a + \mathscr{K}^a) \, d\boldsymbol{v}
$$

分别代入流动项与电磁场项：
$$
\int \Phi^a \, d\boldsymbol{v} = -\nabla_m \int v_m f^a \, d\boldsymbol{v} = -\nabla_m (n_a u_m^a)
$$
$$
\int \mathscr{F}^a \, d\boldsymbol{v} = -\frac{e_a}{m_a} \int \left( E_r(\boldsymbol{x},t) + \epsilon_{rmn} v_m B_n(\boldsymbol{x},t) \frac{\partial}{\partial v_r} f^a \right) d\boldsymbol{v} = 0
$$
同时由守恒律得到：
$$
\int \mathscr{K}^a \, d\boldsymbol{v} = 0
$$

因此得到**连续性方程**：
$$
\partial_t n_a = -\nabla_m (n_a \boldsymbol{u}^a)
$$

然后处理平均速度的演化方程。分布函数乘以 $m_a v_r$ 后对速度积分得到：
$$
m_a \partial_t (n_a u_r^a) = m_a \int v_r (\Phi^a + \mathscr{F}^a + \mathscr{K}^a) \, d\boldsymbol{v}
$$

类似地，代入之前定义过的热力学相关量可以得到：
$$
m_a \int v_r \Phi^a \, d\boldsymbol{v} = -\nabla_m \left[ m_a n_a u_r^a u_m^a + n_a T_a \delta_{rm} + \pi_{rm}^a \right]
$$
$$
m_a \int v_r \mathscr{F}^a \, d\boldsymbol{v} = e_a n_a (E_r + \epsilon_{rmn} u_m^a B_n)
$$

引入被称作摩擦力密度的矢量 $\boldsymbol{R}$ 来解决碰撞项的积分：
$$
R_r^a(\boldsymbol{x},t) = m_a \int v_r \mathscr{K}^a \, d\boldsymbol{v}
$$

最后可以得到**动量平衡方程**：
$$
\partial_t (m_a n_a u_r^a) = -\nabla_m (m_a n_a u_r^a u_m^a + \delta_{rm} n_a T_a + \pi_{rm}^a) + e_a n_a (E_r + \epsilon_{rmn} u_m^a B_n) + R_r^a
$$

这里面的 $E$ 和 $B$ 通过 Maxwell 方程组闭合。

最后是关于温度的能量平衡方程：
$$
\begin{aligned}
n_a \partial_t T_a &= -n_a \boldsymbol{u}^a \cdot \nabla T_a - \frac{2}{3} n_a T_a \nabla \cdot \boldsymbol{u}^a \\
&\quad - \frac{2}{3} \pi^a_{mn} \nabla_m u_n^a - \frac{2}{3} \nabla_m q^a_m + \frac{2}{3} Q^a
\end{aligned}
$$

其中碰撞热交换率：
$$
Q^a = \frac{1}{2} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 \mathscr{K}^a \, d\boldsymbol{v}
$$

摩擦力密度与碰撞热交换率可以由之前的异种粒子碰撞来确定：
$$
R^e = R^{ei}, \qquad R^i = R^{ie}
$$
$$
Q^e = Q^{ei}, \qquad Q^i = Q^{ie}
$$
$$
R^{ei} = -R^{ie}
$$
$$
Q^{ei} = -Q^{ie} - (\boldsymbol{u}^e - \boldsymbol{u}^i) R^{ei}
$$

最终，关于 $n_a$、$u_r^a$、$T_a$ 的二流体平衡方程确立了。$Q$ 与 $R$ 确定了电子与离子的非独立性。

### 流体力学平衡方程

上面推出的二流体方程是为了推出单流体平衡方程做准备的。在采用质量比极小的量级近似后得到以下方程。

由连续性方程：
$$
\partial_t \rho = -\nabla \cdot (\rho \boldsymbol{u})
$$

将单流体与二流体变量的转换公式代入得到动量平衡方程（书中列表）：
$$
\begin{aligned}
\partial_t \rho u_r &= -\nabla \cdot \left\{ \rho u_r u_i + \delta_{ri} \left[ \left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) T_e + \frac{\rho}{m_i} T_i \right] + \pi_{ri}^e + \pi_{ri}^i \right\} \\
&\quad + \sigma E_r + \epsilon_{rim} j_i B_m
\end{aligned}
$$

方程右端散度包含的三项分别为动量流、标量压强、耗散压强。其中得到总标量压强的方程为：
$$
P = \left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) T_e + \frac{\rho}{m_i} T_i
$$

此外注意到这里面碰撞项 $\mathscr{K}^a$ 没有贡献，这是由于总动量的局域守恒的结果。

Maxwell 方程与 Lorentz 密度相互耦合后得到：
$$
\begin{aligned}
&\nabla \cdot \boldsymbol{E} = 4\pi \sigma \\
&\nabla \times \boldsymbol{E} = -\partial_t \boldsymbol{B} \\
&\nabla \cdot \boldsymbol{B} = 0 \\
&\nabla \times \boldsymbol{B} = \partial_t \boldsymbol{E} + 4\pi \boldsymbol{j}
\end{aligned}
$$

然后是温度项，分为 $T_i$ 与 $T_e$：
$$
\begin{aligned}
&\left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) \partial_t T_e = - \left( \frac{Z \rho}{m_i} u_r - \frac{1}{e} j_r \right) \nabla_r T_e \\
&\quad - \frac{2}{3} \left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) T_e \nabla_r \left( \frac{Z e \rho u_r - m_i j_r}{Z e \rho - m_i \sigma} \right) \\
&\quad - \frac{2}{3} \pi_{ri}^e \nabla_r \left( \frac{Z e \rho u_r - m_i j_r}{Z e \rho - m_i \sigma} \right) - \frac{2}{3} \nabla_r q_r^e + \frac{2}{3} Q^e
\end{aligned}
$$

对于离子温度：
$$
\begin{aligned}
\frac{\rho}{m_i} \partial_t T_i &= -\frac{\rho}{m_i} u_r \nabla_r T_i - \frac{2}{3} \frac{\rho}{m_i} T_i \nabla_r u_r \\
&\quad - \frac{2}{3} \pi_{rs}^i \nabla_r u_s - \frac{2}{3} \nabla_r q_r^i + \frac{2}{3} Q^i
\end{aligned}
$$

然后是对电动力学项的方程。首先是电荷守恒方程：
$$
\partial_t \sigma = -\nabla_r j_r
$$

对于电流的偏微分方程要复杂得多：
$$
\begin{aligned}
\partial_t j_r &= \nabla_i \left( \frac{Z e \rho \sigma u_r u_s - Z e \rho (j_r u_s + j_s u_r) + m_i j_r j_s}{Z e \rho - m_i \sigma} \right) \\
&\quad + \frac{1}{m_e m_i} \nabla_r [(Z e \rho - m_i \sigma) T_e] + \frac{e}{m_e} \nabla_i (\pi_{ri}^e - Z \mu \pi_{ri}^i) \\
&\quad + \frac{e}{m_e m_i} (Z e \rho - m_i \sigma) E_r + \frac{e}{m_e m_i} \epsilon_{rim} (Z e \rho u_i - m_i j_i) B_m \\
&\quad - \frac{e}{m_e} R_r^e
\end{aligned}
$$

这个方程称为**广义 Ohm 定律**，它由一般 Ohm 定律 $\boldsymbol{j} = \sigma \boldsymbol{E}$ 推广而来。

### 平衡方程

这样，流体力学平衡方程、广义 Ohm 定律与 Maxwell 方程共同构成了宏观等离体物理基本方程。但是它们不是闭合的，其中的耗散压强、热流、摩擦力密度与热交换率仍然没有约束关系。重新将转换公式代入一开始得到的二流体方程，从而得到单流体的粒子流 $\Gamma^a$、热流 $\boldsymbol{q}^a$、压强张量 $P^a$、四次矩压强张量 $S^a$。具体表达限于篇幅没有展示。

**挑战与目标**：主要需要强调的是，由于流体力学方程具有级列结构，对于一次矩的方程涉及二次矩、二次矩又涉及三次矩，以至于推至无限，这是由于碰撞项的复杂性所决定的，所以目的不在于把全部项罗列出来，而是在于寻找精确解。这个过程涉及电动力学、流体力学、热力学、统计物理等多个物理领域的交叉。