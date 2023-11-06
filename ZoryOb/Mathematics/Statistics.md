---
link: https://zoryzhang.notion.site/Statistic-c2713936ee3c472184e31995e2642ca7
notionID: c2713936-ee3c-4721-84e3-1995e2642ca7
---

>  The note of UIUC course STAT 400 in Fall 2023, by Zory Zhang. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (maybe not up-to-date) can be found [here](Statistics.pdf).

For robust statistics, see [the page](Robust%20Statistics.md).
# Reminder
- The two properties of variance can save a lot of work.

# Preliminaries
The following content is based on the course STAT400@UIUC. [Probability knowledge](./Probability.md) is assumed.

# Textbook
_Probability and Statistical Inference_, Tenth Edition; by Robert V. Hogg, Elliot A. Tanis, Dale L. Zimmerman; Hoboken, NJ: Pearson; 2020.

# Ch0 Matrix cookbook
- [The matrix cookbook](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)
- $a$ for scalar, $\underline a$ for vector, $A$ for matrix.
- $X$ for random variable, $\underline X$ for random vector, $\textbf X$ for random matrix.
- $\text{I\kern-0.15em E}[\underline a^{T}  \underline {{X}}]=\underline a \cdot \text{I\kern-0.15em E}  \underline {{X}}$; $\text{I\kern-0.15em E}[A\underline {{X}}]=A \text{I\kern-0.15em E}\underline {{X}}$; $\text{I\kern-0.15em E}A\textbf{X}B=A \text{I\kern-0.15em E}  [\textbf{X}]B$.
- $\underline \mu:=\text{I\kern-0.15em E}\underline {X}, \underline v:=\text{I\kern-0.15em E} \underline {Y}$.

# Ch1 Probability
## 1.1 Discrete distributions
> Def. (**Bernoulli distribution**, $X \sim Be(p)$ ) Bernoulli trial is that $A \in \mathcal{F}$, and we call the trial a success if $A$ occurs. Bernoulli distribution is based on single Bernoulli trial. $m_{1}=m_{2}=p, Var=p(1-p)$.

> Def. (**Binomial distribution**, $Y \sim Bin(n,p)$ ) Perform n independent Bernoulli trials with $p=\text{I\kern-0.15em P}(A)$, and let Bernoulli r.v.s. $X_{1}, X_{2} \dots X_{n}$ be the indicator funciton of success of the experiments. Let $Y:=\sum X_{i}$, then the p.m.f. $f_{Y}(k)={n \choose k} p^{k} (1-p)^{n-k},k=1, 2, \dots, n$. **Binomial process** is that $Y_n$ to be the number of successes in the first n $Be(p)$ trials.

> Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$, $F(x)=1-(1-p)^{x}$.

> Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose k-r} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$

> Def. (**Approximate poisson process** with param $\lambda>0$) Let the number of **occurrences** of some event in a given **continuous interval** be counted. If
> 1. The number of occurrences in nonoverlapping subintervals are independent.
> 2. The probability of exactly one occurence in a sufficiently short subinterval of length h is approximately $\lambda h$.
> 3. The probability of more than one occurence in a sufficiently short subinterval of length is essentially 0.

> Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) An approximation of number of occurances in an interval of length 1 is given. Consider partition the unit interval into n subintervals. As n becomes larger, the length of subinterval become smaller and thus more likely the last two properties hold. For a large n, $\text{I\kern-0.15em P}(X=k) \sim {n \choose k} (\frac{\lambda}{n})^{k} (1-\frac{\lambda}{n})^{n-k}$, and it converges to $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=0,1, 2, \dots$

Rmk. $M(t)=e^{\lambda(e^{t}-1)}$, then $\mu = \sigma^{2}=\lambda$.

E.g. Number of customers of a shop between 5-6pm.

> Def. (**Hypergeometric distribution**) $f_{X}(k)=\frac{ {K \choose k} {N-K \choose n-k} }{ N \choose n }$. $\text{I\kern-0.15em E} X=n N_{1}/N$, $Var X=n \frac{N_{1}}{N}\frac{N-K}{N}\frac{N-n}{N-1}$. The sample 

> Def. (**Multinomial**) Multi-outcome version of hypergeometric. $f_{X}(x)=\frac{n!}{ \prod x_{i}!} \prod p_{i}^{x_{i}}$, where $\text{I\kern-0.15em E} X_{i}=np_{i}, VarX_{i}=np_{i}(1-p_{i})$.

## 1.2 Continuous distributions
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

## 1.3 Covariance
1. $\sigma_{XY}= Cov[X,Y]=\text{I\kern-0.15em E}[ (X-\text{I\kern-0.15em E}X)(Y-\text{I\kern-0.15em E}Y) ]=\text{I\kern-0.15em E}(XY)-\mu_{X} \mu_{Y}$.
2. $V[\frac{X}{\sigma_{X}}]=1$, $\rho_{XY}=Cov[\tilde X,\tilde Y]=\frac{Cov[X,Y]}{\sigma_{X} \sigma_{Y}} \in [-1, 1]$.
3. The **covariance matrix** $V[\underline X]=\text{I\kern-0.15em E} [(\underline {X}-\underline {\mu}) (\underline {X}-\underline {\mu})^{T}]=\text{I\kern-0.15em E}  \underline {{X}} \underline {{X}}^{T}-\underline {\mu} \underline {\mu}^{T}$.
4. The **variance of r.v.** in the form of $\underline {a} \cdot \underline {X}$: $V[\underline {a} \cdot \underline {X}]=\underline {a}^{T} V[\underline {X}] \underline {a}$; $V[A \underline {X}]=A V[\underline {X}]A^{T}$. When $||\underline {a}||=1$, it's taking the variance in the direction of $\underline {a}$, over the joint p.d.f. (consider variance as the width of the function picture along certain axis).
## 1.4 CLT
Prop. (**Independent normal**) $\sum_{i=1}^{n} c_{i} X_{i} \sim N(\sum c_{i} \mu_{i}, \sum c_{i}^{2} \sigma_{i}^{2})$.

Cor. When all Xi are from the same distribution, $\frac{1}{n} \sum  X_{i} \sim N(\mu, \frac{\sigma^{2}}{n})$.

Thm. (**CLT**) $\frac{1}{n} S_{n}:=\frac{1}{n} \sum_{i=1}^{n} X_{i} \sim N(\mu,\frac{\sigma^{2}}{n})$.

Rmk. Normal approximation work especially well on Binomial distribution when both $np, n(1-p)>5$.

Rmk. (**Continuity correlation**) When normal approximation is applied to interger sample space, we need to adjust the event space. E.g. $\text{I\kern-0.15em P}(3 \le X \le 5)=\text{I\kern-0.15em P}(2.5 \le X \le 5.5)$.

## 1.5 Generating function
> Def. (**k-th moments**) $m_{k}:=\text{I\kern-0.15em E} X^{k}=\int x^{k} f_{X}(x) \ \mathrm{d}x$.

Rmk. Third and forth moments are called skewness and kurtosis respectively.

![[Pasted image 20231013172632.png]]

Motivation. $G_{X}(s) = \text{I\kern-0.15em E} s^{X}, M_{X}(t)=\text{I\kern-0.15em E}e^{tX},\phi_{X}(t)=\text{I\kern-0.15em E}e^{itX}$. Then $X \perp Y$, we have $G_{X+Y}=G_{X}G_{Y}$. The converse may not be true.

Rmk. $\frac{\mathrm{d}^{k}}{\mathrm{d} t^{k}} M_{X}(t) |_{t=0}=\int x^{k} \ \mathrm{d} F_{X}(x)=m_{k}$.

# STAT

>Def. (**Sample mean, variance, and moment**) $n$ samples $X_{1}, \dots X_{n}$, $n$ observations $x_{1}, \dots x_{n}$. 
>1. The sample mean $\bar x:=\frac{1}{n} \sum_{i=1}^{n} x_{i}$;
>2. The sample variance $s^{2}:=\frac{1}{n-1} \sum_{i=1}^{n} (x_{i} - \bar x)^{2}$;
>3. The sample moment $\frac{1}{n} \sum_{i=1}^{n} x_{i}^{k}$.
>   
>These sample statistical quantities are contrast to population statistical quantities. Essentially, they are just random variables before observed.
## 2.1 Point estimation

> Def. (**Point estimation**) Given a dist with some known params and a unknown param $\theta$. The parameter space $\Omega$ is the range of all possible values of $\theta$. Now we need to find our best guess for $\theta$ to have a good estimate of dist. Let an **estimator** of $\theta$ be $\hat \theta:=u(X_{1}, X_{2}, \dots X_{n})$. The instance $u(x_{1}, x_{2}, \dots x_{n})$ is a **point estimate**.

Rmk. (**Maximum likelihood estimate, MLE**) For a **likelihood fun**c $L(\theta):=\prod_{i=1}^{n}f(x_{i};\theta)$, the MLE $\hat \theta:=\text{argmax}_{\theta} L(\theta)$.

> Def. (**Bias of estimator**) Estimator $\hat \theta$ has bias $\text{I\kern-0.15em E} \hat \theta-\theta$. E.g. $S_{X}^{2}$ is an **unbiased estimator** of the variances.

Rmk. (**Method of moments, MOM**) Let i-th sample moment equal to i-th theoretical moment, i from 1 to the # unknown params, then solve the equations.

> Def. (**Chi-squared distribution**) If k iid $Z_{i} \sim N(0,1)$, then $\sum_{i=1}^{k} Z_{i}^{2} \sim X^{2}(k) = Gamma(\alpha=k/2,\theta=2)$. $k$ is called the **degree of freedom**, DF.

Prop. $\frac{(n-1)S^{2}}{\sigma^{2}} \sim X^{2}(n-1)$.

Proof.
1. Assume 

## 2.2 Confidence Interval, CI
> Def. (**Student's t-distribution**) $T:=\frac{Z}{\sqrt {U / r} } \sim t_{r}$, where r is the DF,  $Z \sim N(0,1), U \sim X^{2}(r), Z \perp U$. Then $f_{T}(t)=\frac {\Gamma\left( \frac{r+1}{2} \right) }{\sqrt{\pi r} \Gamma(\frac{r}{2})(1+t^{2}/r)^{(r+1)/2}}$.

Rmk. $\text{I\kern-0.15em E} T=0, VarT=\frac{v}{v-2}$. When the sample size _n_ is relatively big, the difference between normal and t-distribution is small.

E.g. 
1. If the underlying distribution is normal, then  $Z=\frac{ \bar x - \mu }{ \sigma /\sqrt{n} } \sim N(0,1)  ;T=\frac{ \bar x - \mu }{ s/\sqrt{n}} \sim t_{n-1}$. #NotCovered 
2. The above can serve as approximation #NotCovered 
3. "When the distribution is not normal but is unimodal (has only one mode), symmetric, and continuous, the approximation is usually quite good even for small n, such as n = 5. ... In almost all cases encountered in real applications, an n of at least 30 is usually adequate."
4. Usually n being larger than 30 is good enough. But if the underlying distribution is badly skewed or contaminated with occasional outliers, most statisticians would prefer to have a larger sample size—say, 50 or more—and even that might not produce good results.

> Def. (**Confidence interval, CI**) A $100(1-\alpha)\%$ confidence interval is a range believed with probability $\alpha$ for failing to contain the parameter of interest. The answer format: we are $\alpha\%$ confident that the mean number of xxx is between xxx and xxx.

E.g. 
1. (**CI for $\mu$ when $\sigma$ is known**) Let $z_{\frac{\alpha}{2}}$ be the $100(1-\frac{\alpha}{2})$-percentile of $N(0,1)$, then an **approximate 2-sided** $100(1-\alpha)\%$ CI for $\mu$ when $\sigma$ is known is $\bar x \pm z_{\frac{\alpha}{2}} \frac \sigma {\sqrt{n}}$, derived from $Z=\frac{ \bar X - \mu }{ \sigma /\sqrt{n} } \sim N(0,1)$ approximately and thus $\text{I\kern-0.15em P}(-z_{\frac{\alpha}{2}} \le Z \le z_{\frac{\alpha}{2}} )\approx 1-\alpha$ . 
2. (**CI for $\mu$ when $\sigma$ is unknown but n is large**) use $s$ as the unbiased estimator of $\sigma$**, since $\frac{ \bar x - \mu }{ s/\sqrt{n}} \sim N(0,1)$. 
3. (**One sided CI**) Let $z_{\alpha}$ be the $100(1-\alpha)$-percentile of $N(0,1)$, then an approximate 1-sided CI for $\mu$ when $\sigma$ is known can be $(\bar x-z_{\alpha} \frac{\sigma}{\sqrt{n}}, \infty)$, from $\text{I\kern-0.15em P}( Z=\frac{ \bar X - \mu }{ \sigma /\sqrt{n} } \le z_{\alpha} )\approx 1-\alpha$ . 
4. (**CI for $\mu$ when $\sigma$ is unknown and n is small**) Let $t_{n-1, \frac{\alpha}{2}}$ be the $100(1-\frac{\alpha}{2})$-percentile of $t_{n-1}$, then when $\sigma$ is unknown (need estimation $s$), it is $\bar x \pm t_{n-1, \frac{\alpha}{2}} \frac{s}{\sqrt n}$, derived from $\text{I\kern-0.15em P}(-t_{\frac{\alpha}{2}} \le T=\frac{ \bar X - \mu }{ s /\sqrt{n} } \le t_{\frac{\alpha}{2}} )\approx 1-\alpha$ .
5. (**Sample size for target error when $\sigma$ is known or n is large**) The question is to find a sample size so that we have high confident that the mean is within $\bar X \pm \epsilon$. In other word, the CI is within $\bar X \pm \epsilon$, where $\epsilon$ is called the **maximum error of the estimate**. Then $\epsilon:=z_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt n}$. When we want to know what sample size n is needed for certain amount of error, we can solve n from that equation. 
6. (**Sample size for target error when $\sigma$ is unknown and n is small**) Note that $\text{I\kern-0.15em P}(\mu \in \bar X \pm t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )=1-\alpha$, and $\text{I\kern-0.15em E} (t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )^{2}=t_{n-1, \frac{\alpha}{2}} \frac{\sigma^{2}}{\sqrt n }$. Now if we hope $\text{I\kern-0.15em E} \epsilon^{2} := \text{I\kern-0.15em E} (t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )^{2}  \le \epsilon_{u}^{2}$, then we want $\frac{n}{t_{n-1, \frac{\alpha}{2}}^{2}} > \frac{s^{2}}{\epsilon_{u}^{2}}$. We can approximate it by conducting a preliminary experiment first to have sample variance, then get a sense of the n by using (5), and then improve the gap one observation at a time until it obeys the inequality.
7. (**CI for $\mu_{X}-\mu_{Y}$ when common $\sigma$ is unknown and n is small**) Suppose $X_{1}, \dots X_{n_{X}}$ and $Y_{1},\dots Y_{n_{Y}}$ independently from two normal $N(\mu_{X}, \sigma^{2}), N(\mu_{Y}, \sigma^{2})$. 
    - $Z:=\frac{\bar X - \bar Y - (\mu_{X}-\mu_{Y})}{\sqrt{ \frac{\sigma^{2}}{n_{X}} + \frac{\sigma^{2}}{n_{Y}} }} \sim N(0,1)$. 
    - OTAH, $U:=\frac{(n_{X}-1)S_{X}^{2}}{\sigma^{2}}+\frac{(n_{Y}-1)S_{Y}^{2}}{\sigma^{2}}$ is the sum of two independent chi-square r.v. thus $U \sim X^{2}(n_{X}+n_{Y}-2)$. 
    - The independence between the sample means and sample variances implies that $Z \perp U$. Thus $T:=\frac{Z}{\sqrt{\frac{U}{n_{X}+n_{Y}-2}}}\sim t_{n_{X}+n_{Y}-2}$ .
    - Then let $S_{p}:=\sqrt{ \frac{ (n_{X}-1)S_{X}^{2}+(n_{Y}-1)S_{Y}^{2} }{n_{X}+n_{Y}-2} }, t_{0}:=t_{n_{X}+n_{Y}-2, \alpha/2}$, we have the CI: $\bar X-\bar Y \pm t_{0} S_{p} \sqrt{ \frac{1}{n_{X}}+\frac{1}{n_{Y}} }$.
8. (**CI for proportion** $p$) Treat proportion as event success with probability $p$. Assume independent $X_{1}, \dots X_{n} \sim Bernoulli(p)$, unbiased MLE $\hat p=\frac{Y}{n}:= \frac{\sum X_{i}}{n}$, where $Y \sim Bin(n,p)$. 
    - By CLT, $\frac{\hat p - \text{I\kern-0.15em E} \hat p}{\sqrt{Var \hat p}}= \frac{\hat p - p}{ \sqrt{p(1-p)/n}} \sim N(0,1)$ approximately when n is large enough.
   $$\begin{aligned}&\text{I\kern-0.15em P}(-z_{\frac{\alpha}{2}} \le \frac{\hat p - p}{ \sqrt{\frac{p(1-p)}{n}}}  \le z_{\frac{\alpha}{2}} )=1-\alpha \\ \iff& \text{I\kern-0.15em P}\left(\frac{Y}{n}-z_{\frac{\alpha}{2}}\sqrt{\frac{p(1-p)}{n}}  \le p \le \frac{Y}{n}+z_{\frac{\alpha}{2}}\sqrt{\frac{p(1-p)}{n}}  \right)=1-\alpha\end{aligned}$$
    - Make additional approximation by replace $p$ in end points with $\hat p:=\frac{Y}{n}$.
6. (**CI for variance**) 
    





## 2.3 Hypothesis testing





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




