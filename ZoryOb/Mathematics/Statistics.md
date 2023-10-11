---
link: https://zoryzhang.notion.site/Statistic-c2713936ee3c472184e31995e2642ca7
notionID: c2713936-ee3c-4721-84e3-1995e2642ca7
---

>  The note of UIUC course STAT 400 in Fall 2023, by Zory Zhang. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (maybe not up-to-date) can be found [here](Statistics.pdf).

For robust statistics, see [the page](Robust%20Statistics.md).

# Preliminaries
The following content is based on the course STAT400@UIUC. [Probability knowledge](./Probability.md) is assumed.

# Textbook


# Ch0 Matrix cookbook
- [The matrix cookbook](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)
- $a$ for scalar, $\underline a$ for vector, $A$ for matrix.
- $X$ for random variable, $\underline X$ for random vector, $\textbf X$ for random matrix.
- $\text{I\kern-0.15em E}[\underline a^{T}  \underline {{X}}]=\underline a \cdot \text{I\kern-0.15em E}  \underline {{X}}$; $\text{I\kern-0.15em E}[A\underline {{X}}]=A \text{I\kern-0.15em E}\underline {{X}}$; $\text{I\kern-0.15em E}A\textbf{X}B=A \text{I\kern-0.15em E}  [\textbf{X}]B$.
- $\underline \mu:=\text{I\kern-0.15em E}\underline {X}, \underline v:=\text{I\kern-0.15em E} \underline {Y}$.

# Ch1 Distributions

> Def. (**Bernoulli distribution**, $X \sim Be(p)$ ) Bernoulli trial is that $A \in \mathcal{F}$, and we call the trial a success if $A$ occurs. Bernoulli distribution is based on single Bernoulli trial.

> Def. (**Binomial distribution**, $Y \sim Bin(n,p)$ ) Perform n independent Bernoulli trials with $p=\text{I\kern-0.15em P}(A)$, and let Bernoulli r.v.s. $X_{1}, X_{2} \dots X_{n}$ be the indicator funciton of success of the experiments. Let $Y:=\sum X_{i}$, then the p.m.f. $f_{Y}(k)={n \choose k} p^{k} (1-p)^{n-k},k=1, 2, \dots, n$. **Binomial process** is that $Y_n$ to be the number of successes in the first n $Be(p)$ trials.

> Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$, $F(x)=1-(1-p)^{x}$.

> Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose k-r} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$

> Def. (**Approximate poisson process** with param $\lambda>0$) Let the number of **occurrences** of some event in a given **continuous interval** be counted. If
> 1. The number of occurrences in nonoverlapping subintervals are independent.
> 2. The probability of exactly one occurence in a sufficiently short subinterval of length h is approximately $\lambda h$.
> 3. The probability of more than one occurence in a sufficiently short subinterval of length h is essentially 0.

> Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) An approximation of number of occurances in an interval of length 1 is given. Consider partition the unit interval into n subintervals. As n becomes larger, the length of subinterval become smaller and thus more likely the last two properties hold. For a large n, $\text{I\kern-0.15em P}(X=k) \sim {n \choose k} (\frac{\lambda}{n})^{k} (1-\frac{\lambda}{n})^{n-k}$, and it converges to $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=0,1, 2, \dots$

Rmk. $M(t)=e^{\lambda(e^{t}-1)}$, then $\mu = \sigma^{2}=\lambda$.

E.g. Number of customers of a shop between 5-6pm.

> Def. (**Hypergeometric distribution**) $f_{X}(k)=\frac{ {K \choose k} {N-K \choose n-k} }{ N \choose n }$. $\text{I\kern-0.15em E} X=n N_{1}/N$, $Var X=n \frac{N_{1}}{N}\frac{N-K}{N}\frac{N-n}{N-1}$. The sample 

> Def. (**Multinomial**) Multi-outcome version of hypergeometric. $f_{X}(x)=\frac{n!}{ \prod x_{i}!} \prod p_{i}^{x_{i}}$, where $\text{I\kern-0.15em E} X_{i}=np_{i}, VarX_{i}=np_{i}(1-p_{i})$.

---

> Def. (**Exponential distribution**, $X \sim Exp(\lambda)$ ) Define X as the waiting time for the first occurance in a poisson process. Then $F_{X}(x)=1-\text{I\kern-0.15em P}(\text{no occurences in [0,x]})$, therefore
> $$
F_{X}(x)= 
\begin{cases}
0, x<0 
\\\\ 1-e^{-\lambda x} ,x \ge 0 
\end{cases}
,f_{X}(x)=F'_{X}(x)= 
\begin{cases}
0, x<0  
\\ \lambda e^{-\lambda x} ,x \ge 0 
\end{cases} $$

Rmk.
1. It's usually expressed as $\theta=\frac{1}{\lambda}, f(x)=\frac{1}{\theta}e^{- \frac{x}{\theta}}$.
2. $M(t)=\frac{1}{1-\theta t}$ for $t<\frac{1}{\theta}$, thus $\mu=\theta, \sigma^{2}=\theta^{2}$, Fisher's moment coefficient of skewness is 2.
3. (Memoryless) $\text{I\kern-0.15em P}(X>s+t|X>t)=\text{I\kern-0.15em P}(X>s)$.
4. (Failture/hazard rate for positive r.v.) $r(t) = \lim_{h \downarrow 0} \frac{1}{h} \text{I\kern-0.15em P}(X \le t+h|X>t) = \frac{f(t)}{1-F(t)}=\lambda$.

> Def. (**Gamma function**) For $t>0$, $\Gamma(t)=\int_{0}^{\infty} y^{t-1}e^{-y} \ \mathrm{d} y$.

Rmk. $\Gamma(t)=(-y^{t-1}e^{-y})_{y=0}^{\infty} + \int_{0}^{\infty} (t-1) y^{t-2}e^{-y} \ \mathrm{d} y=(t-1) \Gamma(t-1)$. $\Gamma(1)=1$. When t is an integer, $\Gamma(t)=(t-1)!$.

> Def. (**Gamma distribution**, $X \sim Gamma(\alpha, \theta)$ ) For $x \ge 0$, $f_{X}(x)=\frac{1}{\Gamma(\alpha) \theta^{\alpha}} x^{\alpha-1}e^{-x/\theta}$. In a poisson process, the waiting time of first occurence is $Exp(\theta=1/\lambda)$, now gamma distribution describes the waiting time until $\alpha$-th occurrence.

Rmk. $\text{I\kern-0.15em E} X=\alpha \theta, Var X=\alpha \theta^{2}$.

> Def. (**Normal/Gaussian distribution**, $X \sim \mathcal{N}(\mu,\sigma^{2})$ ) $f_{X}(x)=\frac{1}{ \sqrt{2\pi} \sigma } \exp ( - \frac{(x-\mu)^{2}}{2 \sigma^{2}} )$. Standard normal distribution $Y \sim \mathcal{N}(0,1)$, denote the p.d.f. as $\phi(x)=\frac{1}{\sqrt{2\pi}} \exp(\frac{-x^{2}}{2})$.

Rmk. To compute $I=\int_{-\infty}^{\infty}\phi(x) \ \mathrm{d}x$, consider 

$$
\begin{aligned}
I^{2}
&=\int_{-\infty}^{\infty} \phi(x) \ \mathrm{d}x \int_{-\infty}^{\infty}\phi(y) \ \mathrm{d}y
\\\\ &=\frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp(- \frac{x^{2}+y^{2}}{2} ) \ \mathrm{d}x \ \mathrm{d}y
\\\\ &=\frac{1}{2\pi} \int_{0}^{2 \pi} \int_{0}^{\infty} \exp(- \frac{r^{2}}{2} ) r \ \mathrm{d}r \ \mathrm{d} \theta=1
\end{aligned}
$$

Rmk. For normal distribution, the i-th central moment of $N(\mu,\sigma^2)$ is $\sigma_i=\begin{cases} 0, \text{ if i odd}, \\  \sigma^{i}(i-1)!!, \text{ o.w.} \end{cases}$

> Def. (**(standard) Cauchy distribution**, $X \sim \mathcal{N}(\mu,\sigma^{2})$ ) p.d.f. $f_{X}(x)=\frac{1}{\pi (1+x^{2})}, F_{X}(x)=\arctan(x)+\frac{\pi}{2}$.

Rmk. (Heavy tail distribution without moment) Notice the $\text{I\kern-0.15em E}X=\int_{-\infty}^{\infty} |x| f_{X}(x) \ \mathrm{d}x=\infty$ does not exist.

# Ch2 
## 2.1 Covariance
1. $\sigma_{XY}= Cov[X,Y]=\text{I\kern-0.15em E}[ (X-\text{I\kern-0.15em E}X)(Y-\text{I\kern-0.15em E}Y) ]=\text{I\kern-0.15em E}(XY)-\mu_{X} \mu_{Y}$.
2. $V[\frac{X}{\sigma_{X}}]=1$, $\rho_{XY}=Cov[\tilde X,\tilde Y]=\frac{Cov[X,Y]}{\sigma_{X} \sigma_{Y}} \in [-1, 1]$.
3. The **covariance matrix** $V[\underline X]=\text{I\kern-0.15em E} [(\underline {X}-\underline {\mu}) (\underline {X}-\underline {\mu})^{T}]=\text{I\kern-0.15em E}  \underline {{X}} \underline {{X}}^{T}-\underline {\mu} \underline {\mu}^{T}$.
4. The **variance of r.v.** in the form of $\underline {a} \cdot \underline {X}$: $V[\underline {a} \cdot \underline {X}]=\underline {a}^{T} V[\underline {X}] \underline {a}$; $V[A \underline {X}]=A V[\underline {X}]A^{T}$. When $||\underline {a}||=1$, it's taking the variance in the direction of $\underline {a}$, over the joint p.d.f. (consider variance as the width of the function picture along certain axis).
## 2.2 
Prop. (**Independent normal**) $\sum_{i=1}^{n} c_{i} X_{i} \sim N(\sum c_{i} \mu_{i}, \sum c_{i}^{2} \sigma_{i}^{2})$.

Cor. When all Xi are from the same distribution, $\frac{1}{n} \sum  X_{i} \sim N(\mu, \frac{\sigma^{2}}{n})$.

Thm. (**CLT**) $\frac{1}{n} S_{n}:=\frac{1}{n} \sum_{i=1}^{n} X_{i} \sim N(\mu,\frac{\sigma^{2}}{n})$.

---



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




