---
title: "等离子体输运理论(6)"
date: 2026-08-08
draft: false
math: true
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# 等离体动理方程

## Landau 方程

### 传播函数

**目标：从单粒子方程中消去关联函数 $g^{\alpha\beta}$**

从弱耦合形式的关联方程出发，这是一个关于 $g^{\alpha\beta}$ 的线性非齐次方程。

传播函数方程：定义传播函数 $U_{12}^{\alpha\beta}(t)$，满足：
$$
\partial_t U_{12}^{\alpha\beta}(t) - (L_1^\alpha + L_2^\beta)U_{12}^{\alpha\beta}(t) = 0, \quad U_{12}^{\alpha\beta}(0) = I
$$

关联函数的形式解：通过传播函数，运用常数变易法，线性非齐次的 Landau 方程的初值问题解为：
$$
g^{\alpha\beta}(1,2;t) = \int_0^t d\tau\, U_{12}^{\alpha\beta}(\tau) L_{12}^{\alpha\beta} f^\alpha(1;t-\tau)f^\beta(2;t-\tau) + U_{12}^{\alpha\beta}(t) g^{\alpha\beta}(1,2;0)
$$
其中 $g^{\alpha\beta}(1,2;0)$ 是给定的初始关联。

### 主方程

将形式解代入单粒子方程的碰撞项，得到闭合方程：

碰撞项表达式：
$$
\begin{aligned}
\mathcal{K}^\alpha &= \sum_\beta \int d2 \int_0^t d\tau\,
L_{12}^{\alpha\beta} U_{12}^{\alpha\beta}(\tau) L_{12}^{\alpha\beta} f^\alpha(1;t-\tau)f^\beta(2;t-\tau) \\
&\quad + \sum_\beta \int d2\, L_{12}^{\alpha\beta} U_{12}^{\alpha\beta}(t) g^{\alpha\beta}(1,2;0)
\end{aligned}
$$

**方程性质**：
- 该方程称为**主方程**。
- 它是非 Markov 的：$t$ 时刻的变化率 $\partial_t f^\alpha(1;t)$ 依赖于整个过去历史 $f^\alpha(1;t-\tau)$（$\tau$ 从 0 到 $t$ 积分）。
- 这种非 Markov 结构难以导出通常的宏观流体力学或电动力学方程。
- $f_1^a(1;t)$ 在时间 $t$ 时刻的变化率依赖于系统的初始配置。

### 传播函数与单粒子方程的联系

两体传播函数描述两个独立粒子在无相互作用下的联合演化，可以分解为单粒子传播函数的乘积：

因子分解：
$$
U_{12}^{\alpha\beta}(t) = U_1^{\alpha}(t) \, U_2^{\beta}(t)
$$

单粒子传播函数方程：单粒子传播函数满足：
$$
\partial_t U_1^{\alpha}(t) = L_1^{\alpha} U_1^{\alpha}(t)
$$
其中 $L_1^{\alpha}$ 是单粒子 Liouville 算符。

**物理意义**：因子分解表明，在无相互作用时，两个粒子的演化是相互独立的，联合演化算符等于各自演化算符的乘积。

### 传播函数与单粒子运动方程的联系

**传播函数与运动方程等价**：确定传播函数等价于求解单粒子运动方程。根据 Liouville 定理：

传播函数的作用：
$$
U_1^{\alpha}(t) f^{\alpha}(q_1,v_1;0) = f^{\alpha}(q_1,v_1;t) = f^{\alpha}(q_1(-t), v_1(-t); 0)
$$

**反向运动方程**：
- 位置 $q(-t)$ 满足：$\dot{q}(-t) = [H, q(-t)]$
- 初始条件：$q(0) = q$
- 速度 $v(-t)$ 有类似方程

**面临的困难**：当存在非均匀外磁场时，即使单粒子运动方程也难以解析求解。

**出路**：等离子体中存在多个特征时间和长度尺度，在某些情况下可以利用尺度分离来简化，从而推导出清晰的动理方程。

### 特征时间与长度

Debye 长度与等离子体频率：
$$
r_{c\alpha} = \lambda_{D\alpha} = \left( \frac{4\pi e_\alpha^2 n_\alpha}{T_\alpha} \right)^{-1/2}
$$
对应的特征时间（等离子体频率倒数）：
$$
\tau_{c\alpha} = \omega_{p\alpha}^{-1} = \left( \frac{4\pi e_\alpha^2 n_\alpha}{m_\alpha} \right)^{-1/2}
$$

弛豫时间与平均自由程：弛豫时间 $\tau_\alpha$ 是碰撞使分布函数显著变化的时间尺度。平均自由程：
$$
\lambda_{\text{mfp}\alpha} = V_{T\alpha} \tau_\alpha, \qquad V_{T\alpha} = \left( \frac{2T_\alpha}{m_\alpha} \right)^{1/2}
$$

梯度长度尺度（流体力学长度）：宏观量（密度、温度、电磁场、分布函数）空间变化的特征长度：
$$
L_H = \left( \frac{1}{A} \left| \frac{\partial A}{\partial q} \right| \right)^{-1}
$$
其中 $A$ 代表任一宏观量。这个在第一章讨论过。

流体力学时间：
$$
\tau_{H\alpha} = L_H / V_{T\alpha}
$$

Larmor 频率与 Larmor 半径：
$$
\tau_{B\alpha} = |\Omega_\alpha|^{-1} = \frac{m_\alpha c}{|e_\alpha| B}, \qquad \rho_{L\alpha} = V_{T\alpha} \tau_{B\alpha}
$$

在弱耦合等离体中，它们的关系可以如下表示：

**第一种情况**：
$$
r_{c\alpha} \ll \lambda_{\text{mfp}\alpha} < L_H, \qquad \tau_{c\alpha} \ll \tau_\alpha < \tau_{H\alpha}
$$

**第二种情况**：
$$
r_{c\alpha} \ll L_H < \lambda_{\text{mfp}\alpha}, \qquad \tau_{c\alpha} \ll \tau_{H\alpha} < \tau_\alpha
$$

考虑磁场效应时，假设磁场足够弱，满足：
$$
|\Omega_\alpha| \tau_{c\alpha} < 1, \qquad \frac{\tau_{c\alpha}}{\rho_{L\alpha}} < 1
$$
即使对于强磁场，通常也有：
$$
\frac{L_H}{\rho_{L\alpha}} \gg 1, \qquad \frac{\lambda_{\text{mfp}\alpha}}{\rho_{L\alpha}} \gg 1
$$

### Landau 碰撞

我们主要对趋向平衡的现象感兴趣，这在弛豫时间 $\tau_\alpha$ 的时间长度上发生，而这远比碰撞时间 $\tau_{c\alpha}$ 长得多，因此可以将碰撞时间上发生的变化抹平，从而寻找长时间内的宏观状态。

在先前，碰撞项可以粗略表示为：
$$
\mathcal{K}^\alpha = \frac{f^a - f^a_{eq}}{\tau_{\alpha}}
$$

作者给出推导后的表达式，具体推导过程很长，作者放在附录中。

**Landau 碰撞项**：
$$
\mathcal{K}^\alpha = \sum_\beta 2\pi e_\alpha^2 e_\beta^2 \ln\Lambda \int d\mathbf{v}_2\,
m_\alpha^{-1} \frac{\partial}{\partial v_{1,r}} G_{rs}(\mathbf{g}) 
\left( m_\alpha^{-1}\frac{\partial}{\partial v_{1,s}} - m_\beta^{-1}\frac{\partial}{\partial v_{2,s}} \right) f^\alpha f^\beta
$$

- $\mathbf{g} = \mathbf{v}_1 - \mathbf{v}_2$ 为相对速度
- $G_{rs}(\mathbf{a}) = \dfrac{a^2\delta_{rs} - a_r a_s}{a^3}$ 为 Landau 张量
- $\ln\Lambda = \ln\left[ \dfrac{3}{2}(T_e+T_i)\lambda_D / (Ze^2) \right]$ 为 Coulomb 对数

---

## 碰撞项的性质

### 两条重要引理

**引理 A**：若 $A(v)$ 是速度的任意函数，且在无穷远处的增长不超过多项式，则：
$$
\int dv\, \frac{\partial}{\partial v_r} \big[ A(v) f^\alpha(q,v;t) \big] = 0
$$

**引理 B**：若 $A'(v)$ 与 $A(v)$ 具有相同的性质（增长不超过多项式），则有分部积分公式：
$$
\int dv\, A'(v) \frac{\partial}{\partial v_r} \big[ A(v) f^\alpha(q,v;t) \big] = - \int dv\, f^\alpha(q,v;t) A(v) \frac{\partial}{\partial v_r} A'(v)
$$

### 守恒律

碰撞项为分布函数的二次非线性算符，可分解为双体碰撞贡献之和：
$$
\mathcal{K}^\alpha = \sum_{\beta = e,i} \mathcal{K}^{\alpha\beta}
$$
其中 $\mathcal{K}^{\alpha\beta}$ 是 $f^\alpha f^\beta$ 的泛函。

碰撞过程中必须满足的局域守恒律：

1. 粒子数守恒：
$$
\int dv\, \mathcal{K}^\alpha = 0, \quad \alpha = e, i
$$

2. 动量守恒：
$$
\sum_{\alpha} m_\alpha \int dv\, v_r \mathcal{K}^\alpha = 0, \quad r = 1,2,3
$$

3. 能量守恒：
$$
\sum_{\alpha} \frac{1}{2} m_\alpha \int dv\, v^2\, \mathcal{K}^\alpha = 0
$$

同类碰撞（$\alpha$-$\alpha$）的独立守恒律：
$$
\int d\mathbf{v}_1\, \mathcal{K}^{\alpha\alpha} = 0
$$
$$
m_\alpha \int d\mathbf{v}_1\, v_1\, \mathcal{K}^{\alpha\alpha} = 0
$$
$$
\frac{1}{2}m_\alpha \int d\mathbf{v}_1\, v_1^2\, \mathcal{K}^{\alpha\alpha} = 0
$$

异类碰撞（$\alpha$-$\beta$）的守恒性质：
$$
\int d\mathbf{v}_1\, \mathcal{K}^{\alpha\beta} = \int d\mathbf{v}_1\, \mathcal{K}^{\beta\alpha} = 0
$$
$$
m_\alpha \int d\mathbf{v}_1\, v_{1r}\, \mathcal{K}^{\alpha\beta} = -m_\beta \int d\mathbf{v}_1\, v_{1r}\, \mathcal{K}^{\beta\alpha}
$$
$$
\frac{1}{2}m_\alpha \int d\mathbf{v}_1\, v_1^2\, \mathcal{K}^{\alpha\beta} = -\frac{1}{2}m_\beta \int d\mathbf{v}_1\, v_1^2\, \mathcal{K}^{\beta\alpha}
$$

---

## Lorentz 过程

### Lorentz 模型

Landau 碰撞项具有惊人的对称性：
$$
\mathcal{K}^{\alpha\beta} = A_{\alpha\beta} \int d\boldsymbol{v}_2 \, (m_\alpha^{-1}\partial_{1r} - m_\beta^{-1}\partial_{2r}) G_{rs}(\boldsymbol{g}) \times (m_\alpha^{-1}\partial_{1s} - m_\beta^{-1}\partial_{2s}) f^\alpha(1) f^\beta(2)
$$

但是实际上电子与离子由于质量的悬殊，导致这样的对称性往往受到质疑。解决的方法是引入一个近似：由于电子的速度远大于离子，不妨将离子看作不动，而电子在离子之间碰撞，这很类似于气体动理论中的 Lorentz 模型，或者是金属气理论中的 Drude-Lorentz 模型。

### 电子-离子碰撞项

**基本方程**：
$$
\mathcal{K}^{ei} = \frac{2\pi Z^2 e^4 \ln\Lambda}{m_e^2} \partial_{1r} \Phi_r^{ei}
$$
其中：
$$
\Phi_r^{ei} = \int d\mathbf{v}_2\, G_{rs}(\mathbf{v}_1 - \mathbf{v}_2) (\partial_{1s} - \mu \partial_{2s}) f^e(\mathbf{v}_1) f^i(\mathbf{v}_2)
$$

- $\mu = m_e/m_i \ll 1$（质量比）
- $\partial_{1s} \equiv \partial/\partial v_{1s}$（对电子速度求导）
- $\partial_{2s} \equiv \partial/\partial v_{2s}$（对离子速度求导）
- $G_{rs}(\mathbf{a}) = \dfrac{a^2\delta_{rs} - a_r a_s}{a^3}$（Landau 张量）

### 速度分布特征

**电子与离子分布对比**：
- 离子分布：$\langle |v_1 - u^e|^2 \rangle \sim 3T_i/m_i + |u^e - u^i|^2$
- 电子分布：$\langle |v_2 - u^e|^2 \rangle \sim 3T_e/m_e$

**近似条件**：
1. 电子漂移速度远小于热速度：
$$
|\mathbf{u}^e| \ll \sqrt{3T_e/m_e}
$$

2. 离子温度远低于标度化电子温度：
$$
T_i/T_e \ll m_i/m_e = \mu^{-1}
$$

那么就有：
$$
|\mathbf{v}_1 - \mathbf{u}^e| \gg |\mathbf{v}_2 - \mathbf{u}^e|
$$

在小参数 $|\mathbf{v}_2 - \mathbf{u}^e|$ 下展开：
$$
\begin{aligned}
G_{rs}(\mathbf{v}_1 - \mathbf{v}_2) &= G_{rs}(\mathbf{v}_1 - \mathbf{u}^e - (\mathbf{v}_2 - \mathbf{u}^e)) \\
&\approx G_{rs}^{(0)} - (v_{2s} - u_s^e) \partial_{1s} G_{rs}^{(0)} \\
&\quad + \frac{1}{2}(v_{2s} - u_s^e)(v_{2m} - u_m^e) \partial_{1s}\partial_{1m} G_{rs}^{(0)} + \cdots
\end{aligned}
$$
其中：
$$
G_{rs}^{(0)} \equiv G_{rs}(\mathbf{v}_1 - \mathbf{u}^e) = \frac{|\mathbf{v}_1 - \mathbf{u}^e|^2 \delta_{rs} - (v_{1r} - u_r^e)(v_{1s} - u_s^e)}{|\mathbf{v}_1 - \mathbf{u}^e|^3}
$$

对离子速度 $\mathbf{v}_2$ 积分，从而得到电子-离子碰撞算符的表达式：
$$
\begin{aligned}
\Phi_r^{ei} &\approx n_i \left[ G_{rs}^{(0)} + u_s^e \partial_{1s} G_{rs}^{(0)} + \frac{1}{2} a_{nm} \partial_{1n}\partial_{1m} G_{rs}^{(0)} + \cdots \right] \partial_{1s} f^e \\
&\quad - \mu n_i \left[ \partial_{1s} G_{rs}^{(0)} + \cdots \right] f^e
\end{aligned}
$$
其中：
$$
a_{nm} = \frac{T_i}{m_i}\delta_{rs} + \frac{1}{n_i m_i} \pi_{nm}^i + u_n^e u_m^e
$$

### 离子-电子碰撞算符

**基本方程**：
$$
\mathcal{K}^{ie} = \frac{2\pi Z^2 e^4 \ln\Lambda}{m_e^2} \mu \partial_{1r} \Phi_r^{ie}
$$
$$
\Phi_r^{ie} = \int d\mathbf{v}_2\, G_{rs}(\mathbf{v}_1 - \mathbf{v}_2) \left[ \mu f^i(\mathbf{v}_2) \partial_{1s} f^i(\mathbf{v}_1) - f^i(\mathbf{v}_1) \partial_{2s} f^e(\mathbf{v}_2) \right]
$$

展开过程是类似的，不过此时是对 $\boldsymbol{v}_1$ 展开，可以得到：
$$
\begin{aligned}
\Phi_r^{ie} &= -L_r f^i(\mathbf{v}_1) + M_{rm} (v_{1m} - u_m^e) f^i(\mathbf{v}_1) \\
&\quad - \frac{1}{2} N_{rmn} (v_{1m} - u_m^e)(v_{1n} - u_n^e) f^i(\mathbf{v}_1) + \cdots \\
&\quad + \mu \left[ L_{rs} \partial_{1s} f^i(\mathbf{v}_1) + \cdots \right]
\end{aligned}
$$

系数定义（电子分布泛函）：
$$
L_r = \int d\mathbf{v}_2\, G_{rs}^{(2)} \partial_{2s} f^e(\mathbf{v}_2)
$$
$$
M_{rm} = \int d\mathbf{v}_2\, \left[ \partial_{2m} G_{rs}^{(2)} \right] \partial_{2s} f^e(\mathbf{v}_2)
$$
$$
N_{rmn} = \int d\mathbf{v}_2\, \left[ \partial_{2m} \partial_{2n} G_{rs}^{(2)} \right] \partial_{2s} f^e(\mathbf{v}_2)
$$
$$
L_{rs} = \int d\mathbf{v}_2\, G_{rs}^{(2)} f^e(\mathbf{v}_2)
$$