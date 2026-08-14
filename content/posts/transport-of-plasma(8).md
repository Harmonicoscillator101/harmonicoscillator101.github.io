---
title: "等离子体输运理论(8)"
date: 2026-08-14
draft: false
math: true
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# 等离体宏观量的级列结构

## 不同阶矩

### 零阶矩

**粒子数密度，双流体变量**：
$$
n_a(\boldsymbol{x},t) = \int f^a(\boldsymbol{v};\boldsymbol{x},t) \, d\boldsymbol{v}
$$

**密度，单流体变量**：
$$
\rho(\boldsymbol{x},t) = \sum_a m_a \int f^a \, d\boldsymbol{v}
$$

**电荷密度，电动力学量**：
$$
\sigma(\boldsymbol{x},t) = \sum_a e_a \int f^a \, d\boldsymbol{v}
$$

在这里面，分布函数应当理解为：
$$
f^a(\boldsymbol{v};\boldsymbol{x},t) = \int \delta(\boldsymbol{q} - \boldsymbol{x}) f^a(\boldsymbol{q},\boldsymbol{v};t) \, d\boldsymbol{q}
$$

### 一阶矩

**平均速度，双流体变量**：
$$
n_a u_r^a(\boldsymbol{x},t) = \int v_r f^a \, d\boldsymbol{v}
$$

**质心速度，单流体量**：
$$
\rho u_r(\boldsymbol{x},t) = \sum_a m_a \int v_r f^a \, d\boldsymbol{v}
$$

**电动力学量**：

电流密度：
$$
j_r(\boldsymbol{x},t) = \sum_a e_a \int v_r f^a \, d\boldsymbol{v}
$$

粒子流：
$$
\Gamma_r^a(\boldsymbol{x},t) = \int v_r f^a \, d\boldsymbol{v}
$$

### 二阶矩

**温度**（既是双流体变量也是单流体变量）：
$$
n_a T_a(\boldsymbol{x},t) = \frac{1}{3} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v}
$$

**压强张量**：

耗散压强张量：
$$
\pi_{rs}^a = m_a \int \left[ (v_r - u_r^a)(v_s - u_s^a) - \frac{1}{3}|\boldsymbol{v} - \boldsymbol{u}^a|^2 \delta_{rs} \right] f^a \, d\boldsymbol{v}
$$

总压强张量：
$$
P_{rs}^a = m_a \int (v_r - u_r^a)(v_s - u_s^a) f^a \, d\boldsymbol{v}
$$

### 三阶及以上矩

**热流**：
$$
q_r^a(\boldsymbol{x},t) = \frac{1}{2} m_a \int (v_r - u_r^a)|\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v}
$$

更高阶矩没有直接的物理含义，但是仍然为我们感兴趣：

1. 三阶张量三次矩：$ q_{rsp}^a = \frac{1}{2} \int (v_r - u_r^a)(v_s - u_s^a)(v_p - u_p^a) f^a \, d\boldsymbol{v} $

2. 二阶张量四次矩：$ S_{rs}^a = \frac{1}{2} m_a \int (v_r - u_r^a)(v_s - u_s^a) |\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v} $

3. 四阶张量四次矩：$ S_{rspq}^a = \frac{1}{2} m_a \int (v_r - u_r^a)(v_s - u_s^a)(v_p - u_p^a)(v_q - u_q^a) f^a \, d\boldsymbol{v} $

4. 三阶张量五次矩：$ T_{rsp}^a = \frac{1}{2} m_a \int (v_r - u_r^a)(v_s - u_s^a)(v_p - u_p^a)|\boldsymbol{v} - \boldsymbol{u}^a|^2 f^a \, d\boldsymbol{v} $


## 回到动理方程，推导演化方程

### 回顾动理方程

**动理方程**：
$$
\partial_t f^a = \Phi^a + \mathscr{F}^a + \mathscr{K}^a
$$

自由流动项：
$$
\Phi^a = -\boldsymbol{v} \cdot \nabla f^a
$$

电磁场项：
$$
\mathscr{F}^a = -\frac{e_a}{m_a} \left( E_r(\boldsymbol{x},t) + \epsilon_{rmn} v_m B_n(\boldsymbol{x},t) \frac{\partial}{\partial v_r} f^a \right)
$$

若忽略碰撞项，$E$ 与 $B$ 由 Maxwell 方程组闭合，这就是 Vlasov 方程。

最复杂的一项就是碰撞项 $\mathscr{K}^a$，它是系统演化的主要驱动。在弱耦合情况下它归结为 Landau 碰撞算符。注意式子中的速度项，这是产生级列结构的根源。

### 不同宏观量的演化方程

**粒子数密度（连续性方程）**：
$$
\partial_t n_a = -\nabla \cdot (n_a \boldsymbol{u}^a)
$$
可见，零阶矩变量的方程需要一阶矩的方程以闭合。

**平均速度（动量定理）**：
$$
\begin{aligned}
\partial_t (m_a n_a u_r^a) &= -\nabla_m (m_a n_a u_r^a u_m^a + \delta_{rm} n_a T_a + \pi_{rm}^a) \\
&\quad + e_a n_a (E_r + \epsilon_{rmn} u_m^a B_n) + R_r^a
\end{aligned}
$$
其中 $R_r^a(\boldsymbol{x},t) = m_a \int v_r \mathscr{K}^a \, d\boldsymbol{v}$ 是摩擦力密度。可见，一阶矩的方程需要二阶矩变量（式子中的温度 $T_a$、耗散压强张量 $\pi_{rm}^a$）的方程以闭合。

**温度（能量方程）**：
$$
\begin{aligned}
n_a \partial_t T_a &= -n_a \boldsymbol{u}^a \cdot \nabla T_a - \frac{2}{3} n_a T_a \nabla \cdot \boldsymbol{u}^a \\
&\quad - \frac{2}{3} \pi_{mn}^a \nabla_m u_n^a - \frac{2}{3} \nabla_m q_m^a + \frac{2}{3} Q^a
\end{aligned}
$$
其中碰撞热交换率：
$$
Q^a = \frac{1}{2} m_a \int |\boldsymbol{v} - \boldsymbol{u}^a|^2 \mathscr{K}^a \, d\boldsymbol{v}
$$
可见，二阶矩方程需要三阶矩变量（式子中的热流 $q_m^a$）的方程以闭合。

转换至单流体平衡方程，仍然存在相同的级列结构：

1. 连续性方程：
$$
\partial_t \rho = -\nabla \cdot (\rho \boldsymbol{u})
$$

2. 动量方程：
$$
\begin{aligned}
\partial_t \rho u_r &= -\nabla \cdot \left\{ \rho u_r u_i + \delta_{ri} \left[ \left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) T_e + \frac{\rho}{m_i} T_i \right] + \pi_{ri}^e + \pi_{ri}^i \right\} \\
&\quad + \sigma E_r + \epsilon_{rim} j_i B_m
\end{aligned}
$$

3. 温度方程（电子）：
$$
\begin{aligned}
\left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) \partial_t T_e
&= - \left( \frac{Z \rho}{m_i} u_r - \frac{1}{e} j_r \right) \nabla_r T_e \\
&\quad - \frac{2}{3} \left( \frac{Z \rho}{m_i} - \frac{\sigma}{e} \right) T_e \nabla_r \left( \frac{Z e \rho u_r - m_i j_r}{Z e \rho - m_i \sigma} \right) \\
&\quad - \frac{2}{3} \pi_{ri}^e \nabla_r \left( \frac{Z e \rho u_r - m_i j_r}{Z e \rho - m_i \sigma} \right) - \frac{2}{3} \nabla_r q_r^e + \frac{2}{3} Q^e
\end{aligned}
$$

温度方程（离子）：
$$
\begin{aligned}
\frac{\rho}{m_i} \partial_t T_i
&= -\frac{\rho}{m_i} u_r \nabla_r T_i - \frac{2}{3} \frac{\rho}{m_i} T_i \nabla_r u_r \\
&\quad - \frac{2}{3} \pi_{rs}^i \nabla_r u_s - \frac{2}{3} \nabla_r q_r^i + \frac{2}{3} Q^i
\end{aligned}
$$

电动力学方程：

1. 电荷守恒方程：
$$
\partial_t \sigma = -\nabla_r j_r
$$

2. 广义 Ohm 定律：
$$
\begin{aligned}
\partial_t j_r &= \nabla_i \left( \frac{Z e \rho \sigma u_r u_s - Z e \rho (j_r u_s + j_s u_r) + m_i j_r j_s}{Z e \rho - m_i \sigma} \right) \\
&\quad + \frac{1}{m_e m_i} \nabla_r [(Z e \rho - m_i \sigma) T_e] + \frac{e}{m_e} \nabla_i (\pi_{ri}^e - Z \mu \pi_{ri}^i) \\
&\quad + \frac{e}{m_e m_i} (Z e \rho - m_i \sigma) E_r + \frac{e}{m_e m_i} \epsilon_{rim} (Z e \rho u_i - m_i j_i) B_m \\
&\quad - \frac{e}{m_e} R_r^e
\end{aligned}
$$

显然，以上的方程组都具有级列结构，低阶矩依赖于高阶矩，一直到无限级，其中还涉及耗散压强张量、热流、摩擦力密度与热交换率等未知量。

### 其他平衡方程

1. 粒子流：
$$
\begin{aligned}
\partial_t \Gamma_r^a &= -\nabla_n \left( m_a^{-1} P_{rn}^a + u_n^a \Gamma_r^a \right) + \frac{e_a}{m_a} n_a E_r \\
&\quad + \frac{e_a B}{m_a} \epsilon_{rmn} \Gamma_m^a b_n + \frac{1}{m_a} R_r^a
\end{aligned}
$$

2. 热流：
$$
\begin{aligned}
\partial_t q_r^e &= -\nabla_n (S_{rn}^a + u_n^a q_r^a) - (2 q_{rmn}^a + q_m^a \delta_{rn}) \nabla_m u_n^a \\
&\quad + \left( P_{rn}^a + \frac{3}{2} P_a \delta_{rn} \right) \frac{1}{m_a n_a} \nabla_m P_{mn}^a \\
&\quad + \frac{e_a B}{m_a} \varepsilon_{rmn} q_m^a b_n + R_r^{a(3)} - \frac{1}{m_a n_a} \left( P_{rn}^a + \frac{3}{2} P_a \delta_{rn} \right) R_n^a
\end{aligned}
$$

3. 压强张量：
$$
\begin{aligned}
\partial_t P_{rs}^a &= -\nabla_n (2 q_{rsn}^a + u_n^a P_{rs}^a) - (P_{rm}^a \delta_{sn} + P_{nm}^e \delta_{rn}) \nabla_m u_n^a \\
&\quad + \frac{e_a B}{m_a} (\epsilon_{rpq} P_{sp}^a + \epsilon_{spq} P_{rp}^a) b_q + R_{rs}^{a(2)}
\end{aligned}
$$

4. 四次矩压强张量：
$$
\begin{aligned}
\partial_t S_{rs}^a &= -\nabla_n (T_{rsn}^a + u_n^a S_{rs}^a) - (2 S_{rsmn}^u + S_{rm}^a \delta_{rm} + S_{nm}^a \delta_{rn}) \nabla_m u_n^a \\
&\quad + (2 q_{rsn}^a + q_r^a \delta_{sn} + q_s^a \delta_{rn}) \frac{1}{m_a n_a} \nabla_m P_{mn}^a + \frac{e_a B}{m_a} (\epsilon_{rpq} S_{sp}^a + \epsilon_{spq} S_{rp}^a) b_q \\
&\quad + R_{rs}^{(4)} - \frac{1}{m_a n_a} (2 q_{rsn}^a + q_r^a \delta_{sn} + q_s^a \delta_{rn}) R_m^a
\end{aligned}
$$

每个矩方程包括含有高次矩的散度的一项，以及该矩本身乘以 $\boldsymbol{u}^a$ 的一项。所有方程包含涉及磁场的一项，以广义 Lorentz 力的形式表现。所有方程包含碰撞项的一份贡献，以广义摩擦力 $R^{a(n)}$ 的形式表现。

### 一个猜测

通过观察这些矩以及相关演化方程的形式，可以做出 $n$ 阶矩的演化方程的一个猜测：

**$n$ 阶矩的表达式**：
$$
M^{(n)}_{i_1 i_2 \cdots i_n}(\boldsymbol{x},t) = \int (v_{i_1} - u_{i_1}^a)(v_{i_2} - u_{i_2}^a) \cdots (v_{i_n} - u_{i_n}^a) f^a \, d\boldsymbol{v}
$$

**$n$ 阶矩演化方程的表达式**：
$$
\begin{aligned}
\partial_t M^{(n)}_{i_1 \cdots i_n} &+ \nabla_j \left( u_j^a M^{(n)}_{i_1 \cdots i_n} + M^{(n+1)}_{j i_1 \cdots i_n} \right) \\
&= -\sum_{k=1}^{n} M^{(n)}_{i_1 \cdots j \cdots i_n} \, \partial_j u_{i_k}^a + \frac{e_a}{m_a} \sum_{k=1}^{n} \epsilon_{i_k j l} B \, M^{(n)}_{i_1 \cdots j \cdots i_n} \\
&\quad + \bigl( \text{低阶矩与一些梯度} \bigr) + R^{a(n)}
\end{aligned}
$$