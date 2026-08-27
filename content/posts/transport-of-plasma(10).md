---
title: "等离子体输运理论(10)"
date: 2026-08-27
draft: false
math: true
tags: ["等离子体", "输运理论","笔记"]
categories: ["物理"]
---
# Hermite 矩估计

## 矩的分类

### 双流体的分类方式

**等离体动力学矩**：包含 $n_a$、$\boldsymbol{u}^a$、$T_a$，为参考局域平衡分布 $f^{a0}$ 的矩，它们的信息完全确定了参考态。

**非等离体动力学矩**：分布函数全部 Hermite 矩 $h^{a(m)}_{\cdots}(\boldsymbol{x},t)$ 的集合，在处于参考局域平衡态的时候，它们的值恒为零，因此它们确定了真实态对参考态的偏差。

---

### 单流体的分类方式

**标量矩**：
$$
\begin{pmatrix} n_e \\ n_i \end{pmatrix}
\Rightarrow
\begin{pmatrix} \rho = \sum_a m_a n_a \\ \sigma = \sum_a e_a n_a \end{pmatrix}
$$

**矢量矩**：
$$
\begin{pmatrix} \boldsymbol{u}^e \\ \boldsymbol{u}^i \end{pmatrix}
\Rightarrow
\begin{pmatrix} \rho \boldsymbol{u} = \sum_a m_a n_a \boldsymbol{u}^a \\ \boldsymbol{j} = \sum_a e_a n_a \boldsymbol{u}^a \end{pmatrix}
$$

**当电流 $\boldsymbol{j}$ 不是有用量时**：
$$
\begin{pmatrix} \boldsymbol{u}^i \\ \boldsymbol{u}^e \end{pmatrix}
\Rightarrow
\begin{pmatrix} \rho \boldsymbol{u} = \sum_a m_a n_a \boldsymbol{u}^a \\ \boldsymbol{\Gamma}^e = n_e \boldsymbol{u}^e \end{pmatrix}
$$

质量密度 $\rho$，质量流 $\rho \boldsymbol{u}$ 是守恒量，而温度 $T_e, T_i$ 是准守恒量，它们全部被定义为参考局域平衡态的矩，在它们的演化方程中几乎没有来自碰撞项的任何贡献。

---

### 非流体力学矩

电动力学矩包括电荷密度 $\sigma$ 和电流 $\boldsymbol{j}$，其中电荷密度不出现在流体方程中，它们仅仅出现在 Poisson 方程中，根据上一节的讨论，可以令 $\sigma \approx 0$。电流项 $\boldsymbol{j}$ 不是一个守恒量，它包含碰撞项的贡献，主要由摩擦力项 $\boldsymbol{R}$ 带来，对于粒子流 $\boldsymbol{\Gamma}^a$ 来说也是一样的。

**无量纲化**：
$$
\begin{aligned}
j_r &= e n_e \left( \frac{T_e}{m_e} \right)^{1/2} h_r^{(1)} \\
\Gamma^e_r &= n_a \left( \frac{T_a}{m_a} \right)^{1/2} h_r^{a(1)} \\
h_r^{(1)} &= -h_r^{e(1)} + \left( \frac{m_e}{T_e} \right)^{1/2} u_r
\end{aligned}
$$
注意 $h_r^{(1)}$ 和 $h_r^{a(1)}$ 并不是 Hermite 矩，它们根据约束条件并不恒为 0。

---

以下特殊非流体力学矩除了物理重要性外，还具有一个共同性质：
- 粒子流：$\Gamma_r^e \rightarrow h_r^{a(1)}$
- 电流：$j_r \rightarrow h_r^{(1)}$
- 压强张量：$\pi_{rs}^a \rightarrow h_{rs}^{a(2)}$
- 热流：$q_r^a \rightarrow h_r^{a(3)}$

它们的演化方程中出现一个**源项**，该源项是流体力学矩的函数；所有其他非流体力学矩的方程**不具有**这种源项。


# 矩的演化方程

## 流体力学平衡方程

**流体描述**：我们已经知道，无穷级列矩方程的求解是不可能的，因此需要对级列方程在某个级别做合理的截短近似。为了获得这个近似的流体力学矩的闭合方程组，必须要获得特殊非流体力学矩作为在同一个时空点的流体力学矩泛函的有效近似。

因此这里要做的就是推导矩的演化方程的一般形式，并且分析其共同结构。

写出流体力学平衡方程后，再对其运用局域准中性条件、压强张量与热流的矩展开和无量纲量，重写连续性方程、动量平衡方程以及两种粒子的温度方程。

### 连续性方程
$$
\partial_t \rho = -\nabla \cdot (\rho \boldsymbol{u})
$$

### 动量平衡方程
$$
\begin{aligned}
\partial_t (\rho u_r) &= -\nabla_s (\rho u_r u_s) - \nabla_s (n_e T_e + n_i T_i) \\
&\quad - \sqrt{2} \nabla_s \bigl( n_e T_e h_{rs}^{e(2)} + n_i T_i h_{rs}^{i(2)} \bigr) \\
&\quad + \frac{e}{c} n_e \left( \frac{T_e}{m_e} \right)^{1/2} \varepsilon_{rsm} h_s^{(1)} B_m
\end{aligned}
$$

### 温度方程（电子）
$$
\begin{aligned}
\partial_t T_e &= -u \cdot \nabla T_e - \frac{2}{3} T_e \nabla \cdot u + \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(1)} \nabla T_e \\
&\quad + \frac{2}{3} T_e \nabla \cdot \left[ \left( \frac{T_e}{m_e} \right)^{1/2} \boldsymbol{h}^{(1)} \right] - \frac{2}{3} \sqrt{2} T_e h_{rs}^{e(2)} \nabla_r u_s \\
&\quad + \frac{2}{3} \sqrt{2} T_e h_{rs}^{e(2)} \nabla_r \left[ \left( \frac{T_e}{m_e} \right)^{1/2} h_s^{(1)} \right] \\
&\quad - \frac{\sqrt{10}}{3 n_e} \nabla_r \left[ n_e T_e \left( \frac{T_e}{m_e} \right)^{1/2} h_r^{e(3)} \right] \\
&\quad - \frac{1}{Z} Q^{(2)} - \frac{2}{3} T_e h_s^{(1)} Q_r^{(1)}
\end{aligned}
$$

### 温度方程（离子）
$$
\begin{aligned}
\partial_t T_i &= -u \cdot \nabla T_i - \frac{2}{3} T_i \nabla \cdot u - \frac{2}{3} \sqrt{2} T_i h_{rs}^{i(2)} \nabla_r u_s \\
&\quad - \frac{\sqrt{10}}{3 n_i} \nabla_r \left[ n_i T_i \left( \frac{T_i}{m_i} \right)^{1/2} h_r^{i(3)} \right] + Q^{(2)}
\end{aligned}
$$

这里出现的碰撞项 $Q^{(1)}_r$ 与 $Q^{(2)}$ 都是量级为 $\mu$ 的量，而温度方程 (e) 的最后一项很小，因此两个温度量可以当作准守恒量。

流体力学平衡方程的结构中，第一组仅仅包含流体力学项，第二组则包含非流体力学矩，以及很小的碰撞项贡献。

### Maxwell 方程组
$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= 4\pi\sigma \;(\approx 0), \\
\nabla \times \mathbf{E} &= -\frac{1}{c} \partial_t \mathbf{B}, \\
\nabla \cdot \mathbf{B} &= 0, \\
\nabla \times \mathbf{B} &= \frac{4\pi e}{c} n_e \left( \frac{T_e}{m_e} \right)^{1/2} \boldsymbol{h}^{(1)}
\end{aligned}
$$


## 非流体力学方程

这一部分主要包含电动力学矩方程。之前已经得到过，对于慢运动，主要有以下两个方程：

**电荷守恒约束**：
$$
\nabla_n (n_e T_e^{1/2} h_n^{(1)}) = 0
$$

**广义 Ohm 定律**：
$$
\begin{aligned}
\partial_t h_r^{(1)} &= \left( \frac{m_e}{T_e} \right)^{1/2} \left( \frac{e}{m_e} E_r + \frac{1}{m_e n_e} \nabla_r (n_e T_e) + \frac{e}{m_e c} \epsilon_{rnm} u_m B_n \right) \\
&\quad - \frac{e}{m_e c} \epsilon_{rnm} h_n^{(1)} B_n + Q_r^{(1)} + U_r^{(1)} + C_r^{(1)} + N_r^{(1)}
\end{aligned}
$$

其中 $Q_r^{(1)}$ 是无量纲摩擦力，后面三项展开形式略，碰撞项贡献：
$$
Q_{r_1 r_2 \cdots}^{a(m)} = n_a^{-1} \int d\mathbf{v} \, H_{r_1 r_2 \cdots}^{(m)} \bigl( (m_a/T_a)^{1/2} (\mathbf{v} - \mathbf{u}^a) \bigr) \chi^a
$$


## 矩的演化方程的共同结构

作者将级列方程在 29M 近似上截短，得到两种矩方程如下：

**(A) 矢量矩**
$$
\begin{aligned}
\partial_t h_r^{\alpha(3)} &= -\sqrt{\frac{5}{2}} \left( \frac{T_\alpha}{m_\alpha} \right)^{1/2} \frac{1}{T_\alpha} \nabla_r T_\alpha + \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(3)} B_n \\
&\quad + Q_r^{\alpha(3)} + U_r^{\alpha(3)} + D_r^{\alpha(3)} + C_r^{\alpha(3)} + N_r^{\alpha(3)} \\
\partial_t h_r^{\alpha(5)} &= \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(5)} B_n + Q_r^{\alpha(5)} + U_r^{\alpha(5)} + D_r^{\alpha(5)} + C_r^{\alpha(5)} + N_r^{\alpha(5)} \\
\partial_t h_r^{\alpha(7)} &= \frac{e_\alpha}{m_\alpha c} \epsilon_{rnm} h_m^{\alpha(7)} B_n + Q_r^{\alpha(7)} + U_r^{\alpha(7)} + D_r^{\alpha(7)} + C_r^{\alpha(7)} + N_r^{\alpha(7)}
\end{aligned}
$$

**(B) 张量矩**
$$
\begin{aligned}
\partial_t h_{rs}^{\alpha(2)} &= -\sqrt{2} \mathscr{F}_{rs|pq} \nabla_p u_q + \frac{2e_\alpha}{m_\alpha c} \mathscr{F}_{rs|pq} \epsilon_{pnm} h_q^{\alpha(2)} B_n \\
&\quad + Q_{rs}^{\alpha(2)} + U_{rs}^{\alpha(2)} + D_{rs}^{\alpha(2)} + C_{rs}^{\alpha(2)} + N_{rs}^{\alpha(2)} \\
\partial_t h_{rs}^{\alpha(4)} &= \frac{2e_\alpha}{m_\alpha c} \mathscr{F}_{rs|pq} \epsilon_{pnm} h_q^{\alpha(4)} B_n + Q_{rs}^{\alpha(4)} + U_{rs}^{\alpha(4)} + D_{rs}^{\alpha(4)} + C_{rs}^{\alpha(4)} + N_{rs}^{\alpha(4)} \\
\partial_t h_{rs}^{\alpha(6)} &= \frac{2e_\alpha}{m_\alpha c} \mathscr{F}_{rs|pq} \epsilon_{pnm} h_{qm}^{\alpha(6)} B_n + Q_{rs}^{\alpha(6)} + U_{rs}^{\alpha(6)} + D_{rs}^{\alpha(6)} + C_{rs}^{\alpha(6)} + N_{rs}^{\alpha(6)}
\end{aligned}
$$

其中对称化算符：
$$
\mathscr{F}_{rs|pq} = \frac{1}{2} \left( \delta_{r,p} \delta_{s,q} + \delta_{r,q} \delta_{s,p} - \frac{1}{3} \delta_{r,s} \delta_{p,q} \right)
$$

### 共同结构

1. **流体力学变量 $\rho$、$\boldsymbol{u}$、$T$ 的梯度与电磁场变量 $\boldsymbol{E}$ 与 $\boldsymbol{B}$**：这一部分为源项，从而使得非流体力学矩能够用流体力学矩表达。仅在于 $h_r^{(1)}, h_r^{\alpha(1)}, h_{rs}^{\alpha(2)}, h_r^{\alpha(3)}$ 的方程中源项不为零。
2. **来源于磁场项的 Lorentz 力**：正比于 n 次矩与磁场的矢积。
3. **标志广义摩擦力的碰撞项 $Q^{\alpha(n)}_{\cdots}$**：包含线性和非线性贡献。
4. **一个高项 $U^{\alpha(n)}_{\cdots}$**：包含动理方程的流项产生 $n+1$ 次矩，由于在 29M 近似的截短，没有高于 7 次的高阶矩。
5. **一个低项 $D^{\alpha(n)}_{\cdots}$**：涉及较低的 $n-1$ 次矩的空间导数。
6. **一组涉及 n 次矩的运流项 $C^{\alpha(n)}_{\cdots}$**，以及它的导数。
7. **非线性项 $N^{\alpha(n)}_{\cdots}$**：包含广义摩擦项之外的其他非线性项。
8. **电场项 $\boldsymbol{E}$ 只出现在一次矩的源项之中**。


# 广义摩擦

## 广义摩擦概述

现在来处理广义碰撞项，经过变换后，问题归结为四种碰撞项中系数的计算：

- 在 21M 近似下，广义摩擦项（碰撞项）可表示为 **Hermite 矩**的线性与非线性组合。
- 区分四种碰撞类型：电子-电子（e-e）、电子-离子（e-i）、离子-离子（i-i）、离子-电子（i-e）。
- 线性部分：$Q^{(M)} = \sum_N C_{MN} h^{(N)}$，非线性部分：$Q^{(M)} = \sum_{N,P} D_{M|NP} h^{(N)} h^{(P)}$。
- 特征弛豫时间：
  $$
  \frac{1}{\tau_e} = \frac{4\sqrt{2\pi} Z^2 e^4 n_e \ln\Lambda}{3 m_e^{1/2} T_e^{3/2}}, \qquad
  \frac{1}{\tau_i} = \frac{4\sqrt{2\pi} Z^4 e^4 n_i \ln\Lambda}{3 m_i^{1/2} T_i^{3/2}}
  $$


## 广义摩擦项的线性部分

### 电子广义摩擦项（$Q_e^{(M)}$）——线性部分

- 线性碰撞矩阵：
  $$
  C_{MN}^e = -\frac{1}{\tau_e} \left( \alpha_{MN} + Z^{-1} \beta_{MN} \right)
  $$
  其中 $\alpha_{MN}$（e-i 贡献）占主导，$\beta_{MN}$（e-e 贡献）含小因子 $Z^{-1}$。

- 矢量矩耦合（$M=1,3,5$）：
  $$
  \begin{aligned}
  \tau_e Q_e^{(1)} &= -c_{11}^e h_e^{(1)} - c_{13}^e h_e^{(3)} - c_{15}^e h_e^{(5)} - \cdots, \\
  \tau_e Q_e^{(3)} &= -c_{31}^e h_e^{(1)} - c_{33}^e h_e^{(3)} - c_{35}^e h_e^{(5)} - \cdots, \\
  \tau_e Q_e^{(5)} &= -c_{51}^e h_e^{(1)} - c_{53}^e h_e^{(3)} - c_{55}^e h_e^{(5)} - \cdots,
  \end{aligned}
  $$
  系数 $c_{MN}^e = \alpha_{MN} + Z^{-1} \beta_{MN}$，且 $c_{MN}^e = c_{NM}^e$。

- 张量矩耦合（$M=2,4,6$）：
  $$
  \tau_e Q_e^{(2)} = -c_{22}^e h_e^{(2)} - c_{24}^e h_e^{(4)} - c_{26}^e h_e^{(6)} - \cdots,
  $$
  类似有 $Q_e^{(4)}, Q_e^{(6)}$。

### 离子广义摩擦项（$Q_i^{(M)}$）——线性部分

- 线性碰撞矩阵仅来自 **离子-离子碰撞**：
  $$
  C_{MN}^i = -\frac{1}{\tau_i} \beta'_{MN}
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

- **离子-电子碰撞**贡献为 $O(\mu)$，在 21M 近似下忽略。


## 广义摩擦的非线性部分

- 非线性系数：
  $$
  D_{M|NP}^{e} = \frac{1}{\tau_e} \left( d_{M|NP}^{\text{(e-i)}} + Z^{-1} d_{M|NP}^{\text{(e-e)}} \right)
  $$

- 在 13M 近似下，典型非线性项：
  $$
  Q_e^{(1)} \supset \frac{1}{\tau_e} d_{1|1,2}\, h_e^{(1)} h_e^{(2)}, \qquad
  Q_e^{(2)} \supset \frac{1}{\tau_e} d_{2|1,1}\, h_e^{(1)} h_e^{(1)}
  $$

- 离子碰撞的非线性项仅来自 **离子-离子碰撞**：
  $$
  Q_i^{(M)} \supset \sum_{N,P} D_{M|NP}^{i}\, h_i^{(N)} h_i^{(P)}
  $$
  系数 $D_{M|NP}^{i} \sim \tau_i^{-1}$。


## 异类碰撞的交叉贡献

- **电子-离子碰撞**在电子方程中占主导（线性部分 $\alpha_{MN}$），并贡献非线性项。
- **离子-电子碰撞**对离子矩的贡献为 $O(\mu)$，可忽略：
  $$
  C_{MN}^{i\text{(i-e)}} \approx 0, \qquad D_{M|NP}^{i\text{(i-e)}} \approx 0
  $$
- **温度交换项**（出现在电子和离子的温度方程中）：
  $$
  Q^{(2)} = -\frac{2Z}{\tau_e}\,\mu\,(T_i - T_e), \qquad \mu = \frac{m_e}{m_i}
  $$
  该过程极慢（弛豫时间 $\sim \tau_e/\mu$），因此 $T_e$ 与 $T_i$ 为准守恒量。


**广义摩擦的内禀属性**：广义摩擦（即碰撞项）与 Hermite 矩（即矩变量，也可称为“流”）之间的关系（如线性关系 $Q = C h$）中的系数 $C$（以及非线性系数 $D$）完全由碰撞算符的矩阵元决定，而与宏观的梯度、电场、磁场等外部条件无关。