>  The note of HKUST course MATH2431 Honors Probability, by Zory ZHANG.

# Ch1 Events
## 1.1 Space
Def. (**Sample space** $\Omega$) The set of all outcomes of an experiment.

Rmk. Set of all possible outcomes(elementary events)

Def. (**Event**) A subset of the sample space.

Def. (**Field** $\mathcal{F}$) A collection of subsets of $\Omega$ which satisfies
1. $\emptyset \in \mathcal{F}$
2. If $A \in \mathcal{F}$, then $\overline A \in \mathcal{F}$
3. If $A, B \in \mathcal{F}$, then $A \cup B \in \mathcal{F}$

Corollary. If $A, B \in \mathcal{F}$, then $A \cap B \in \mathcal{F}$; $\Omega \in \mathcal{F}$; **Field is closed under finite unions & intersections.**

Rmk. Field is a collection of events that are of interest.

Def. (**$\sigma$-Field** $\mathcal{F}$) A Field satisfies that (closed under countable unions & intersections)
$$A_{1}, A_{2}, \dots \in \mathcal{F} \implies \bigcup_{i=1}^ {\infty} A_{i} \in \mathcal{F}$$
E.g. The smallest $\sigma\text{-Field}=\{\emptyset, \Omega\}$, largest= $2^{\Omega}$ .

Rmk. With any experiment, we may associate a pair $(\Omega, \mathcal{F})$.

![[proba1.png]]

## 1.2 Assignment
Def. (**Measurable space**) A pair $(\Omega, \mathcal{F})$.

Def. (**General measure**) Given a measurable space $(\Omega, \mathcal{F})$, a measure $\mu$ is a set function $\mu: \mathcal{F} \to [0,  \infty]$, s.t. 
1. $\mu(\emptyset)=0$
2. (countable additivity) If $A_{1}, A_{2}, \dots$ is a collection of disjoint members of $\mathcal{F}$, i.e. $A_{i} \cap A_{j} = \emptyset$ for all $i \ne j$, then $\mu(\bigcup_{i=1}^ {\infty} A_{i})=\sum_{i=1}^ {\infty} \mu(A_{i})$.

Def. (**Measure space**) A triple $(\Omega, \mathcal{F}, \mu)$.

Def. (**Probability measure**) A function $\text{I\kern-0.15em P}: \mathcal{F} \to [0,1]$ satisfying
1. $\text{I\kern-0.15em P}(\emptyset)=0, \text{I\kern-0.15em P}(\Omega)=1$.
2. (countable additivity) If $A_{1}, A_{2}, \dots$ is a collection of **disjoint** members of $\mathcal{F}$, i.e. $A_{i} \cap A_{j} = \emptyset$ for all $i \ne j$, then $\text{I\kern-0.15em P}(\bigcup_{i=1}^ {\infty} A_{i})=\sum_{i=1}^ {\infty} \text{I\kern-0.15em P}(A_{i})$.

Ext. A measure $\mu$ is probability measure if $\mu(\Omega)=1$. Probability measure is a finite measure. Lebesgue measure is a $\sigma$-finite measure.

Def. (**Probability space**) A triple $(\Omega, \mathcal{F}, \text{I\kern-0.15em P})$.

Rmk. 
1. $\text{I\kern-0.15em P}(\overline A)=1-\text{I\kern-0.15em P}(A)$
2. If $B \supset A$, then $\text{I\kern-0.15em P}(B)=\text{I\kern-0.15em P}(A)+\text{I\kern-0.15em P}(B \setminus A) \ge \text{I\kern-0.15em P}(A)$, notice that $B \setminus A \in \mathcal{F}$
3. $\text{I\kern-0.15em P}(A \cup B)=\text{I\kern-0.15em P}(A)+\text{I\kern-0.15em P}(B)-\text{I\kern-0.15em P}(A \cap B)$
4. Inclusion-exclusion principle
5. $\text{I\kern-0.15em P}$ is a continuous set function

## 1.3 Continuity
Recall: 
1. $f$ is continuous at x if $\forall \{x_{n}\}, x_{n} \to x, n \to  \infty \Longrightarrow \lim_{n \to  \infty} f(x_{n})= f(\lim_{n\to\infty} x_{n} ) = f(x)$.
2. $\limsup_{n}x_{n}=\lim_{m \to  \infty} \sup_{n \ge m} x_{n}=\lim_{m \to  \infty} c_{m}$, where $c_m$ is monotonic, so that it must converge if we include $\pm \infty$.

Def. (**Set limit**) Given $A_{1}, A_{2}, \dots \in \mathcal{F}$, 
$$\limsup_{n \to  \infty}A_{n}:=\bigcap_{m=1}^{\infty} \bigcup_{n=m}^{ \infty} A_{n}=\bigcap_{m=1}^{\infty} B_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for infinitely many n}\}$$

Proof. Consider $\omega \in RHS$ or not. If yes, $\omega \in B_{m}, \forall m$; if not, disappear eventually.
$$\liminf_{n\to  \infty}A_{n}:=\bigcup_{m=1}^{  \infty} \bigcap_{n=m}^{ \infty} A_{n}=\bigcup_{m=1}^{\infty} C_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for all but finitely many n}\}$$

Proof. Consider $\omega \in RHS$ or not. If yes, appear eventually; otherwise fail.

Rmk. $\liminf A_{n} \subset \limsup A_{n}$, if equal, we say $A_{n}$ converges.

E.g. Monotonic set sequence converges (if including inf).

Def. (**Continuity of general measure**) $\mu$ is continuous if $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n)=\mu(A)$.
Rmk. Notice the closeness under union&intersection gives that $A:=\limsup_{n}A_{n} \in \mathcal{F}$.

Thm. (**Countable additivity implies continuity**)

Proof. For all convergent sequence $\{A_{n}\}$, which means

1. Case1: monotonic increasing An ($A_{n-1} \subset A_{n}$)
Recall countable additivity (\*), construct $D_{n}=A_{n} \setminus A_{n-1}$, then 

$$
\begin{aligned}
\mu(A)
&=\mu(\lim_{n \to  \infty} A_n)
:=\mu(\bigcup_{n=1}^ {\infty} \bigcap_{m=n}^ {\infty} A_{m}) \\
&=\mu(\bigcup_{n=1}^ {\infty} A_{n})
=\mu(\bigcup_{n=1}^ {\infty}D_{n})
\overset{(*)}{=} \sum_{n=1}^ {\infty} \mu(D_{n})\\
&=\lim_{n \to  \infty} \sum_{i=1}^{n} \mu(D_i)
=\lim_{n \to  \infty} \mu(\bigcup_{i=1}^{n} D_i)
=\lim_{n \to  \infty} \mu(A_n)
\end{aligned}
$$
2. Case2: monotonic decreasing An ($A_{n-1} \supset A_{n}$)
Construct $E_{n}=A_{n} \setminus A_{n+1}$, then 
$$
\begin{aligned}
\mu(A)
&=\mu(\lim_{n \to  \infty} A_n)
:=\mu(\bigcap_{n=1}^ {\infty} \bigcup_{m=n}^ {\infty} A_{m}) \\
&=\mu(\bigcup_{n=1}^ {\infty} A_{n})
=\mu(\bigcup_{n=1}^ {\infty}E_{n})
\overset{(*)}{=} \sum_{n=1}^ {\infty} \mu(E_{n})\\
&=\lim_{n \to  \infty} \sum_{i=1}^{n} \mu(E_i)
=\lim_{n \to  \infty} \mu(\bigcup_{i=1}^{n} E_i)
=\lim_{n \to  \infty} \mu(A_n)
\end{aligned}
$$

3. Case3: general An
Recall $B_{n}=\bigcup_{m=n}^{ \infty} A_{m}, C_{n}=\bigcap_{m=n}^{ \infty} A_m$.
Clearly $C_{n} \subset A_{n}\subset B_{n}$, and that $B_{n}$ is monotonic decreasing, $C_{n}$ is monotonic increasing.
From case1, we know that 

$$\begin{align*}
\limsup_{n \to  \infty} \mu(A_{n})
\le 
\lim_{n \to  \infty}\mu( B_{n})
=& \mu(\lim_{n \to  \infty} B_{n}) \\
=&\mu(B)
=\mu(A)
=\mu(C) \\
=&\mu(\lim_{n \to  \infty} C_{n})
=\lim_{n \to  \infty}\mu( C_{n})
\le \liminf_{n \to  \infty} \mu (A_{n})
\end{align*}
$$

However, $\limsup_{n \to  \infty} A_{n} \ge \liminf_{n \to  \infty} A_{n}$, 
therefore $\lim_{n \to  \infty} \mu(A_{n}) = \limsup_{n \to  \infty} \mu(A_{n}) = \liminf_{n \to  \infty} \mu(A_{n})=\mu(A)$.

Conclusion: $\mu$ is a continuous set function.

Prop. (**Finite additivity + continuity <=> countable additivity**)
Proof. (=>) 
Recall continuity: $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n)=\mu(A)$
and (countable additivity) If $A_{1}, A_{2}, \dots$ is a collection of disjoint members of $\mathcal{F}$, then 

$$
\mu(\bigcup_{i=1}^ {\infty} A_{i})
=\mu( \lim_{n \to  \infty} \bigcup_{i=1}^{n}A_{i}  )
= \lim_{n \to  \infty} \mu( \bigcup_{i=1}^{n}A_{i}  )
= \lim_{n \to  \infty} \sum_{i=1}^ {n} \mu(A_{i}  )
=\sum_{i=1}^ {\infty} \mu(A_{i})
$$

E.g. $\Omega= \mathbb{R}$, $\mathcal{F}$ is some $\sigma$-field including all intervals. If we know $\text{I\kern-0.15em P}([a,b])$ for all $[a,b] \subset \mathbb{R}$, then 
$$\lim_{n \to  \infty} \text{I\kern-0.15em P}([a+ \frac{1}{n}, b- \frac{1}{n} ])=\text{I\kern-0.15em P}(\lim_{n \to  \infty}  [a+ \frac{1}{n}, b- \frac{1}{n} ])=\text{I\kern-0.15em P}((a,b))$$, which uniquely extend all open intervals.

## 1.4 Conditional probability, independence
Rmk. "B has occurred" means $\omega \in B$. We may consider B as another sample space.

Def. (**Conditional probability**) If $\text{I\kern-0.15em P}(B)>0$, then $\text{I\kern-0.15em P}(A|B)= \frac{\text{I\kern-0.15em P}(A \cap B)}{\text{I\kern-0.15em P}(B)}$(pronounced as probability of A given B).

Lemma. (**Law of total probability**) Let $B_{1}, B_{2}, \dots, B_{n}$ be a partition of $\Omega$(disjoint $B_i$, $\cup B_i=\Omega$). If $\text{I\kern-0.15em P}(B_{i}) >0$, then $\text{I\kern-0.15em P}(A)=\sum_{i=1}^{n} \text{I\kern-0.15em P}(A|B_{i}) \text{I\kern-0.15em P}(B_{i})$.

Rmk. $\text{I\kern-0.15em P}(\cdot | B)=\mathbb{Q}(\cdot)$ is also a probability measure.

Cor. **Bayes' Theorm**

Def. (**Independence of events**) Let $A, B \in \mathcal{F}$, that $\text{I\kern-0.15em P}(A \cap B)=\text{I\kern-0.15em P}(A)\text{I\kern-0.15em P}(B)$, denoted as $A  \perp B$.

> Def. (**Mutually independence**) Let $\{A_{i}\}, A_{i} \in \mathcal{F}$, that $\text{I\kern-0.15em P}(\bigcap_{i \in J} A_{i}) = \prod_{i \in J} \text{I\kern-0.15em P}(A_{i}), \forall J \subset I$.

> Def. (**Pairwise independence**) Let $\{A_{i}\}, A_{i} \in \mathcal{F}$, that $\text{I\kern-0.15em P}(\bigcap_{i \in J} A_{i}) = \prod_{i \in J} \text{I\kern-0.15em P}(A_{i}), \forall J \subset I, |J|=2$.

Cor. If $A  \perp B$, then $A  \perp \overline B, \overline  A  \perp B, \overline A  \perp \overline B$.

Cor. If A, B, and C are mutually independent, then A is independent of whatever events formed from B and C.

> Def. (**Generated $\sigma$-field**) $\sigma(A)$ is the smallest $\sigma$-field generated by A, a collection of subset, by keeping taking countable union, intersection, or complement.

> vDef. (**Product space**) Given $(\Omega_1, \mathcal{F_1},  \text{I\kern-0.15em P} 1)$ and $(\Omega_{2}, \mathcal{F_{2}},  \text{I\kern-0.15em P}2)$, then their product space is $(\Omega, \mathcal{F},  \text{I\kern-0.15em P})$, where $\Omega=\Omega_{1} \times \Omega_{2}, \mathcal{F}= \sigma(\mathcal{F_{1}} \times \mathcal{F_{2}}),  \text{I\kern-0.15em P}$ is defined on $\Omega$ by $\text{I\kern-0.15em P}(A_{1}\times A_{2})= \text{I\kern-0.15em P}(A_{1})  \text{I\kern-0.15em P}(A_{2})$ and then continuity.

> Def. (**Independent trials**) If a combined experiment is modeled by the product space, the two sub-experiments are independent.

# Ch2 Random variable
## 2.1 "Preimage" viewpoint
Rmk. To answer the question that $\text{I\kern-0.15em P}(X \in B)=\text{I\kern-0.15em P}(\{\omega:X(\omega) \in B\})$, random variable acts as a "translation", where $\{\omega:X(\omega) \in B\}$ is the preimage $X^{-1}(B) \in \mathcal{F}$.

> Def. (**Random variable**) Given $(\Omega, \mathcal{F},  \text{I\kern-0.15em P})$, consider a function $X: \Omega \to \mathbb{R}$, s.t. $X^{-1}(B) \in \mathcal{F}, \forall \text{ intervals } B \subset \mathbb{R}$, called "X is $\mathcal{F}$-measurable"(\*).

Observ. 
1. Preimage can be interchanged with any set operation, e.g. $X^{-1}(B_{1} \cap B_{2})=X^{-1}(B_{1}) \cap X^{-1}(B_{2})$.
2. $\mathcal{F}$ is a $\sigma$-field: closed under taking countable intersections...

Rmk. Equivalently, holding on the following B will be sufficient instead of the condition (\*):
1. All open intervals
2. All closed intervals
3. All (a,b] intervals
4. All $(- \infty, x]$ intervals (simplest)

Prop. From Prop8.2 in Frederick Fong's book, if $\mu$ is $\mathcal{F}$-measurable, and $\varphi$ is continuous, then $\varphi(\mu)$ is also $\mathcal{F}$-measurable.

## 2.2 Borel Measure space
Rmk. Eventually, by taking countable set operations, we get a **Borel set**. The collection of them are a $\sigma$-field generated by all open intervals, called **Borel $\sigma$-field**, e.g. $(a,b) \in \mathcal{B}(\mathbb{R}), \mathbb{Q}\in \mathcal{B}(\mathbb{R}), \mathbb{R} \setminus \mathbb{Q} \in \mathcal{B}(\mathbb{R})$.

Rmk. Prefer to define by "open set" instead of "open interval", because the latter only works in $\mathbb{R}$.

Rmk. (level 2 understanding) $X: (\Omega, \mathcal{F}) \to (\mathbb{R}, \mathcal{B}(\mathbb{R}))$ is a measurable map, s.t. $X^{-1}(B) \in \mathcal{F}, \forall B \in \mathcal{B}(\mathbb{R})$.

## 2.3 Borel Probability space
Motiv. (level 3 understanding) Is there a probability measure Q, such that Q(B) can answer the question of $\text{I\kern-0.15em P}(X \in B)$? That is consider $X: (\Omega, \mathcal{F}, \text{I\kern-0.15em P}) \to (\mathbb{R}, \mathcal{B}(\mathbb{R}), Q)$.

Rmk. Define $Q(B):=\text{I\kern-0.15em P}(X^{-1}(B))$, or $Q=\text{I\kern-0.15em P} \circ X^{-1}$, and $Q$ is called the **pushforward measure, induced measure**, or **(cumulative) distribution function(c.d.f.)** of X.

Proof. (countable additivity) Notice that $X^{-1}(B_{n})=\{ \omega : X(\omega ) \in B_{n} \}$, and must be disjoint if $B_n$ disjoint, therefore $Q(\bigcup_{i=1}^ {\infty} B_{i})=\bigcup_{i=1}^ {\infty} \text{I\kern-0.15em P}(X^{-1}(B_{i}))=\sum_{i=1}^ {\infty} Q(B_{i})$.

## 2.4 Distribution function
Rmk. Because of the continuity, it's enough to know the **(cumulative) distribution function** $F_X(x):=\text{I\kern-0.15em P} \circ X^{-1}((- \infty, x]), \forall x$, given Caratheodory's extension theorem, to understand the prabability distribution of a random variable.

Prop. c.d.f is right continuous.

Proof. Given the monotonicity of $F_X$,

$$
\begin{aligned}
\lim_{h\to0^+} F_{X}(x+h)
&=\lim_{h\to0^+} \text{I\kern-0.15em P} \circ X^{-1}((- \infty, x+h])
=\text{I\kern-0.15em P} \circ X^{-1}(\lim_{h\to0^+} (- \infty, x+h]) 
\\\\ &=\text{I\kern-0.15em P} \circ X^{-1}(\lim_{n\to  \infty} (- \infty, x+ \frac 1 n ])
\\\\ &=\text{I\kern-0.15em P} \circ X^{-1}(\cap_{n=1}^{\infty} (- \infty, x+ \frac 1 n ])
\\\\ &=\text{I\kern-0.15em P} \circ X^{-1}((- \infty, x ])=F_{X}(x)
\end{aligned}
$$

In contrast, for $\lim_{h\to0^-} F_{X}(x+h)=\text{I\kern-0.15em P} \circ X^{-1}((- \infty, x))=F_X(x-)$.

> Def. (**Constant r.v.**) for some constant c, $\text{I\kern-0.15em P}(X=c)=\text{I\kern-0.15em P}(\omega \in \Omega: X(\omega)=c)=1$.

> Def. (**Bernoulli r.v.**) $A \in \mathcal{F}$, r.v. $I_{A}$ that $I_{A}(\omega)=[\omega\in A]$.

> Def. (**Discrete r.v.**) X takes values in some countable subset of $\mathbb{R}$, as a property of distribution func.

> Def. (**Probability mass func p.m.f.**) $f(x)=\text{I\kern-0.15em P} \circ X^{-1}(\{x\})=\text{I\kern-0.15em P}(X=x)=F_X(x)-F_X(x-)$.

> Def. (**(Absolutely) continuous r.v.**) c.d.f. $F_X(x)$ can be written as an integral of some Lebesgue integrable function $f:\mathbb{R} \to [0, \infty)$. $f$ is called **probability density function**(p.d.f.).


## 2.5 Random vector
> Def.1 (**Random vector**) Given $(\Omega, \mathcal{F},  \text{I\kern-0.15em P})$, consider a function $\vec X: \Omega \to \mathbb{R}^n$, s.t. $X^{-1}(D) \in \mathcal{F}, \forall D \in B(\mathbb{R}^n)$.

Rmk. We can replace all Borel sets by all "rectangles".

> Def.2 (**Random vector**) Given $(\Omega, \mathcal{F},  \text{I\kern-0.15em P})$, consider n random variables $X_i$, which means $X_{i}^{-1}(D_{i}) \in \mathcal{F}, \forall D_{i} \in B(\mathbb{R})$, to constitute $\vec X=[X_{1}, X_{2}, \dots, X_{n}]$.

> Def. (**Random function**) By new metric space -> open set -> Borel $\sigma$-field.

> Def. (**Joint distribution func**) $F_{X_{1}, X_{2}}(x_{1}, x_{2}) = \text{I\kern-0.15em P} \circ \vec X^{-1}((- \infty, x_{1}] \times (- \infty, x_{2}])$.

> Def. (**Marginal distribution func**) $F_{X}(x)=\lim_{y \uparrow  \infty} F_{X,Y}(x,y)$. 

Rmk. The marginal distribution of a subset of a collection of random variables is the probability distribution of the variables contained in the subset. It gives the probabilities of various values of the variables in the subset without reference to the values of the other variables.

> Def. (**Jointly (absolutely) continuous r.v.s.**) distribution func $F_{X,Y}(x,y)$ can be written as an double integral of some Lebesgue integrable functions $f:\mathbb{R^2} \to [0, \infty)$. $f$ is called **joint probability density function**.

Rmk. If $X=Y$, they're not jointly continuous.

## 2.6 Independence of r.v.s.
> Def. (**Independence of r.v.s.**) $X,Y:\Omega\to \mathbb{R}$ are independent($X  \perp Y$) if $\text{I\kern-0.15em P}(X \in E, Y \in F)=\text{I\kern-0.15em P}(X \in E) \text{I\kern-0.15em P}(Y \in F),\forall E,F \in B(\mathbb{R})$.

Rmk. The following two are also equivalent to the definition:
1. Holding on all half spaces is enough: $F_{X,Y}(x,y)=F_{X}(x)F_{Y}(y)$.
2. Holding on all single points is enough: p.m.f if discrete; otherwise p.d.f, i.e., $f_{X,Y}(x,y)=f_{X}(x)f_{Y}(y)$.

> Def. (**Mutually independence of r.v.s.**) $F_{X_{1},X_{2}, \dots, X_{n}}(x_{1}, x_{2}, \dots, x_{n})=F_{X_{1}}(x_{1})F_{X_{2}}(x_{2}) \dots F_{X_{n}}(x_{n})$. By choosing $x_i= \infty$, we have the freedom to restrict on all subsets of r.v.s, not only all of them.

Rmk. Independence of events is a special case of indepence of r.v., given that $A  \perp B \iff I_{A}  \perp I_{B}$.

Thm. If $X  \perp Y$, and two Borel measurable functions $g,h: \mathbb{R} \to \mathbb{R}$, then $g(X), h(Y)$ are still r.v.s., and that $g(X)  \perp h(Y)$.

Proof. By measure theory.

E.g. $\omega=(\omega_{1}, \omega_{2}), X_{1}(\omega) \equiv \tilde X_{1}(\omega_{1}), X_{2}(\omega) \equiv \tilde X_{2}(\omega_{2})$, where $X_{1}, X_{2}$ are defined on the product space, then $X_{1}  \perp X_{2}$.

# Ch3 Discrete world
## 3.1 Discrete distributions
> Def. (**Bernoulli distribution**, $X \sim Be(p)$ ) Bernoulli trial is that $A \in \mathcal{F}$, and we call the trial a success if $A$ occurs. Bernoulli distribution is based on single Bernoulli trial.

> Def. (**Binomial distribution**, $Y \sim Bin(n,p)$ ) Perform n independent Bernoulli trials with $p=\text{I\kern-0.15em P}(A)$, and let Bernoulli r.v.s. $X_{1}, X_{2} \dots X_{n}$ be the indicator funciton of success of the experiments. Let $Y:=\sum X_{i}$, then the p.m.f. $f_{Y}(k)={n \choose k} p^{k} (1-p)^{n-k},k=1, 2, \dots, n$. **Binomial process** is that $Y_n$ to be the number of successes in the first n $Be(p)$ trials.

> Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$

> Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose r-1} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$

> Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=1, 2, \dots$ The Poisson distribution is an approximation of a binomial distribution of a rare event in the case that n is large, p is small, and $\lambda=np$ is moderate.

## 3.2 Expectation of discrete r.v.
> Def. (**Expectation**) A discrete r.v. X taking values from ${x_{1}, x_{2}, \dots}$ with p.m.f. $f_{X}(x)$. The expectation $\text{I\kern-0.15em E}X:=\sum_{i} x_{i} f_{X}(x_{i})=\sum_{x:f_{X}(x)>0} xf_{X}(x)$ exists if the sum is absolutely convergent. The summation range is indicating the countability.

Rmk. Our best guess of X to minimize $(X-\text{I\kern-0.15em E}X)^{2}$.

Rmk. Absolutely convergence ensures the reorderability.

Lemma. (**Change of variable for Lebesgue integral**) $\text{I\kern-0.15em E}g(X)=\sum_{x:f_{X}(x)>0} g(x)f_{X}(x)$.

Lemma. (3.6.6) Let $X,Y$ be two r.v.s. jointly discrete, and $g(X,Y)$ is still a r.v, then $\text{I\kern-0.15em E}g(X,Y)=\sum_{x,y:f_{X,Y}(x,y)>0} g(x,y) f_{X,Y}(x,y)$.

Rmk. Expectation has finite linearity.

> Def. (**Uncorrelated**) $\text{I\kern-0.15em E}(XY)=\text{I\kern-0.15em E}(X)E(Y)$. Independence implies uncorrelation.

## 3.3 Variance of discrete r.v.
> Def. (**k-th moments**) $m_{k}:=\text{I\kern-0.15em E} X^k$.

> Def. (**k-th central moments**) $\sigma_{k}:=\text{I\kern-0.15em E} (X-\text{I\kern-0.15em E} X)^k$.

> Def. (**Variance**) 2-nd central moments $\sigma_{2}=m_{2}-m_{1}^{2}$, which describes the randomness of a r.v.

> Def. (**Covariance**) $Cov(X,Y)=\text{I\kern-0.15em E}[(X-\text{I\kern-0.15em E}X)(Y-\text{I\kern-0.15em E}Y)]=\text{I\kern-0.15em E}XY-\text{I\kern-0.15em E}X \cdot \text{I\kern-0.15em E} Y$.

Rmk. Properties of variance.
1. $Var(aX+b)=a^{2} Var X$
2. $VarX=Cov(X,X)$
3. $Var(X+Y)=Var X + Var Y+2Cov(X,Y)$

## 3.4 Conditional distribution & expectation
> Joint p.d.f is a symmetric viewpoint, here we try an asymmetric viewpoint.

> Def. (**Conditional distribution** of Y given event "X=x") To answer $\text{I\kern-0.15em P}(Y \in \cdot|X=x): B(\mathbb{R}) \to [0,1]$, define the c.m.f. $F_{Y|X}(\cdot|x):=\text{I\kern-0.15em P}(Y \le \cdot|X=x)$. The p.m.f $f_{Y|X}(\cdot|x)=\frac{ f_{X,Y}(x, \cdot) }{ f_{X}(x) }$, if $f_{X}(x)>0$.

> Def. (**Conditional expectation** of Y given event " $X=x:=\cdot$ ") $\psi_{Y|X}: \mathbb{R} \to \mathbb{R}$, $\psi_{Y|X}(\cdot):= \text{I\kern-0.15em E}(Y|X=\cdot):=\sum_{y} y f_{Y|X}(y|\cdot)$.

Rmk. Our best guess of Y to minimize $(Y-\text{I\kern-0.15em E}Y)^{2}$, after know that $X=x$.

> Def. (**Conditional expectation** of Y given a r.v. X) $\psi_{Y}: r.v. \to r.v.$, $\psi_{Y}(X):= \text{I\kern-0.15em E} (Y|X)=\sum_{x} \mathbb{1}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x)=\sum_{x} \mathbb{1}(X=x) \psi_{Y|X}(x)$.

Rmk. $\psi_{Y}(X)$ is from the same probability space as $X$, and it's our best guess of the "strategy" of Y to minimize $(Y-\text{I\kern-0.15em E}Y)^{2}$, after knowing the distribution of $X$.

> Def. (**Conditional expectation** of Y given a $\sigma$-field) skipped.


> Thm. (**Law of total expectation**) $\text{I\kern-0.15em E}\text{I\kern-0.15em E} (Y|X)=\text{I\kern-0.15em E} \psi_{Y}(X)=\sum_{x} \text{I\kern-0.15em P}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x)=\text{I\kern-0.15em E} Y$.

Rmk. $\text{I\kern-0.15em E}(\text{I\kern-0.15em E}(Y|X)g(X))=\text{I\kern-0.15em E}(Yg(X))$.

## 3.6 Sum of discrete r.v.s.
- (Convolution) If $X  \perp Y$, $f_{X+Y}(z)=\sum_{x}f_{X}(x)f_{Y}(z-x)$.

# Ch4 Continuous world
The probability at u is $f_{X}(u) \ \mathrm{d}u$.

## 4.1 Expectation of continuous r.v.
> Def. (**Expectation of continuous r.v.** X)  $\text{I\kern-0.15em E}X:=\int_{- \infty}^ {\infty} x f_{X}(x) \ \mathrm{d}x$. It exists if absolutely convergent.

Lemma. (**Tail probability**) $\text{I\kern-0.15em E} X=\int_{- \infty}^ {\infty} (1-F_{X}(x)) \ \mathrm{d}x=\int_{- \infty}^ {\infty} \text{I\kern-0.15em P}(X \ge x) \ \mathrm{d}x$.

Thm. (**Change of variable for Lebesgue integral**) Suppose X and g(X) are both continuous r.v., $g(X) \ge 0$, $\text{I\kern-0.15em E}g(X)=\int_{- \infty}^ {\infty} g(x) f_{X}(x)  \ \mathrm{d} x$.

Proof. 

$$
\begin{aligned}
\text{I\kern-0.15em E} g(X)
&=\int_{0}^{\infty} \text{I\kern-0.15em P}(g(X) >x) \ \mathrm{d}x
=\int_{0}^{\infty} \left[\int_{B:=\{y:g(y)>x\}} f_{X}(y) \ \mathrm{d} y \right] \ \mathrm{d} x,
\\
&=\int_{-\infty}^{\infty} \left[ \int_{0}^{g(y)} f_{X}(y) \ \mathrm{d} x \right] \ \mathrm{d}y
=\int_{-\infty}^{\infty} g(y) f_{X}(y) \ \mathrm{d}y
\end{aligned}
$$
## 4.2 Variance of continuous r.v.
> Def. (**k-th moments**) $m_{k}:=\text{I\kern-0.15em E} X^{k}=\int x^{k} f_{X}(x) \ \mathrm{d}x$.

> Def. (**k-th central moments**) $\sigma_{k}:=\text{I\kern-0.15em E} (X-\text{I\kern-0.15em E} X)^{k}=\int (x-\text{I\kern-0.15em E} X)^{k} f_{X}(x) \ \mathrm{d}x$.


## 4.3 Continuous distributions
> Def. (**Uniform distribution** $X \sim \mathcal{U}[0,1]$ ) $f_{X}(x)=1, F_{X}(x)=x$ over $[0,1]$, otherwise nature.

Thm. (**Inverse transform sampling**) Given a distribution function G, we can generate a r.v. Y with $F_{Y}=G$ by only generating a r.v. $U \sim \mathcal{U}[0,1]$.

Proof. We know G, as a distribution function, is non-decreasing and right continuous, with $G(x) \in [0,1]$.
1. Case 1: G is strictly increasing, and therefore invertible. Claim that $Y:=G^{-1}(U)$, then
   
$$
F_Y(x)=\text{I\kern-0.15em P}(Y \le x)=\text{I\kern-0.15em P}(G^{-1}(U) \le x)=\text{I\kern-0.15em P}(U \le G(x))=G(x)
$$

2. Case 2: otherwise,  what we really want of $G^{-1}$ is the property that $G^{-1}(z) \le x \iff z \le G(x)$. Consider to construct a generalized inverse function to satisfy this property. 
    Claim that $Y:=invG(U)$, where $invG(z):=\inf_{t \in \mathbb{R}} \{ G(t) \ge z \}=\inf H_{z}$. Due to right continuity and monotone, $invG(z) \in H_{z}$. To preserve the $F_{Y}=G$, we only need to verify the desired property. 

$$invG(z) \le x \iff \inf H_{z} \le x \iff  x \in H_{z} \iff G(x) \ge z$$

Rmk. It can help generate psuedo-random numbers following specific distribution given a uniformly distributed psuedo-random numbers generator.

> Def. (**Exponential distribution**, $X \sim Exp(\lambda)$ ) 

$$
F_{X}(x)= 
\begin{cases}
0, x<0 
\\\\ 1-e^{-\lambda x} ,x \ge 0 
\end{cases}
,f_{X}(x)= 
\begin{cases}
0, x<0  
\\\\ \lambda e^{-\lambda x} ,x \ge 0 
\end{cases}
$$

Rmk. 
1. X is the waiting time for the first success in a poisson process.
2. $\text{I\kern-0.15em E}X=\frac{1}{\lambda}$.
3. (Memoryless) $\text{I\kern-0.15em P}(X>s+t|X>t)=\text{I\kern-0.15em P}(X>s)$.
4. (Failture/hazard rate for positive r.v.) $r(t) = \lim_{h \downarrow 0} \frac{1}{h} \text{I\kern-0.15em P}(X \le t+h|X>t) = \frac{f(t)}{1-F(t)}=\lambda$.

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

> Def. (**(standard) Cauchy distribution**, $X \sim \mathcal{N}(\mu,\sigma^{2})$ ) p.d.f. $f_{X}(x)=\frac{1}{\pi (1+x^{2})}$.

Rmk. (Heavy tail distribution without moment) Notice the $\text{I\kern-0.15em E}X=\int_{-\infty}^{\infty} |x| f_{X}(x) \ \mathrm{d}x=\infty$ does not exist.

## 4.4 Dependence & joint distribution(symmetric)
Thm. (**Change of variable for Lebesgue integral**) $g: \mathbb{R^{2}} \to \mathbb{R}$ is Lebesgue integrable, then $\text{I\kern-0.15em E}g(X,Y)=\int_{- \infty}^ {\infty} \int_{- \infty}^ {\infty} g(x,y) f_{X,Y}(x,y)  \ \mathrm{d} x \ \mathrm{d}y$.

Rmk. By marginal distribution func, linearity of expectation can be proved.

> Def. (**Correlation coefficient**) $\frac{Cov(X,Y)}{\sqrt{Var X \cdot Var Y}}$, which is invariant under scaling.

> Def. (**Bivariate normal**) $f_{X,Y}(x,y)=\frac{1}{2\pi \sqrt{1-\rho^{2}}} \exp ( \frac{-1}{2(1-\rho^{2})} (x^{2}-2 \rho xy+y^{2}) )$.

Property. $X,Y$ are bivariate normal and uncorrelated, then they're independent.  Examples: [Wiki](https://en.wikipedia.org/wiki/Normally_distributed_and_uncorrelated_does_not_imply_independent) 

## 4.5 Conditional distribution(asymmetric)
> Def. (**Regular conditional dist**) If $f_{X}(x)>0$, $F_{Y|X}(y|x):= \text{I\kern-0.15em P}(Y \le y|X=x):=\int_{-\infty}^{y} \frac{f_{X,Y}(x,u)}{f_{X}(x)} \ \mathrm{d}u$; the cond. p.d.f $f_{Y|X}(\cdot|x)=\frac{ f_{X,Y}(x, \cdot) }{ f_{X}(x) }$.

Rmk. To compute $f_{X|Y}(x|y)=\frac{f_{X,Y}(x,y)}{f_{Y}(y)}=C_{y}g_{y}(x)$, we can view it as a p.d.f. of x given fixed y, because we know that $C_{y}=\frac{1}{\int g_{y}(x)}$, so we may ignore $f_{Y}(y)$, which is included in $C_{y}$.

E.g. For bivariate normal, $f_{X|Y}(x|y)$, given Y=y, $X \sim \mathcal{N}(\rho y,1-\rho^{2})$. When $\rho=0$, they're independent. In contrast, when $\rho \to 1$, $X \to Y$. In general, $X=\rho Y+\sqrt{1-\rho^{2}}Z$, where $Z \sim \mathcal{N}(0,1), Y \perp  Z$. Furthermore, 

$$
\begin{pmatrix}  
X \\\\  
Y
\end{pmatrix}
=
\begin{bmatrix}  
\rho & \sqrt{1-\rho^{2}} \\\\  
1 & 0 
\end{bmatrix}
\begin{pmatrix}  
Y \\\\  
Z
\end{pmatrix}
$$

> Def. (**Conditional expectation** of Y given event " $X=x:=\cdot$ ") $\psi_{Y|X}: \mathbb{R} \to \mathbb{R}$, $\psi_{Y|X}(\cdot):= \text{I\kern-0.15em E}(Y|X=\cdot):=\int y f_{Y|X}(y|\cdot) \ \mathrm{d}y$.
> Def. (**Conditional expectation** of Y given a r.v. X) $\psi_{Y}: r.v. \to r.v.$, $\psi_{Y}(X):= \text{I\kern-0.15em E} (Y|X)=\int \mathbb{1}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x) \ \mathrm{d}x=\int \mathbb{1}(X=x) \psi_{Y|X}(x) \ \mathrm{d}x$.
> Def. (**Conditional expectation** of Y given a $\sigma$-field) skipped.
> Thm. (**Law of total expectation**) $\text{I\kern-0.15em E}\text{I\kern-0.15em E} (Y|X)=\text{I\kern-0.15em E} \psi_{Y}(X)=\int \text{I\kern-0.15em P}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x) \ \mathrm{d}x=\text{I\kern-0.15em E} Y$. 
> Rmk. $\text{I\kern-0.15em E}(\text{I\kern-0.15em E}(Y|X)g(X))=\text{I\kern-0.15em E}(Yg(X))$.

## 4.6 Change of variable
$(U,V) \overset{g}{\to} (X,Y)$, where $g^{-1}$ exists. 
Furthermore, the Jacobian $J = \det \frac{\partial(x,y)}{\partial(u,v) }  =\det \begin{bmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\\\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v}\end{bmatrix} \ne 0$. 
Then $f_{X,Y}(x,y)=f_{U,V}(g^{-1}(x,y)) \frac{1}{\left| \det \frac{\partial(x,y)}{\partial(u,v) }\right| }$.

## 4.7 Sum of continuous r.v.s.

$$
\begin{aligned}
F_{X+Y}(z)
=&\text{I\kern-0.15em P}(X+Y \le z)
=\iint_{x+y\le z} f_{X,Y}(x,y) \ \mathrm{d}x \ \mathrm{d}y
\\\\  \overset{t=x+y}{=}& \iint_{t\le z} f_{X,Y}(x,t-x) \left| \det \frac{\partial(x,t)}{\partial(x,y) } \right|  \ \mathrm{d}x \ \mathrm{d}t
\\\\ =& \int_{-\infty}^{z}\left(\int  f_{X,Y}(x,t-x)  \ \mathrm{d}x\right)  \ \mathrm{d}t
\\\\ f_{X+Y}(z)
=& \int  f_{X,Y}(x,z-x)  \ \mathrm{d}x
\end{aligned}
$$

Eventually, convolution if independent.

Rmk. Sum of independent normal is still normal.


# Ch5 Generating function
Motivation. $G_{X}(s) = \text{I\kern-0.15em E} s^{X}, M_{X}(t)=\text{I\kern-0.15em E}e^{tX},\phi_{X}(t)=\text{I\kern-0.15em E}e^{itX}$. Then if $X \perp Y$, then $G_{X+Y}=G_{X}G_{Y}$.

> Def. (**Generating function**) $G_{a}(s)=\sum_{i=0}^{\infty} a_{i}s^{i}$, then $a_{i}=\frac{G_{a}^{(i)}(0)}{i!}$ if within the radius of convergence.

Rmk. (**Radius of convergence** R) Recall various convergence tests.
1. When $s \in (-R,R)$, $G_{a}(s)$ is absolutely convergent and can be differentiated or integrated term by term.
2. If $\exists R' \in (0,R], \forall s \in [-R',R'],G_{a}(s)=G_{b}(s)$, then $a_{i}=b_{i}, \forall i$.
3. If $R>0$ for $G_{a}(s)$, then $\{a_{n}\}$ is uniquely determined.

Thm. (**Abel's theorem**) If $G_{a}(s)$ has $R=1$, and $G_{a}(1)$ exists(divergent to positive infinity is included), then $G_{a}(s)$ is left continuous at $s=1$, i.e. $G_{a}(1)=\sum_{i=0}^{\infty}a_{i}=\lim_{s \uparrow 1} G_{a}(s)$.

## 5.1 Probability generating function
> Def. (**Probability generating function**) For nonnegative interger-valued discrete r.v.s. X, the p.g.f. $G_{X}(s)=\text{I\kern-0.15em E} s^{X}=\sum_{i=0}^{\infty} f_{X}(i) s^i$.

Rmk. $\sum_{i=0}^{\infty} f_{X}(i) s^{i} \le \sum_{i=0}^{\infty} s^i$, so $R \ge 1$.

# Ch6 Convergence



# Ch7 Limiting theorm