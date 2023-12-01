### Reminder
- p-value for 2-side: remember twice it.
- The two properties of variance can save a lot of work.
### Dist
%% > Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$, $F(x)=1-(1-p)^{x}$. 

 > Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose k-r} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$ 

 > Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) An approximation of number of occurances in an interval of length 1 is given. Consider partition the unit interval into n subintervals. As n becomes larger, the length of subinterval become smaller and thus more likely the last two properties hold. For a large n, $\text{I\kern-0.15em P}(X=k) \sim {n \choose k} (\frac{\lambda}{n})^{k} (1-\frac{\lambda}{n})^{n-k}$, and it converges to $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=0,1, 2, \dots$    

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

 > Def. (**Gamma function**) For $t>0$, $\Gamma(t)=\int_{0}^{\infty} y^{t-1}e^{-y} \ \mathrm{d} y$.

Rmk. $\Gamma(t)=(-y^{t-1}e^{-y})_{y=0}^{\infty} + \int_{0}^{\infty} (t-1) y^{t-2}e^{-y} \ \mathrm{d} y=(t-1) \Gamma(t-1)$. $\Gamma(1)=1$. When t is an integer, $\Gamma(t)=(t-1)!$.

> Def. (**Gamma distribution**, $X \sim Gamma(\alpha, \theta)$ ) For $x \ge 0$, $f_{X}(x)=\frac{1}{\Gamma(\alpha) \theta^{\alpha}} x^{\alpha-1}e^{-x/\theta}$. In a poisson process, the waiting time of first occurence is $Exp(\theta=1/\lambda)$, now gamma distribution describes the waiting time until $\alpha$-th occurrence.

> Def. (**Normal/Gaussian distribution**, $X \sim \mathcal{N}(\mu,\sigma^{2})$ ) $f_{X}(x)=\frac{1}{ \sqrt{2\pi} \sigma } \exp ( - \frac{(x-\mu)^{2}}{2 \sigma^{2}} )$. Standard normal distribution $Y \sim \mathcal{N}(0,1)$, denote the p.d.f. as $\phi(x)=\frac{1}{\sqrt{2\pi}} \exp(\frac{-x^{2}}{2})$. %%

> Def. (**Chi-squared distribution**) If k iid $Z_{i} \sim N(0,1)$, then $\sum_{i=1}^{k} Z_{i}^{2} \sim X^{2}_{(k)} = Gamma(\alpha=k/2,\theta=2)$. $k$ is called the **degree of freedom**, DF.

> Prop. $\frac{(n-1)S^{2}}{\sigma^{2}} \sim X^{2}_{(n-1)}$.

### CI
> Def. (**Student's t-distribution**) $T:=\frac{Z}{\sqrt {U / r} } \sim t_{r}$, where r is the DF,  $Z \sim N(0,1), U \sim X^{2}(r), Z \perp U$. Then $f_{T}(t)=\frac {\Gamma\left( \frac{r+1}{2} \right) }{\sqrt{\pi r} \Gamma(\frac{r}{2})(1+t^{2}/r)^{(r+1)/2}}$.

E.g. 
1. If the underlying distribution is normal, then  $Z=\frac{ \bar x - \mu }{ \sigma /\sqrt{n} } \sim N(0,1)  ;T=\frac{ \bar x - \mu }{ s/\sqrt{n}} \sim t_{n-1}$. #NotCovered 
2. The above can serve as approximation #NotCovered 
The answer format: we are $\alpha\%$ confident that the mean number of xxx is between xxx and xxx.

E.g. 
1. (**CI for $\mu$ when $\sigma$ is known**) Let $z_{\frac{\alpha}{2}}$ be the $100(1-\frac{\alpha}{2})$-percentile of $N(0,1)$, then an **approximate 2-sided** $100(1-\alpha)\%$ CI for $\mu$ when $\sigma$ is known is $\bar x \pm z_{\frac{\alpha}{2}} \frac \sigma {\sqrt{n}}$, derived from $Z=\frac{ \bar X - \mu }{ \sigma /\sqrt{n} } \sim N(0,1)$ approximately and thus $\text{I\kern-0.15em P}(-z_{\frac{\alpha}{2}} \le Z \le z_{\frac{\alpha}{2}} )\approx 1-\alpha$ . 
2. (**CI for $\mu$ when $\sigma$ is unknown but n is large**) use $s$ as the unbiased estimator of $\sigma$**, since $\frac{ \bar x - \mu }{ s/\sqrt{n}} \sim N(0,1)$. 
3. (**One sided CI**) Let $z_{\alpha}$ be the $100(1-\alpha)$-percentile of $N(0,1)$, then an approximate 1-sided CI for $\mu$ when $\sigma$ is known can be $(\bar x-z_{\alpha} \frac{\sigma}{\sqrt{n}}, \infty)$, from $\text{I\kern-0.15em P}( Z=\frac{ \bar X - \mu }{ \sigma /\sqrt{n} } \le z_{\alpha} )\approx 1-\alpha$ .
4. (**CI for $\mu$ when $\sigma$ is unknown and n is small**) Let $t_{n-1, \frac{\alpha}{2}}$ be the $100(1-\frac{\alpha}{2})$-percentile of $t_{n-1}$, then when $\sigma$ is unknown (need estimation $s$), it is $\bar x \pm t_{n-1, \frac{\alpha}{2}} \frac{s}{\sqrt n}$, derived from $\text{I\kern-0.15em P}(-t_{\frac{\alpha}{2}} \le T=\frac{ \bar X - \mu }{ s /\sqrt{n} } \le t_{\frac{\alpha}{2}} )\approx 1-\alpha$ .
5. (**Sample size for target error when $\sigma$ is known or n is large**) The question is to find a sample size so that we have high confident that the mean is within $\bar X \pm \epsilon$. In other word, the CI is within $\bar X \pm \epsilon$, where $\epsilon$ is called the **maximum error of the estimate**. Then $\epsilon:=z_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt n}$. When we want to know what sample size n is needed for certain amount of error, we can solve n from that equation. 
6. (**Sample size for target error when $\sigma$ is unknown and n is small**) Note that $\text{I\kern-0.15em P}(\mu \in \bar X \pm t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )=1-\alpha$, and $\text{I\kern-0.15em E} (t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )^{2}=t_{n-1, \frac{\alpha}{2}} \frac{\sigma^{2}}{\sqrt n }$. Now if we hope $\text{I\kern-0.15em E} \epsilon^{2} := \text{I\kern-0.15em E} (t_{n-1, \frac{\alpha}{2}} \frac{S}{\sqrt n } )^{2}  \le \epsilon_{u}^{2}$, then we want $\frac{n}{t_{n-1, \frac{\alpha}{2}}^{2}} > \frac{s^{2}}{\epsilon_{u}^{2}}$. We can approximate it by conducting a preliminary experiment first to have sample variance, then get a sense of the n by using (5), and then improve the gap one observation at a time until it obeys the inequality.
7. (**CI for $\mu_{X}-\mu_{Y}$ when $\sigma_{X}, \sigma_{Y}$ is known or n is large**) Suppose $X_{1}, \dots X_{n_{X}}$ and $Y_{1},\dots Y_{n_{Y}}$ independently from two normal $N(\mu_{X}, \sigma_{X}^{2}), N(\mu_{Y}, \sigma_{Y}^{2})$. $W:=X-Y, \sigma_{W}=\sqrt{ \frac{\sigma_{X}^{2}}{n_{X}} + \frac{\sigma_{Y}^{2}}{n_{Y}} }, Z:=\frac{\bar X - \bar Y - (\mu_{X}-\mu_{Y})}{\sigma_{W}} \sim N(0,1)$. 
8. (**CI for $\mu_{X}-\mu_{Y}$ when the common $\sigma$ is unknown and n is small**) Suppose $X_{1}, \dots X_{n_{X}}$ and $Y_{1},\dots Y_{n_{Y}}$ independently from two normal $N(\mu_{X}, \sigma^{2}), N(\mu_{Y}, \sigma^{2})$. 
    - $Z:=\frac{\bar X - \bar Y - (\mu_{X}-\mu_{Y})}{\sqrt{ \frac{\sigma^{2}}{n_{X}} + \frac{\sigma^{2}}{n_{Y}} }} \sim N(0,1)$. 
    - OTAH, $U:=\frac{(n_{X}-1)S_{X}^{2}}{\sigma^{2}}+\frac{(n_{Y}-1)S_{Y}^{2}}{\sigma^{2}}$ is the sum of two independent chi-square r.v. thus $U \sim X^{2}(n_{X}+n_{Y}-2)$. 
    - The independence between the sample means and sample variances implies that $Z \perp U$. Thus $T:=\frac{Z}{\sqrt{\frac{U}{n_{X}+n_{Y}-2}}}\sim t_{n_{X}+n_{Y}-2}$ .
    - Then let $S_{p}:=\sqrt{ \frac{ (n_{X}-1)S_{X}^{2}+(n_{Y}-1)S_{Y}^{2} }{n_{X}+n_{Y}-2} }, t_{0}:=t_{n_{X}+n_{Y}-2, \alpha/2}$, we have the CI: $\bar X-\bar Y \pm t_{0} S_{p} \sqrt{ \frac{1}{n_{X}}+\frac{1}{n_{Y}} }$.
9. (**CI for proportion** $p$) Treat proportion as event success with probability $p$. Assume independent $X_{1}, \dots X_{n} \sim Bernoulli(p)$, unbiased MLE $\hat p=\frac{Y}{n}:= \frac{\sum X_{i}}{n}$, where $Y \sim Bin(n,p)$. 
    - By CLT, $\frac{\hat p - \text{I\kern-0.15em E} \hat p}{\sqrt{Var \hat p}}= \frac{\hat p - p}{ \sqrt{p(1-p)/n}} \sim N(0,1)$ approximately when n is large enough. $$\begin{aligned}&\text{I\kern-0.15em P}(-z_{\frac{\alpha}{2}} \le \frac{\hat p - p}{ \sqrt{\frac{p(1-p)}{n}}}  \le z_{\frac{\alpha}{2}} )=1-\alpha \\ \iff& \text{I\kern-0.15em P}\left(\frac{Y}{n}-z_{\frac{\alpha}{2}}\sqrt{\frac{p(1-p)}{n}}  \le p \le \frac{Y}{n}+z_{\frac{\alpha}{2}}\sqrt{\frac{p(1-p)}{n}}  \right)=1-\alpha\end{aligned}$$
    - Make additional approximation by replace $p$ in end points with $\hat p:=\frac{Y}{n}$.
6. (**CI for variance**) $( \frac{(n-1)s^{2}}{X^{2}_{\frac{\alpha}{2}}} , \frac{(n-1)s^{2}}{X^{2}_{1-\frac{\alpha}{2}}} )$ .
### Hypothesis testing
- Test for **one mean** with known variance or large n:
    - $H_{0}: \mu=\mu_{0}$, test statistics $Z:=\frac{ \bar X - \mu_{0} }{ \sigma/\sqrt{n} } \sim N(0,1)$.
    - When $H_{1}: \mu \ne \mu_{0}$, the critical region $|z| \ge z_{\alpha/2}$ or $|\bar x - \mu_{0}| \ge z_{\frac{\alpha}{2}}\sigma / \sqrt{n}$.
    - When $H_{1}: \mu > \mu_{0}$, the critical region $z \ge z_{\alpha}$ or $\bar x - \mu_{0}\ge z_{\alpha}\sigma / \sqrt{n}$.
- Test for **one mean** with unknown variance and small n:
    - Simply adopt the t-distribution CI.
- Test for **one proportion**:
    - $H_{0}: p=p_{0}$, under which test statistics $Z:=\frac{ \frac{Y}{n} - p_{0} }{ \sqrt{p_{0} (1-p_{0}) /n } } \sim N(0,1)$, whose denominator is different from the CI. That one can also be used, yet produces approximately the same result.
    - When $H_{1}: \mu \ne \mu_{0}$, the critical region $|z| \ge z_{\alpha/2}$.
- Test for **equality of two means** with both dist approximately normal:
    - $Z:=\frac{\bar X - \bar Y - (\mu_{X}-\mu_{Y})}{\sqrt{ \frac{\sigma_{X}^{2}}{n_{X}} + \frac{\sigma_{Y}^{2}}{n_{Y}} }} \sim N(0,1)$. 
    - CI = $(\bar X - \bar Y) \pm z_\frac{\alpha}{2}\sqrt{ \frac{\sigma_{X}^{2}}{n_{X}}+\frac{\sigma_{Y}^{2}}{n_{Y}} }$.
- Test for **equality of two means** with unknown variance and n is small:
    - In general case, to use t distribution, we can use **conservative T**: $df=min(n_{1}, n_{2})-1$ or **Welch's T**: $df=\lfloor \frac{ (\frac{s_{X}^{2}}{n_{X}} + \frac{s_{Y}^{2}}{n_{Y}} )^{2} }{ \frac{1}{n_{X}-1} (\frac{s_{X}^{2}}{n_{X}})^{2} +  \frac{1}{n_{Y}-1} (\frac{s_{Y}^{2}}{n_{Y}})^{2} } \rfloor$.
    - **Pooled variance**: in the case that we assume $\sigma_{X}=\sigma_{Y}$, we can use $s_{pooled}$ as the estimator for both, where $s_{pooled}^{2}:=\frac{ (n_{X}-1)s_{X}^{2} + (n_{Y}-1)s_{Y}^{2} }{ n_{X} + n_{Y} -2 }$ and $df=n_{X}+n_{Y}-2$. This assumption is reasonable **if quotient between two sample standard deviation is at most 2**.
    - **Matched pairs**: if the data are paried, i.e. $D_{i}=X_{i}-Y_{i}$ are approximately random sample from normal. Then df=n-1, treat as one dist directly.
- Test for **two proportion**:
    - $Z:=\frac{ (\frac{Y_{1}}{n_{1}}-\frac{Y_{2}}{n_{2}})-(p_{1}-p_{2}) }{ \sqrt{ \frac{p_{1}(1-p_{1})}{n_{1}} + \frac{p_{2}(1-p_{2})}{n_{2}} } } \sim N(0,1)$.
    - To get test statistic under $H_{0}: p_{1}=p_{2}$, estimate $p_{1},p_{2}$ with $\hat p:=\frac{Y_{1}+Y_{2}}{n_{1}+n_{2}}$. $Z:=\frac{ (\frac{Y_{1}}{n_{1}}-\frac{Y_{2}}{n_{2}}) }{ \sqrt{ \hat p(1-\hat p) (\frac{1}{n_{1}}+ \frac{1}{n_{2}} ) } } \sim N(0,1)$.
- Test for **variance**:
    - $X^{2}=\frac{(n-1)S^{2}}{\sigma^{2}} \sim X^{2}_{(n-1)}$
    - $H_{0}: \sigma = \sigma_{0},H_{1}:\sigma < \sigma_{0}, C=\{ X^{2} < X^{2}_{n-1, 1-\alpha} \}$.









