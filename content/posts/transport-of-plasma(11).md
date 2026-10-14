---
title: "等离子体输运理论（11）"
date: 2026-10-14
draft: false
math: true
series: ['plasma-transport']
series_order: 11
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# 矩的演化方程(一般形式)

## 流体力学平衡方程

**流体描述**：我们已经知道，无穷级列矩方程的求解是不可能的，因此需要对级列方程在某个级别做合理的截短近似。为了获得这个近似的流体力学矩的闭合方程组，必须要获得特殊非流体力学矩作为在同一个时空点的流体力学矩泛函的有效近似。

因此这里要做的就是推导矩的演化方程的一般形式，并且分析其共同结构。

写出流体力学平衡方程后，再对其运用局域准中性条件、压强张量与热流的矩展开和无量纲量，重写连续性方程、动量平衡方程以及两种粒子的温度方程。

### 连续性方程

$$
\partial_t \rho = -\nabla \cdot (\rho u)
$$

### 动量平衡方程

$$
\begin{aligned}
\partial_t (\rho u_r) = &-\nabla_s (\rho u_r u_s) - \nabla_s (n_e T_e + n_i T_i) \\
&-\sqrt{2} \nabla_s \bigl( n_e T_e h_{rs}^{(2)} + n_i T_i h_{rs}^{(2)} \bigr) \\
&+ \frac{e}{c} n_e \left( \frac{T_e}{m_e} \right)^{1/2} \varepsilon_{rsm} h_s^{(1)} B_m.
\end{aligned}
$$

### 温度方程(e)

$$
\begin{aligned}
&\partial_t T_e = -u \cdot \nabla T_e - \frac{2}{3} T_e \nabla \cdot u + \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(1)} \nabla T_e \\
&+ \frac{2}{3} T_e \nabla \cdot \left[ \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(1)} \right] - \frac{2}{3} \sqrt{2} T_e h_{rs}^{(2)} \nabla_r u \\
&+ \frac{2}{3} \sqrt{2} T_e h_{rs}^{(2)} \nabla_r \left[ \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(1)} \right] \\
&- \frac{\sqrt{10}}{3 n_e} \nabla_r \left[ n_e T_e \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(3)} \right] \\
&- \frac{1}{Z} Q^{(2)} - \frac{2}{3} T_e h_s^{(1)} Q_n^{(1)}.
\end{aligned}
$$

### 温度方程(i)

$$
\begin{aligned}
\partial_t T_i = &-u \cdot \nabla T_i - \frac{2}{3} T_i \nabla \cdot u - \frac{2}{3} \sqrt{2} T_i h_r^{(2)} \nabla_r u_s \\
&- \frac{\sqrt{10}}{3 n_i} \nabla_r \left[ n_i T_i \left( \frac{T_i}{m_i} \right)^{1/2} h_r^{(3)} \right] + Q^{(2)}.
\end{aligned}
$$

这里出现的碰撞项 $Q^{(1)}_r$ 与 $Q^{(2)}$ 都是量级为 $\mu$ 的量，而温度方程(e)的最后一项很小，因此两个温度量可以当作准守恒量。

流体力学平衡方程的结构中，第一组仅仅包含流体力学项，第二项则包含非流体力学矩，以及很小的碰撞项贡献。

**Maxwell方程组（新记号）**：

$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= 4\pi\sigma (\approx 0), & \nabla \times\mathbf{E} &= -\frac{1}{c} \partial_t \mathbf{B},\\
\nabla \cdot \mathbf{B} &= 0, & \nabla \times \mathbf{B} &= \frac{4\pi e}{c} n_e \left( \frac{T_e}{m_e} \right)^{1/2} h_r^{(1)}
\end{aligned}
$$

## 非流体力学方程

这一部分主要包含电动力学矩方程。之前已经得到过，对于慢运动，主要有以下两个方程：

**电荷守恒约束**：

$$
\nabla_n (n_e T_e^{1/2} h_n^{(1)}) = 0.
$$

**广义Ohm定律**：

$$
\begin{aligned}
\partial_t h_r^{(1)} = &\biggl( \frac{m_e}{T_e} \biggr)^{\!1/2} \biggl( \frac{e}{m_e} E_r \\
&+ \frac{1}{m_e n_e} \nabla_r (n_e T_e) + \frac{e}{m_e c} \epsilon_{rnm} u_m B_n \biggr) \\
&- \frac{e}{m_e c} \epsilon_{rnm} h_n^{(1)} B_n \\
&+ Q_r^{(1)} + U_r^{(1)} + C_r^{(1)} + N_r^{(1)}.
\end{aligned}
$$

其中 $Q_r^{(1)}$ 是无量纲摩擦力，后面三项展开形式略，碰撞项贡献：

$$
Q_{r_1 r_2...}^{a(m)} = n_a^{-1} \int d\mathbf{v} H_{r_1 r_2...}^{\text{(m)}} ((m_a / T_{a})^{1/2} (\mathbf{v} - \mathbf{u}^a)) \chi^a.
$$

## 矩的演化方程的共同结构

作者将级列方程在29M近似上截短，得到两种矩方程如下：

**(A) 矢量矩**

$$
\begin{aligned}
\partial_t h_r^{\alpha(3)} &= -\sqrt{\frac{5}{2}} \left( \frac{T_\alpha}{m_\alpha } \right)^{1/2} \frac{1}{T_\alpha} \nabla_r T_\alpha + \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(3)} B_n \\
&+ Q_r^{\alpha(3)} + U_r^{\alpha(3)} + D_r^{\alpha(3)} + C_r^{\alpha(3)} + N_r^{\alpha(3)}\\
\partial_t h_r^{\alpha(5)} &= \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(5)} B_n + Q_r^{\alpha(5)} + U_r^{\alpha(5)} + D_r^{\alpha(5)} + C_r^{\alpha(5)} + N_r^{\alpha(5)} \\
\partial_t h_r^{\alpha(7)} &= \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(7)} B_n + Q_r^{\alpha(7)} + U_r^{\alpha(7)} + D_r^{\alpha(7)} + C_r^{\alpha(7)} + N_r^{\alpha(7)}.
\end{aligned}
$$

**(B) 张量矩**

$$
\begin{aligned}
\partial_t h_{rs}^{\alpha(2)} &= -\sqrt{2} \mathscr{F}_{rs|pq} \nabla_p u_q + \frac{2e_\alpha}{m_\alpha c} \mathscr{F}_{rs|pq} \epsilon_{pnm} h_q^{\alpha(2)} B_n + Q_{rs}^{\alpha(2)} + U_{rs}^{\alpha(2)} + D_{rs}^{\alpha(2)} \\
&+ C_{rs}^{\alpha(2)} + N_{rs}^{\alpha(2)}\\
\partial_t h_{rs}^{\alpha(4)} &= \frac{2e_\alpha}{m_\alpha c} \mathscr{F}_{rs|pq} \epsilon_{pnm} h_q^{(4)} B_n + Q_{rs}^{\alpha(4)} + U_{rs}^{\alpha(4)} + D_{rs}^{\alpha(4)} + C_{rs}^{\alpha(4)} + N_{rs}^{\alpha(4)}\\
\partial_t h_{rs}^{\alpha(6)} &= \frac{2e_a}{m_\alpha c} \mathscr{F}_{rs|p q} \epsilon_{p m n a} h_{q m}^{\alpha(6)} B_n + Q_{rs}^{\alpha(6)} + U_{rs}^{\alpha(6)} + D_{rs}^{\alpha(6)} + C_{rs}^{\alpha(6)} + N_{rs}^{\alpha(6)}
\end{aligned}
$$

其中有对称化算符

$$
\mathscr{F}_{rs|pq} = \frac{1}{2} \left( \delta_{r,p} \delta_{s,q} + \delta_{r,q} \delta_{s,p} - \frac{1}{3} \delta_{r,s} \delta_{p,q} \right).
$$

### 共同结构

1. **流体力学变量 $\rho$、$u$、$T$ 的梯度与电磁场变量 $E$ 与 $B$**，这一部分为源项，从而使得非流体力学矩能够用流体力学矩表达。仅在于 $h_r^{(1)},h_r^{\alpha(1)},h_{rs}^{\alpha(2)},h_r^{(3)}$ 的方程中源项不为零
2. **来源于磁场项的Lorentz力**，正比于n次矩于磁场的矢积
3. **标志广义摩擦力的碰撞项 $Q^{\alpha(n)}_{...}$**，包含线性和非线性贡献
4. **一个高项 $U^{\alpha(n)}_{...}$**，包含动理方程的流项产生n+1次矩，由于在29M近似的截短，没有高于7次的高阶矩
5. **一个低项 $D^{\alpha(n)}_{...}$**，它涉及较低的n-1次矩的空间导数
6. **一组涉及n次矩的运流项 $C^{\alpha(n)}_{...}$**，以及它的导数
7. **非线性项 $N^{\alpha(n)}_{...}$**，包含广义摩擦项之外的其他非线性项。
8. **电场项E只出现在一次矩的源项之中**

## 广义摩擦

### 广义摩擦概述

现在来处理广义碰撞项，经过变换后，问题归结为四种碰撞项中系数的计算

- 在21M近似下，广义摩擦项（碰撞项）可表示为**Hermite矩**的线性与非线性组合。
- 区分四种碰撞类型：电子-电子（e-e）、电子-离子（e-i）、离子-离子（i-i）、离子-电子（i-e）。
- 线性部分：$Q^{(M)} = \sum_N C_{MN} h^{(N)}$，非线性部分：$Q^{(M)} = \sum_{N,P} D_{M|NP} h^{(N)} h^{(P)}$。
- 特征弛豫时间：
  $$
  \frac{1}{\tau_e} = \frac{4\sqrt{2\pi} Z^2 e^4 n_e \ln\Lambda}{3 m_e^{1/2} T_e^{3/2}}, \quad
  \frac{1}{\tau_i} = \frac{4\sqrt{2\pi} Z^4 e^4 n_i \ln\Lambda}{3 m_i^{1/2} T_i^{3/2}}.
  $$

### 广义摩擦项的线性部分

#### 电子广义摩擦项（$Q_e^{(M)}$）——线性部分

- 线性碰撞矩阵：
  $$
  C_{MN}^e = -\frac{1}{\tau_e}\bigl( \alpha_{MN} + Z^{-1}\beta_{MN} \bigr),
  $$
  其中 $\alpha_{MN}$（e-i贡献）占主导，$\beta_{MN}$（e-e贡献）含小因子 $Z^{-1}$。

- 矢量矩耦合（$M=1,3,5$）：
  $$
  \begin{aligned}
  \tau_e Q_e^{(1)} &= -c_{11}^e h_e^{(1)} - c_{13}^e h_e^{(3)} - c_{15}^e h_e^{(5)} - \cdots,\\
  \tau_e Q_e^{(3)} &= -c_{31}^e h_e^{(1)} - c_{33}^e h_e^{(3)} - c_{35}^e h_e^{(5)} - \cdots,\\
  \tau_e Q_e^{(5)} &= -c_{51}^e h_e^{(1)} - c_{53}^e h_e^{(3)} - c_{55}^e h_e^{(5)} - \cdots,
  \end{aligned}
  $$
  系数 $c_{MN}^e = \alpha_{MN} + Z^{-1}\beta_{MN}$，且 $c_{MN}^e = c_{NM}^e$。

- 张量矩耦合（$M=2,4,6$）：
  $$
  \tau_e Q_e^{(2)} = -c_{22}^e h_e^{(2)} - c_{24}^e h_e^{(4)} - c_{26}^e h_e^{(6)} - \cdots,
  $$
  类似有 $Q_e^{(4)}, Q_e^{(6)}$。

#### 离子广义摩擦项（$Q_i^{(M)}$）——线性部分

- 线性碰撞矩阵仅来自**离子-离子碰撞**：
  $$
  C_{MN}^i = -\frac{1}{\tau_i}\, \beta'_{MN}.
  $$

- 矢量矩耦合（$M=1,3,5,7$）：
  $$
  \tau_i Q_i^{(1)} = -c_{11}^i h_i^{(1)} - c_{13}^i h_i^{(3)} - c_{15}^i h_i^{(5)} - \cdots,
  $$
  其中系数 $c_{MN}^i$ 对称。

- 张量矩耦合（$M=2,4,6$）：
  $$
  \tau_i Q_i^{(2)} = -c_{22}^i h_i^{(2)} - c_{24}^i h_i^{(4)} - c_{26}^i h_i^{(6)} - \cdots,
  $$
  类似有 $Q_i^{(4)}, Q_i^{(6)}$。

- **离子-电子碰撞**贡献为 $O(\mu)$，在21M近似下忽略。

### 广义摩擦的非线性部分

- 非线性系数：
  $$
  D_{M|NP}^{e} = \frac{1}{\tau_e}\bigl( d_{M|NP}^{\text{(e-i)}} + Z^{-1} d_{M|NP}^{\text{(e-e)}} \bigr).
  $$

- 在13M近似下，典型非线性项：
  $$
  \begin{aligned}
  Q_e^{(1)} &\supset \frac{1}{\tau_e} d_{1|1,2}\, h_e^{(1)} h_e^{(2)},\\
  Q_e^{(2)} &\supset \frac{1}{\tau_e} d_{2|1,1}\, h_e^{(1)} h_e^{(1)}.
  \end{aligned}
  $$

- 离子碰撞的非线性项仅来自**离子-离子碰撞**：
  $$
  Q_i^{(M)} \supset \sum_{N,P} D_{M|NP}^{i}\, h_i^{(N)} h_i^{(P)},
  $$
  系数 $D_{M|NP}^{i} \sim \tau_i^{-1}$。

### 异类碰撞的交叉贡献

- **电子-离子碰撞**在电子方程中占主导（线性部分 $\alpha_{MN}$），并贡献非线性项。
- **离子-电子碰撞**对离子矩的贡献为 $O(\mu)$，可忽略：
  $$
  C_{MN}^{i\text{(i-e)}} \approx 0,\quad D_{M|NP}^{i\text{(i-e)}} \approx 0.
  $$
- **温度交换项**（出现在电子和离子的温度方程中）：
  $$
  Q^{(2)} = -\frac{2Z}{\tau_e}\,\mu\,(T_i - T_e),\quad \mu = \frac{m_e}{m_i}.
  $$
  该过程极慢（弛豫时间 $\sim \tau_e/\mu$），因此 $T_e$ 与 $T_i$ 为准守恒量。

### 四种碰撞贡献总结

| 碰撞类型 | 影响方程 | 贡献大小 |
| --- | --- | --- |
| e-e | 电子矩 | $O(Z^{-1}/\tau_e)$ |
| e-i | 电子矩 | $O(1/\tau_e)$ |
| i-i | 离子矩 | $O(1/\tau_i)$ |
| i-e | 离子矩 | $O(\mu/\tau_e)$ |

*表：广义摩擦项中四种碰撞的贡献*

**广义摩擦的内禀属性**：广义摩擦（即碰撞项）与 Hermite 矩（即矩变量，也可称为“流”）之间的关系（如线性关系 $Q=Ch$）中的系数 C（以及非线性系数D ）完全由碰撞算符的矩阵元决定，而与宏观的梯度、电场、磁场等外部条件无关。
