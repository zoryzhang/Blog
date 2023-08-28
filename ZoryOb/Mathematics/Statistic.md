---
link: https://zoryzhang.notion.site/Statistic-c2713936ee3c472184e31995e2642ca7
notionID: c2713936-ee3c-4721-84e3-1995e2642ca7
---

For robust statistics, see [the page](Robust%20Statistics.md).

# Textbook

# Matrix cookbook
- [The matrix cookbook](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)
- $a$ for scalar, $\underline a$ for vector, $A$ for matrix.
- $X$ for random variable, $\underline X$ for random vector, $\textbf X$ for random matrix.
- $\text{I\kern-0.15em E}[\underline a^{T}  \underline {{X}}]=\underline a \cdot \text{I\kern-0.15em E}  \underline {{X}}$; $\text{I\kern-0.15em E}[A\underline {{X}}]=A \text{I\kern-0.15em E}\underline {{X}}$; $\text{I\kern-0.15em E}A\textbf{X}B=A \text{I\kern-0.15em E}  [\textbf{X}]B$.
- $\underline \mu:=\text{I\kern-0.15em E}\underline {X}, \underline v:=\text{I\kern-0.15em E} \underline {Y}$.

# Covariance
1. $Cov[X,Y]=\text{I\kern-0.15em E}[ (X-\text{I\kern-0.15em E}X)(Y-\text{I\kern-0.15em E}Y) ]=\text{I\kern-0.15em E}[ (X-\text{I\kern-0.15em E}X)(Y-\text{I\kern-0.15em E}Y) ]$.
2. $V[\frac{X}{\sigma_{X}}]=1$, $\rho_{XY}=Cov[\tilde X,\tilde Y]=\frac{Cov[X,Y]}{\sigma_{X} \sigma_{Y}}$
3. The **covariance matrix** $V[\underline X]=\text{I\kern-0.15em E} [(\underline {X}-\underline {\mu}) (\underline {X}-\underline {\mu})^{T}]=\text{I\kern-0.15em E}  \underline {{X}} \underline {{X}}^{T}-\underline {\mu} \underline {\mu}^{T}$.
4. The **variance of r.v.** in the form of $\underline {a} \cdot \underline {X}$: $V[\underline {a} \cdot \underline {X}]=\underline {a}^{T} V[\underline {X}] \underline {a}$; $V[A \underline {X}]=A V[\underline {X}]A^{T}$. When $||\underline {a}||=1$, it's taking the variance in the direction of $\underline {a}$, over the joint p.d.f. (consider variance as the width of the function picture along certain axis).
# Multivariate normal
1. Standard normal: $\underline {Z} \sim N(\underline {0}, I)$.
2. (Stretch) $\underline {X}=D \underline {Z}$ where $D=diag(\sigma_{1}, \sigma_{2}, \dots)$, then $\underline {X} \sim N(\underline {0},D^{2})$.
3. (Rotate) $\underline {Y}=Q \underline {X}$ where $Q^{T}Q=I$ (orthogonal), then $\underline {Y} \sim N(\underline {0},V)$. Given D to find V and Q, consider that by (Covariance-4), 
$$
V=V[Y]=V[QX]=QV[X]Q^{T}=QD^{2}Q^{T}
$$
    Eigenvalue decomposition solves this problem. Say $eigen(V)=\lambda_{1}, \dots$, then $\lambda_{i}=\sigma_{i}^{2}$.

# **Hypothesis Testing**

# **Kullback–Leibler divergence**

a measure of how one probability distribution _P_ is different from a second, reference probability distribution _Q_.





# STAT 400
Def. Outcome space / Sample space.
Def. Event. Occurance.
Def. 