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
> Def. (**Bernoulli distribution**, $X \sim Be(p)$ ) Bernoulli trial is that $A \in \mathcal{F}$, and we call the trial a success if $A$ occurs. Bernoulli distribution is based on single Bernoulli trial.

> Def. (**Binomial distribution**, $Y \sim Bin(n,p)$ ) Perform n independent Bernoulli trials with $p=\text{I\kern-0.15em P}(A)$, and let Bernoulli r.v.s. $X_{1}, X_{2} \dots X_{n}$ be the indicator funciton of success of the experiments. Let $Y:=\sum X_{i}$, then the p.m.f. $f_{Y}(k)={n \choose k} p^{k} (1-p)^{n-k},k=1, 2, \dots, n$. **Binomial process** is that $Y_n$ to be the number of successes in the first n $Be(p)$ trials.

> Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$, $F(x)=1-(1-p)^{x}$.

> Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose k-r} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$

> Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=1, 2, \dots$ The Poisson distribution is an approximation of a binomial distribution of a rare event in the case that **n is large, p is small**, and $\lambda=np$ is moderate.

> Def. (**Hypergeometric distribution**) $f_{X}(k)=\frac{ {K \choose k} {N-K \choose n-k} }{ N \choose n }$. $\text{I\kern-0.15em E} X=n N_{1}/N$, $Var X=n \frac{N_{1}}{N}\frac{N-K}{N}\frac{N-n}{N-1}$. The sample 

> Def. (**Multinomial**) Multi-outcome version of hypergeometric. $f_{X}(x)=\frac{n!}{ \prod x_{i}!} \prod p_{i}^{x_{i}}$, where $\text{I\kern-0.15em E} X_{i}=np_{i}, VarX_{i}=np_{i}(1-p_{i})$.