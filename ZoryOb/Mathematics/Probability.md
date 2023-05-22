>  The note of HKUST course MATH2431 Honors Probability in Spring 2023, by Zory ZHANG. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (may not up-to-date) can be found [here](probability.pdf).

# Reminder
- Expectation exists: absolutely convergence.

# Ch0 Notations
$A \setminus B$: the set difference/minus.
$A \triangle B$: the symmetric difference, $(A\setminus B) \cup (B\setminus A)$.

# Ch1 Events
## 1.1 Space
> Def. (**Sample space** $\Omega$) The set of all possible outcomes of an experiment(elementary events).

> Def. (**Event**) A subset of the sample space.

> Def. (**Field** $\mathcal{F}$) A collection of subsets of $\Omega$ which satisfies
>    1. $\emptyset \in \mathcal{F}$
>    2. If $A \in \mathcal{F}$, then $\overline A \in \mathcal{F}$
>    3. If $A, B \in \mathcal{F}$, then $A \cup B \in \mathcal{F}$

Corollary. If $A, B \in \mathcal{F}$, then $A \cap B \in \mathcal{F}$; $\Omega \in \mathcal{F}$; i.e. **Field is closed under finite unions & intersections.**

Rmk. Field is a collection of events that are of interest.

> Def. (**$\sigma$-Field** $\mathcal{F}$) A Field satisfies that (closed under countable unions & intersections)
> 
$$A_{1}, A_{2}, \dots \in \mathcal{F} \implies \bigcup_{i=1}^ {\infty} A_{i} \in \mathcal{F}$$

E.g. The smallest $\sigma\text{-Field}=\{\emptyset, \Omega\}$, largest= $2^{\Omega}$ .

Rmk. With any experiment, we may associate a pair $(\Omega, \mathcal{F})$.
> Def. (**Measurable space**) A pair $(\Omega, \mathcal{F})$.

![[proba1.png]]

## 1.2 Assignment
> Def. (**General measure**) Given a measurable space $(\Omega, \mathcal{F})$, a measure $\mu$ is a set function $\mu: \mathcal{F} \to [0,  \infty]$, s.t. 
> 1. $\mu(\emptyset)=0$
> 2. (**countable additivity**) If $A_{1}, A_{2}, \dots$ is a collection of **disjoint** members of $\mathcal{F}$, i.e. $A_{i} \cap A_{j} = \emptyset$ for all $i \ne j$, then $\mu(\bigcup_{i=1}^ {\infty} A_{i})=\sum_{i=1}^ {\infty} \mu(A_{i})$.

> Def. (**Measure space**) A triple $(\Omega, \mathcal{F}, \mu)$.

> Def. (**Probability measure**) A function $\text{I\kern-0.15em P}: \mathcal{F} \to [0,1]$ satisfying
> 1. $\text{I\kern-0.15em P}(\emptyset)=0, \text{I\kern-0.15em P}(\Omega)=1$.
> 2. (**countable additivity**) If $A_{1}, A_{2}, \dots$ is a collection of **disjoint** members of $\mathcal{F}$, i.e. $A_{i} \cap A_{j} = \emptyset$ for all $i \ne j$, then $\text{I\kern-0.15em P}(\bigcup_{i=1}^ {\infty} A_{i})=\sum_{i=1}^ {\infty} \text{I\kern-0.15em P}(A_{i})$.

Ext.
1. A measure $\mu$ is probability measure iff $\mu(\Omega)=1$. 
2. Probability measure is a finite measure.
3. Lebesgue measure is a $\sigma$-finite measure.

> Def. (**Probability space**) A triple $(\Omega, \mathcal{F}, \text{I\kern-0.15em P})$.

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

> Def. (**Set limit**) Given $A_{1}, A_{2}, \dots \in \mathcal{F}$, 
$$\limsup_{n \to  \infty}A_{n}:=\bigcap_{m=1}^{\infty} \bigcup_{n=m}^{ \infty} A_{n}=\bigcap_{m=1}^{\infty} B_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for infinitely many n}\}$$

Proof. 
Consider $\omega \in RHS$ or not. If yes, $\omega \in B_{m}, \forall m$; if not, disappear eventually.
$$\liminf_{n\to  \infty}A_{n}:=\bigcup_{m=1}^{  \infty} \bigcap_{n=m}^{ \infty} A_{n}=\bigcup_{m=1}^{\infty} C_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for all but finitely many n}\}$$

Proof. 
Consider $\omega \in RHS$ or not. If yes, appear eventually; otherwise fail.

Rmk. $\liminf A_{n} \subset \limsup A_{n}$; if equal, we say $A_{n}$ converges.

E.g. Monotonic set sequence converges (if including $\infty$).

> Def. (**Continuity of general measure**) $\mu$ is continuous if $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n)=\mu(A)$.

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
$$\lim_{n \to  \infty} \text{I\kern-0.15em P}([a+ \frac{1}{n}, b- \frac{1}{n} ])=\text{I\kern-0.15em P}(\lim_{n \to  \infty}  [a+ \frac{1}{n}, b- \frac{1}{n} ])=\text{I\kern-0.15em P}((a,b))$$, which uniquely extends all open intervals.

## 1.4 Conditional probability, independence
Rmk. "B has occurred" means $\omega \in B$. We may consider B as another adjusted sample space.

> Def. (**Conditional probability**) If $\text{I\kern-0.15em P}(B)>0$, then $\text{I\kern-0.15em P}(A|B)= \frac{\text{I\kern-0.15em P}(A \cap B)}{\text{I\kern-0.15em P}(B)}$(pronounced as probability of A given B).

Lemma. (**Law of total probability**) Let $B_{1}, B_{2}, \dots, B_{n}$ be a partition of $\Omega$(disjoint $B_i$, $\sqcup B_i=\Omega$) and $\text{I\kern-0.15em P}(B_{i}) >0$, then $\text{I\kern-0.15em P}(A)=\sum_{i=1}^{n} \text{I\kern-0.15em P}(A|B_{i}) \text{I\kern-0.15em P}(B_{i})$.

Rmk. $\text{I\kern-0.15em P}(\cdot | B)=\mathbb{Q}(\cdot)$ is also a probability measure, therefore B can be viewed as another adjusted sample space.

Cor. (**Bayes' Theorm**) Skipped.

> Def. (**Independence of events**) Let $A, B \in \mathcal{F}$, that $\text{I\kern-0.15em P}(A \cap B)=\text{I\kern-0.15em P}(A)\text{I\kern-0.15em P}(B)$, denoted as $A  \perp B$.

> Def. (**Mutually independence**) Let $\{A_{i}\}, A_{i} \in \mathcal{F}$, that $\text{I\kern-0.15em P}(\bigcap_{i \in J} A_{i}) = \prod_{i \in J} \text{I\kern-0.15em P}(A_{i}), \forall J \subset I$.

> Def. (**Pairwise independence**) Let $\{A_{i}\}, A_{i} \in \mathcal{F}$, that $\text{I\kern-0.15em P}(\bigcap_{i \in J} A_{i}) = \prod_{i \in J} \text{I\kern-0.15em P}(A_{i}), \forall J \subset I, |J|=2$.

Cor. If $A  \perp B$, then $A  \perp \overline B, \overline  A  \perp B, \overline A  \perp \overline B$.

Cor. If A, B, and C are mutually independent, then A is independent of whatever events formed from B and C.

> Def. (**Generated $\sigma$-field**) $\sigma(A)$ is the smallest $\sigma$-field generated by A, a collection of subset of $\Omega$, by keeping taking countable union, intersection, or complement.

> Def. (**Product space**) Given $(\Omega_1, \mathcal{F_1},  \text{I\kern-0.15em P} 1)$ and $(\Omega_{2}, \mathcal{F_{2}},  \text{I\kern-0.15em P}2)$, then their product space is $(\Omega, \mathcal{F},  \text{I\kern-0.15em P})$, where $\Omega=\Omega_{1} \times \Omega_{2}, \mathcal{F}= \sigma(\mathcal{F_{1}} \times \mathcal{F_{2}}),  \text{I\kern-0.15em P}$ is defined on $\Omega$ by $\text{I\kern-0.15em P}(A_{1}\times A_{2})= \text{I\kern-0.15em P}1(A_{1})  \text{I\kern-0.15em P}2(A_{2})$ and then continuity.

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

Rmk. Define $Q(B):=\text{I\kern-0.15em P}(X^{-1}(B))$, or $Q=\text{I\kern-0.15em P} \circ X^{-1}$, and $Q$ is called the **push forward measure, induced measure**, or **(cumulative) distribution function(c.d.f.)** of X.

Proof. (countable additivity) Notice that $X^{-1}(B_{n})=\{ \omega : X(\omega ) \in B_{n} \}$, and must be disjoint if $B_n$ disjoint, therefore $Q(\bigcup_{i=1}^ {\infty} B_{i})=\bigcup_{i=1}^ {\infty} \text{I\kern-0.15em P}(X^{-1}(B_{i}))=\sum_{i=1}^ {\infty} Q(B_{i})$.

## 2.4 Distribution function
Rmk. Because of the continuity, it's enough to know the **(cumulative) distribution function** $F_X(x):=\text{I\kern-0.15em P} \circ X^{-1}((- \infty, x]), \forall x$, given Caratheodory's extension theorem, to understand the prabability distribution of a random variable.

Prop. c.d.f is **right continuous**.

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

> Def. (**Bernoulli/indicator r.v.**) $A \in \mathcal{F}$, r.v. $\mathbb{1_A}$ that $\mathbb{1_A}(\omega)=[ \omega\in A ]$.


> Def. (**Discrete r.v.**) X takes values in some countable subset of $\mathbb{R}$, as a property of distribution func.
> 
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

> Def. (**Jointly (absolutely) continuous r.v.s.**) distribution func $F_{X,Y}(x,y)$ can be written as an Lebesgue double integral of some functions $f:\mathbb{R}^{2} \to [0, \infty)$. $f$ is called **joint probability density function**.

Rmk. (important) If $X=Y$, they're not jointly continuous, because $\iint f(x) \mathbb{1}(x=y) \ \mathrm{d}x \ \mathrm{d}y=\int f(x) \left[\int \mathbb{1}(x=y) \ \mathrm{d}y\right]\ \mathrm{d}x=0$.

## 2.6 Independence of r.v.s.
> Def. (**Independence of r.v.s.**) $X,Y:\Omega\to \mathbb{R}$ are independent($X  \perp Y$) if $\text{I\kern-0.15em P}(X \in E, Y \in F)=\text{I\kern-0.15em P}(X \in E) \text{I\kern-0.15em P}(Y \in F),\forall E,F \in B(\mathbb{R})$.

Rmk. The following two are also equivalent to the definition:
1. Holding on all half spaces is enough: $F_{X,Y}(x,y)=F_{X}(x)F_{Y}(y)$.
2. (important) Holding on all single points is enough: p.m.f if discrete; otherwise p.d.f, i.e., $f_{X,Y}(x,y)=f_{X}(x)f_{Y}(y)$.

> Def. (**Mutually independence of r.v.s.**) $F_{X_{1},X_{2}, \dots, X_{n}}(x_{1}, x_{2}, \dots, x_{n})=F_{X_{1}}(x_{1})F_{X_{2}}(x_{2}) \dots F_{X_{n}}(x_{n})$. By choosing $x_i= \infty$, we have the freedom to restrict on all subsets of r.v.s, not only all of them.

Rmk. Independence of events is a special case of indepence of r.v., given that $A  \perp B \iff I_{A}  \perp I_{B}$.

Thm. If $X  \perp Y$, and two Borel measurable functions $g,h: \mathbb{R} \to \mathbb{R}$, then $g(X), h(Y)$ are still r.v.s., and that $g(X)  \perp h(Y)$. Prove by measure theory.

E.g. $\omega=(\omega_{1}, \omega_{2}), X_{1}(\omega) \equiv \tilde X_{1}(\omega_{1}), X_{2}(\omega) \equiv \tilde X_{2}(\omega_{2})$, where $X_{1}, X_{2}$ are defined on the product space, then $X_{1}  \perp X_{2}$.

# Ch3 Discrete world
## 3.1 Discrete distributions
> Def. (**Bernoulli distribution**, $X \sim Be(p)$ ) Bernoulli trial is that $A \in \mathcal{F}$, and we call the trial a success if $A$ occurs. Bernoulli distribution is based on single Bernoulli trial.

> Def. (**Binomial distribution**, $Y \sim Bin(n,p)$ ) Perform n independent Bernoulli trials with $p=\text{I\kern-0.15em P}(A)$, and let Bernoulli r.v.s. $X_{1}, X_{2} \dots X_{n}$ be the indicator funciton of success of the experiments. Let $Y:=\sum X_{i}$, then the p.m.f. $f_{Y}(k)={n \choose k} p^{k} (1-p)^{n-k},k=1, 2, \dots, n$. **Binomial process** is that $Y_n$ to be the number of successes in the first n $Be(p)$ trials.

> Def. (**Geometric distribution**, $W \sim Geom(p)$ ) Keep performing Bernoulli trials until the first success, and let $W:=\text{the waiting time}$, then $f_{W}(k)=(1-p)^{k-1}p,k=1, 2, \dots$

> Def. (**Negative Binomial distribution**, $W_{r} \sim NB(r,p)$ ) Let $W_{r}:=\text{the waiting time for r successes}$, then $f_{W_{r}}(k)={k-1 \choose k-r} p^{r-1} (1-p)^{k-r}p ,k=1, 2, \dots$

> Def. (**Poisson distribution**, $X \sim poisson(\lambda)$ ) $f_{X}(k):= \frac{\lambda^{k}}{k!} e^{-\lambda}, k=1, 2, \dots$ The Poisson distribution is an approximation of a binomial distribution of a rare event in the case that **n is large, p is small**, and $\lambda=np$ is moderate.

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

> Def. (**$\sigma$-field induced by a r.v. X**) $\sigma(X):=\{X^{-1}(B):\forall B \in \mathcal{B}(\mathbb{R})\}$, which characterizes all information that can be obtained by observing the value of X.

E.g. For dice rolling, $X(\omega):=\mathbb{1}(\omega \text{ is odd})$, then $\sigma(X):=\{\emptyset, \Omega, \{1,3,5\}, \{2,4,6\}\}$.

Rmk. $\sigma(Y) \subset \sigma(\sigma(Y),\sigma(Z))$, here we use the above defined concept of generated $\sigma$-field. The meaning is that the information from both Y and Z is more than the information from Y.

> Def. (**Conditional expectation** of Y given a $\sigma$-field) skipped.

Rmk. (**Tower property**) Consider two $\sigma$-field $H_{1}\subset H_{2} \subset \mathcal{F}$, then $\text{I\kern-0.15em E}(\text{I\kern-0.15em E}(X|H_{1})|H_{2})=\text{I\kern-0.15em E}(\text{I\kern-0.15em E}(X|H_{2})|H_{1})=\text{I\kern-0.15em E}(X|H_{1})$. It's reasonable if we consider $\text{I\kern-0.15em E} (Y|X):=\psi_{Y}(X)$ as a function that maps a r.v. X to another r.v. in the same probability space. Then $\sigma(\psi_{Y}(X)) \subset \sigma(X)$ because there will at most no information lost during mapping.

> Thm. (**Law of total expectation**) $\text{I\kern-0.15em E}\text{I\kern-0.15em E} (Y|X)=\text{I\kern-0.15em E} \psi_{Y}(X)=\sum_{x} \text{I\kern-0.15em P}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x)=\text{I\kern-0.15em E} Y$.

Rmk. $\text{I\kern-0.15em E}(\text{I\kern-0.15em E}(Y|X)g(X))=\text{I\kern-0.15em E}(Yg(X))$.

## 3.6 Sum of discrete r.v.s.
- (Convolution) If $X  \perp Y$, $f_{X+Y}(z)=\sum_{x}f_{X}(x)f_{Y}(z-x)$.

# Ch4 Continuous world
$\text{I\kern-0.15em P}(u \le x \le u + \mathrm{d} u)=f_{X}(u) \ \mathrm{d}u$. 
More generally, borel set $B \in \mathbb{R}^{n},\text{I\kern-0.15em P} ( \vec X \in B )=\text{I\kern-0.15em P} \circ \vec X^{-1}(B) =\int_{B}  f_{X}(u) \ \mathrm{d}u$.

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

E.g. for normal distribution, $\sigma_i=\begin{cases} 0, \text{ if i odd}, \\  \sigma^{i}(i-1)!!, \text{ o.w.} \end{cases}$

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

> Def. (**(standard) Cauchy distribution**, $X \sim \mathcal{N}(\mu,\sigma^{2})$ ) p.d.f. $f_{X}(x)=\frac{1}{\pi (1+x^{2})}, F_{X}(x)=\arctan(x)+\frac{\pi}{2}$.

Rmk. (Heavy tail distribution without moment) Notice the $\text{I\kern-0.15em E}X=\int_{-\infty}^{\infty} |x| f_{X}(x) \ \mathrm{d}x=\infty$ does not exist.

## 4.4 Dependence & joint distribution(symmetric)
Thm. (**Change of variable for Lebesgue integral**) $g: \mathbb{R^{2}} \to \mathbb{R}$ is Lebesgue integrable, then $\text{I\kern-0.15em E}g(X,Y)=\int_{- \infty}^ {\infty} \int_{- \infty}^ {\infty} g(x,y) f_{X,Y}(x,y)  \ \mathrm{d} x \ \mathrm{d}y$.

Rmk. By marginal distribution func, linearity of expectation can be proved.

> Def. (**Correlation coefficient**) $\frac{Cov(X,Y)}{\sqrt{Var X \cdot Var Y}}$, which is invariant under scaling.

> Def. (**Bivariate normal**) $f_{X,Y}(x,y)=\frac{1}{2\pi \sqrt{1-\rho^{2}}} \exp ( \frac{-1}{2(1-\rho^{2})} (x^{2}-2 \rho xy+y^{2}) )$.

Property. $X,Y$ are bivariate normal and uncorrelated($\rho=0$), then they're independent. Examples: [Wiki](https://en.wikipedia.org/wiki/Normally_distributed_and_uncorrelated_does_not_imply_independent) 

## 4.5 Conditional distribution(asymmetric)
> Def. (**Regular conditional dist**) If $f_{X}(x)>0$, $F_{Y|X}(y|x):= \text{I\kern-0.15em P}(Y \le y|X=x):=\int_{-\infty}^{y} \frac{f_{X,Y}(x,u)}{f_{X}(x)} \ \mathrm{d}u$; the cond. p.d.f $f_{Y|X}(\cdot|x)=\frac{ f_{X,Y}(x, \cdot) }{ f_{X}(x) }$.

Rmk. To compute $f_{X|Y}(x|y)=\frac{f_{X,Y}(x,y)}{f_{Y}(y)}=C_{y}g_{y}(x)$, we can view it as a p.d.f. of x given fixed y, because we know that $C_{y}=\frac{1}{\int g_{y}(x)}$, so we may ignore $f_{Y}(y)$, which is included in $C_{y}$.

E.g. For bivariate normal, $f_{X|Y}(x|y)$, given Y=y, $X \sim \mathcal{N}(\rho y,1-\rho^{2})$. When $\rho=0$, they're independent. In contrast, when $\rho \to 1$, $X \to Y$. In general, $X=\rho Y+\sqrt{1-\rho^{2}}Z$, where $Z \sim \mathcal{N}(0,1), Y \perp  Z$. Furthermore, 

$$
\begin{pmatrix}  
X \\\\ Y
\end{pmatrix}
=\begin{bmatrix}  
\rho & \sqrt{1-\rho^{2}} \\
1 & 0 
\end{bmatrix}
\begin{pmatrix}  
Y \\\\ Z
\end{pmatrix}
$$

> Def. (**Conditional expectation** of Y given event " $X=x:=\cdot$ ") $\psi_{Y|X}: \mathbb{R} \to \mathbb{R}$, $\psi_{Y|X}(\cdot):= \text{I\kern-0.15em E}(Y|X=\cdot):=\int y f_{Y|X}(y|\cdot) \ \mathrm{d}y$.
> 
> Def. (**Conditional expectation** of Y given a r.v. X) $\psi_{Y}: r.v. \to r.v.$, $\psi_{Y}(X):= \text{I\kern-0.15em E} (Y|X)=\int \mathbb{1}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x) \ \mathrm{d}x=\int \mathbb{1}(X=x) \psi_{Y|X}(x) \ \mathrm{d}x$.
> 
> Def. (**Conditional expectation** of Y given a $\sigma$-field) skipped.
> 
> Thm. (**Law of total expectation**) $\text{I\kern-0.15em E}\text{I\kern-0.15em E} (Y|X)=\text{I\kern-0.15em E} \psi_{Y}(X)=\int \text{I\kern-0.15em P}(X=x) \cdot \text{I\kern-0.15em E}(Y|X=x) \ \mathrm{d}x=\text{I\kern-0.15em E} Y$. 
> 
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
Motivation. $G_{X}(s) = \text{I\kern-0.15em E} s^{X}, M_{X}(t)=\text{I\kern-0.15em E}e^{tX},\phi_{X}(t)=\text{I\kern-0.15em E}e^{itX}$. Then $X \perp Y$, we have $G_{X+Y}=G_{X}G_{Y}$. The converse may not be true.

> Def. (**Generating function**) $G_{a}(s)=\sum_{i=0}^{\infty} a_{i}s^{i}$, then $a_{i}=\frac{G_{a}^{(i)}(0)}{i!}$ if within the radius of convergence.

Rmk. (**Radius of convergence** R) Recall various convergence tests.
1. When $s \in (-R,R)$, $G_{a}(s)$ is absolutely convergent and can be differentiated or integrated term by term.
2. If $\exists R' \in (0,R], \forall s \in [-R',R'],G_{a}(s)=G_{b}(s)$, then $a_{i}=b_{i}, \forall i$.
3. If $R>0$ for $G_{a}(s)$, then $\{a_{n}\}$ is **uniquely determined** by taking derivative.

Thm. (**Abel's theorem**) If $a_i>0$, $G_{a}(s)$ has $R=1$, and $G_{a}(1)$ exists (diverging to positive infinity is included), then $G_{a}(s)$ is left continuous at $s=1$, i.e. $G_{a}(1):=\sum_{i=0}^{\infty}a_{i}=\lim_{s \uparrow 1} G_{a}(s)$.

## 5.1 Probability generating function
> Def. (**Probability generating function**) For nonnegative interger-valued discrete r.v. X, the p.g.f. $G_{X}(s)=\text{I\kern-0.15em E} s^{X}=\sum_{i=0}^{\infty} f_{X}(i) s^i$ is the g.f. of $a_{i}=f_{X}(i)$.

Rmk. 
1. $\sum_{i=0}^{\infty} f_{X}(i) s^{i} \le \sum_{i=0}^{\infty} s^i$, therefore $R \ge 1$.
2. $G_X(1)=\sum_{i} \text{I\kern-0.15em P}(X=i)=1-\text{I\kern-0.15em P}(X=\infty)$. If not 1, we say that X is **defective** with defective distribution func, and all moments equal $+\infty$.
3. $\text{I\kern-0.15em E}X=\lim_{s \uparrow 1} G_{X}'(s):=G_{X}'(1)$.
4. $\text{I\kern-0.15em E}X^{\underline k}:=\text{I\kern-0.15em E}[X(X-1)\dots (X-k+1)]=\lim_{s \uparrow 1} G_{X}^{(k)}(s):=G_{X}^{(k)}(1)$.
5. Limitation: hard to directly generate moment. E.g. $Var X = G''(1)+G'(1)-G'(1)^{2}$.

E.g.
1. $X \sim Be(p), G_{X}(s)=1-p+ps$.
2. $Y \sim Bin(n,p), G_Y(s)=G_{X}^{n}(s)$.
3. $W \sim Geom(p), G_{W}(s)=\frac{ps}{1-s(1-p)}$.
4. $X \sim poisson(\lambda), G_{X}(s)=e^{\lambda(s-1)}$.

Thm 5.1.1. (**Sum of a random number of i.i.d. r.v.s.**) N i.i.d. r.v. $X_{i}$ are independent of N, $T=\sum_{i=1}^{N} X_{i}$, then $G_{T}(s)=G_{N}(G_{X}(s))$. Prove by the law of total expectation.

E.g. The sum of a poisson number of i.i.d. Bernoulli r.v.s. is still poisson.

> Def. (**Joint probability generating function**) For nonnegative interger-valued discrete r.v.s. $X_{1},X_{2}$, the j.p.g.f. $G_{X,Y}(s,t)=\text{I\kern-0.15em E} s^{X} t^{Y}=\sum_{i=0}^{\infty} \sum_{j=0}^{\infty} f_{X,Y}(i,j) s^{i}t^{j}$.

Thm  5.1.2. $X \perp Y \iff G_{X,Y}(s,t)=G_{X}(s)G_{Y}(t)$. 

### 5.1.1 Application 1: Recurrence of random walk
Problem.
- $S_{0}=0,S_{n}=\sum_{i=1}^{n} X_{i}$, where $X_{i}$ are i.i.d. $Be(p)$ r.v.s. within $\{-1,1\}$.
- Define $T_{0}:=\min \{ i \ge 1:S_{i}=0 \}$. Notice that $T_{0}$ technically can be $\infty$, therefore it's a defective r.v. if $\text{I\kern-0.15em P}(T_{0}=\infty)>0$; 

Qes. The transience $\text{I\kern-0.15em P}(T_{0}=\infty)$; if none, the $\text{I\kern-0.15em E}T_{0}$.

Sol. 
1. $f_{T_{0}}(n):=\text{I\kern-0.15em P}(S_{1} \dots S_{n-1} \ne 0;S_{n} = 0)$, then $\text{I\kern-0.15em P}(T_{0}=\infty)=1-G_{T_{0}}(1)$. 
2. Consider $p_{0}(n)=\text{I\kern-0.15em P}(S_{n} = 0)=\mathbb{1}(\text{n is even}) {n \choose n/2} (pq)^{n/2}$, then $G_{p_{0}}(s)=(1-4pqs^{2})^{-1/2}$.
3. By law of total probability, that first return happens at the k-th step, then

$$
\begin{gather}
p_{0}(n)=\sum_{k=1}^{n} p_{0}(n-k) f_{T_{0}}(k) \\
\implies
G_{p_{0}}(s)=1+G_{p_{0}}(s) G_{T_{0}}(s)
\end{gather}
$$

4. $G_{T_{0}}(s)=1-(1-4pqs^{2})^{1/2}$, following (2) and (3).
5. $P(T_{0}=\infty)=|p-q|$. If $p=q=\frac{1}{2}$, then transience is none. In such case, $G_{T_{0}}(s)=1-(1-s^{2})^{1/2}$, and $\text{I\kern-0.15em E} T_{0}=G_{T_{0}}'(1)=+\infty$.

### 5.1.2 Application 2: Branching process (Galton-Watson tree)
Problem.
- Each member of the n-th generation gives birth to a family of members of the (n+1)-th generation.
- $Z_{0}=1,Z_{n+1}=X_{1}^{(n)}+X_{2}^{(n)}+\dots+X_{Z_{n}}^{(n)}$, where the branching r.v. X are i.i.d.
- Once $Z_{n}=0$, then $Z_{n+1}=0$. 
- $X_{i}^{(m)}$ is identical to $Z_{1}:=Z$.

Qes. What's the expectation and variance of $Z_{n}$?

Sol.
1. Denote $\mu:=\text{I\kern-0.15em E} Z=\mu, \sigma^{2}=Var Z$. 
2. p.g.f. $G_{n}=G_{1}(G_{n-1})=G(G_{n-1})$ by Thm 5.1.1.
3. $\text{I\kern-0.15em E} Z_{n}= \frac{\ \mathrm{d}}{\ \mathrm{d}s} G(G_{{n-1}}(s)) |_{s=1}=\mu \text{I\kern-0.15em E} Z_{n-1}$, i.e. $\text{I\kern-0.15em E} Z_{n}=\mu^n$.
4. $Var Z_{n}=\frac{\ \mathrm{d^{2}}}{\ \mathrm{d}s^{2}} G(G_{{n-1}}(s)) |_{s=1}+\frac{\ \mathrm{d}}{\ \mathrm{d}s} G_{{n}}(s)|_{s=1}-(\frac{\ \mathrm{d}}{\ \mathrm{d}s} G_{{n}}(s) |_{s=1})^{2}$.
5. If $\mu=1$, $Var Z_{n}=n \sigma^2$.
6. If $\mu \ne 1$, $Var Z_{n}=\frac{\sigma^{2} (\mu^{n}-1)\mu^{n-1} }{\mu-1}$.

Qes. Does the process eventually extinct?

Sol.
1. $\text{ \{ultimate extinction\} }=\bigcup_{n} \{Z_{n}=0\}=\lim_{n \to \infty} \{Z_{n}=0\}$, as an increasing sequence. Therefore $\text{I\kern-0.15em P}(\text{extinction})=\lim_{n \to \infty} \text{I\kern-0.15em P}(Z_{n}=0)=\lim_{n \to \infty} G_{{n}}(0)$. Let $\eta_{n}:=G_{{n}}(0) \to \eta:=\text{I\kern-0.15em P}(\text{extinction})$, then $\mu_{n}=G(\mu_{n-1})$.
2. Take limit, then $\eta=G(\eta)$ by continuity. Claim that $\eta$ is the smallest non-negative number that makes $s=G(s)$. Proof can be done by induction.
3. $G(s)$ is convex on $[0,1]$ because $G''(s):=\text{I\kern-0.15em E}(Z(Z-1)s^{Z-2})>0$ if $s \ge 0$.
4. When $\mu=1$, then $\eta=1$, i.e. must extinct given $\sigma>0$.
5. When $\mu<1$, then $\eta=1$, i.e. must extinct.
6. When $\mu>1$, then $\eta<1$.

## 5.2 Moment generating function
Limitation of p.g.f is that it only applys to nonnegative interger-valued discrete r.v.. We ask for a unified framework.

> Notation. (**Expectation for general r.v.**) $\text{I\kern-0.15em E}g(X)=\int g(x) \ \mathrm{d} F_{X}(x)=\int g(x) \text{I\kern-0.15em P} \circ X^{-1}(\mathrm{d}x)$.

E.g. $g(x)$ is the Dirichlet function.

Motivation. (**Lebesgue integral**) We ask for intervals such that function value in this interval is quite close. But we don't have to decompose the domain into intervals according to the natural ordering. Instead, we can decompose according to the function value using measure theory.

> Def. (**Moment generating function**) $M_{X}(t)=\text{I\kern-0.15em E}e^{tX}$.

Rmk. $\frac{\mathrm{d}^{k}}{\mathrm{d} t^{k}} M_{X}(t) |_{t=0}=\int x^{k} \ \mathrm{d} F_{X}(x)$. When k is even, we can directly claim existence.

## 5.3 Characteristic function
Motivation. We need to keep x on the exponential. But convergence of m.g.f. easily requires X to decay fast. The only left choice is to make the exponential complex. By Euler's formula, $e^{iy}=\cos y + i \sin y \implies \text{I\kern-0.15em E} e^{itx}=\text{I\kern-0.15em E}(\cos tX)+\text{I\kern-0.15em E}(\sin tX)$, therefore bounded. Essentially it becomes Fourier transform.

> Def. (**Characteristic function**) $\phi_{X}(t)=\text{I\kern-0.15em E}e^{itX}=\int e^{itx} \ \mathrm{d} F=\int (\cos tx + i \sin tx) \ \mathrm{d} F$. 
> (**Cumulants generating function**) $\log \phi_{X}(t)=\sum_{j} \frac{i^{j} c_{j}t^{j}}{j!}$.

Thm. (Bochner's thm) A function is a characteristic func of some r.v. iff (1), (2), (3) hold.
1. $\phi(0)=1,|\phi(t)|=|\int e^{itx} \ \mathrm{d} F| \le \int |e^{itx}| \ \mathrm{d} F \le \int \ \mathrm{d} F= 1$.
2. $\phi(t)$ is uniformly continuous. 
   $|\phi(t+h)-\phi(t)| \le \text{I\kern-0.15em E} |e^{itX}(e^{ihX}-1)| \le \text{I\kern-0.15em E} |e^{ihX}-1|$.
   Proved by dominated convergence thm.
3. $\phi$ is non-negative definite.

Thm. (c.f. can generate moments) $\phi^{(k)}(t)=\int (ix)^{k} e^{itx} \ \mathrm{d} F$. 
1. If $\phi^{(k)}(0)$ exists, which is $i^{k} \text{I\kern-0.15em E}X^{k}$, then $\text{I\kern-0.15em E} X^{\lfloor \frac{k}{2} \rfloor *2 }$ exists. 
2. If $\text{I\kern-0.15em E} X^{k}$ exists, then $\phi^{(k)}(0)$ exists. Then by Taylor expansion, $\phi(t)=\sum_{j=0}^{k} \phi^{(j)}(0)\frac{t^{j}}{j!}+o(t^{k})=\sum_{j=0}^{k} \text{I\kern-0.15em E}X^{j} \frac{ (it)^{j}}{j!}+o(t^{k})$.

Thm. $\forall s,t,\phi_{X,Y}(s,t)=\phi_{X}(s)\phi_{Y}(t) \iff X \perp Y$.

E.g.
- $X \sim Be(p)$, $\phi(t)=q+pe^{it}$.
- $X \sim Exp(\lambda)$, $\phi(t)=\frac{\lambda}{{\lambda-it}}$.
- $X \sim Cauchy$, $\phi(t)=e^{-|t|}$.
- $X \sim N(\mu,\sigma^2)$, $\phi(t)=\exp( i \mu t  -\frac{1}{2} \sigma^{2} t^{2})$.

Prop. Normal distribution is the only one whose cumulants expansion has finitely many non-zero terms: $\log \phi_{X}(t)=i \mu t -\frac{1}{2} \sigma^{2} t^{2}$.

### 5.3.1 Inversion thm
Thm. (**Fourier inversion thm**) At all points where f is differentiable, $f_{X}(x)=\frac{1}{2\pi} \int e^{-itx} \phi_{X}(t) \ \mathrm{d}t$. If the integral fails to converge absolutely, we interpret it as its principal value.

Thm. (**Inversion thm**)
$\bar F(x):=\frac{1}{2}(F(x)+F(x-))$. Notice that there's a one-to-one correspondence between $F, \bar F$. Then, 

$$
\bar F(b)-\bar F(a):=\lim_{N \to \infty} \int_{-N}^N \frac{e^{-ita}-e^{-itb}}{2\pi i t} \phi_{X}(t) \ \mathrm{d}t
$$

### 5.3.2 Lévy’s continuity theorem
Motiv. In certain sense, the function that maps probability measure on $\mathbb{R}$ to its c.f. (Fourier transform) is continuous and has a continuous inverse. Hence the convergence of probability measures can be checked with the aid of the c.f.

> Def. (**Convergence of distribution function sequence**) $F_{X_{n}} \to F_{X}$ if $F_{X_{n}}(x) \to F_{X}(x)$ at every point x where $F_{X}$ is continuous (*weak convergence*). We say  $X_{n}$ converges to $X$ in distribution/weakly/in law (denoted as $X_{n} \overset{D}{\to} X$ or $X_{n} \Rightarrow X$).

Motiv. We expect that $X_{n}(\omega)=\frac{1}{n}$ and $Y_{n}(\omega)=\frac{-1}{n}$ have the same limit. Therefore we drop the requirement at discontinuous points.

> Def. (**Vague convergence**) Given a set of d.f. $F_{n}$, if $F_{n}(x) \to G(x)$ at all continuous point of G, then $F_{n}$ converges to $G$ vaguely (because $G$ may be not a d.f.).

E.g. $X_{n}(\omega) \in \{\frac{1}{n},n\}$, G is not a d.f.

Rmk. Convergence in distribution is equivalent to convergence with respect to the Lévy metric.

Thm. (**Lévy’s continuity theorem**) 
1. If $F_{n} \to F$ vaguely and $F$ is a d.f. with c.f. $\phi$ , then $\phi_{n}\to \phi$ pointwise.
2. If $\phi_{n}\to \phi$ pointwise and the c.f. $\phi$ is continuous at 0 with d.f. $F$, then $F_{n} \to F$. 

Rmk. the statement "$\phi$ is continuous at 0" can be replaced by
1. $\phi$ is continuous (as a pointwise limit of c.f., 0 is the only point that can become discontinuous).
2. $\phi$ is a c.f. with d.f. $F$.
3. $\{ F_{n} \}_{n=0}^\infty$ is tight, i.e. the tail probability is uniformly bounded, $\forall \epsilon >0, \exists M_{\epsilon}>0, s.t. \sup_{n}[F_{n}(-M_{\epsilon})+(1-F_{n}(M_{\epsilon}))] \le \epsilon$.

E.g. $X_{n} \sim N(0,n^2)$, $\phi_{n}(t)=\exp(-\frac{1}{2} n^{2} t^{2})$.

### 5.3.3 Two limiting thm
###### Thm. 
n i.i.d. r.v. $X_n$ with $\mu:=\text{I\kern-0.15em E}X < \infty$: (Abuse of notation here)
1. (**Weak law of large number**, WLLN) $\frac{1}{n} \sum_{i=1}^{n} X_{i} \overset{D}{\to } \mu$.
2. (**Central limit thm**, CLT) Suppose $Var X_{1}=\sigma$, then $\sqrt n \left(\frac{1}{n} \sum_{i=1}^{n} X_{i} - \mu\right) \overset{D}{\to } N(0,\sigma^{2})$.
3. In other word, $\frac{1}{n} S_{n}:=\frac{1}{n} \sum_{i=1}^{n} X_{i} \sim N(\mu,\frac{\sigma^{2}}{n})$.

###### Proof: characteristics function
$$
\begin{aligned}
\phi_{X_{1}}(t)
&:=\text{I\kern-0.15em E} e^{itX_{1}}
=[k \le 1] \sum_{j=0}^{k} \text{I\kern-0.15em E} X_{1}^{j} \frac{(it)^{j}}{j!} +o(t^{k})
=1+i \mu  t+o(t)
\\
\phi_{n}(t)
&:= \text{I\kern-0.15em E} e^{it \frac{1}{n} S_{1}}
=(\text{I\kern-0.15em E} e^{it \frac{1}{n} X_{1}})^n
=\left(\phi_{X_{1}}\left(\frac{t}{n}\right)\right)^{n} \\
&=\left( 1+i \mu  \frac{t}{n}+o(\frac{t}{n}) \right)^{n}
\to e^{i t \mu}=\phi_{\mu}(t), \forall t
\end{aligned}
$$

$\phi_\mu$ is continuous at 0, by Lévy’s continuity theorem, $\frac{1}{n} \sum_{i=1}^{n} X_{i} \overset{D}{\to } \mu$. The same trick for Central limit thm.

###### Alternative proof of CLT: moment method
Say $\mu=0, \sigma=1, \text{I\kern-0.15em E}|X_{i}|^{k} <\infty$ for simplicity, then it becomes showing $Y_{n}:=\frac{1}{\sqrt n} \sum_{i=1}^{n} X_{i} \overset{D}{\to } N(0,1) \sim Y$.

Thm. (**Portmanteau thm**) Let $X_{1}, X_{2}, \dots$ be r.v.s. with d.f. $F_{1}, F_{2}, \dots$, then $X_{n} \overset{D}{\to} X$ iff $\forall \text{bounded continuous func } g:\mathbb{R} \to \mathbb{R}$, $\text{I\kern-0.15em E} g(X_{n}):= \int g(x)\ \mathrm{d} F_{n}(x) \to \int g(x)\ \mathrm{d} F_{X}(x):=\text{I\kern-0.15em E} g(X)$ as $n\to \infty$.

Rmk. It's sufficient to only check for all Lipschitz continuious functions.

Thm. (**Carleman's thm**) It's sufficient to only check for $\forall k \in \mathbb{N}, g_{k}(x):=x^{k}$ if given X satisfies $\sum_{k=1}^{\infty} (\int g_{2k}(x)\ \mathrm{d} F_{X}(x))^{-\frac{1}{2k}}=\infty$.

Alternative proof for CLT:
It's suffices to show $\forall k \in \mathbb{N},\text{I\kern-0.15em E} Y_{n}^{2k} \to  (2k-1)!!, \text{I\kern-0.15em E} Y_{n}^{2k+1}  \to 0$.
$$
\text{I\kern-0.15em E} Y_{n}^{p}=n^{ -\frac{p}{2}} \sum_{S \in 2^{[n]}} \text{I\kern-0.15em E} \left( \prod_{j=1}^{p} X_{S_{j}} \right) 
$$
Due to independence and $\text{I\kern-0.15em E}X_{j}=0$, this become a combinatorics problem. Some terms are negligible. Details are skipped.

###### Alternative proof of CLT: comparison method(Lindeberg swapping)
Say $\mu=0, \sigma=1, \text{I\kern-0.15em E}|X_{i}|^{3} \le C_{3} <\infty$ for simplicity, then it becomes showing  $Y_{n}:=\frac{1}{\sqrt n} \sum_{i=1}^{n} X_{i} \overset{D}{\to } N(0,1)$. 

Construct $g_{i} \sim N(0,1)$ as i.i.d., and let $Z_{n}:=\frac{1}{\sqrt n} \sum_{i=1}^{n} g_{i} \sim N(0,1)$.
It suffices to show $\forall t, F_{Y_{n}}(t)-F_{Z_{n}}(t) \to 0$ as $n \to \infty$.

$$
\begin{aligned}
&\forall t, F_{Y_{n}}(t)-F_{Z_{n}}(t) \to 0  \text{ as } n \to \infty \\

\Leftarrow &\forall t, \text{I\kern-0.15em E} \mathbb{1}(Y_{n}\le t)
-\text{I\kern-0.15em E} \mathbb{1}(Z_{n}\le t) \to 0  \text{ as } n \to \infty \\

\Leftarrow &\forall t, \phi_{t}(\cdot):=\mathbb{1}(\cdot \le t), \text{I\kern-0.15em E} \phi_{t}(Y_{n})-\phi_{t}(Z_{n}) \to 0  \text{ as } n \to \infty \\

\Leftarrow &\forall \text{bounded smooth func with bounded derivative } \phi, \\ & \text{I\kern-0.15em E} \phi(Y_{n})-\phi(Z_{n}) \to 0  \text{ as } n \to \infty
\end{aligned}
$$

Construct $H_{n,i}:=n^{-\frac{1}{2}}(g_{1}+g_{2} \dots g_{i} + X_{i+1}+\dots+X_{n})$, then $Y_{n}=H_{n,0}, Z_{n}=H_{n,n}$. Through this construction, we can bounded the difference between the two summations term by term. 

$$
\begin{align*}
& \text{I\kern-0.15em E} \phi(Y_{n})-\phi(Z_{n})\\
&= \text{I\kern-0.15em E} \phi(H_{n,0})-\text{I\kern-0.15em E} \phi(H_{n,n})\\
&= \sum_{i=0}^{n-1} \text{I\kern-0.15em E}\phi(H_{n,i})-\text{I\kern-0.15em E}\phi(H_{n,i+1}) \in o(1)\\
& \Leftarrow \forall n,i, \text{I\kern-0.15em E}\phi(H_{n,i})-\text{I\kern-0.15em E}\phi(H_{n,i+1}) \in o(\frac{1}{n})\\
\end{align*}
$$

Notice that the consecutive two terms $\phi(H_{n,i}), \phi(H_{n,i+1})$ only differ in the $i+1$-th entry. We can estimate by Tarlor expansion (with Lagrange remainder) w.r.t. this entry.

$$
\begin{aligned}
& H_{n,i}^{\circ}:=n^{-\frac{1}{2}}(g_{1}+g_{2} \dots g_{i} + 0+ X_{i+2}+\dots+X_{n})\\
& \phi(H_{n,i})
=\phi(H_{n,i}^{\circ})
+\phi'(H_{n,i}^{\circ})(\frac{X_{i+1}}{\sqrt{n}})
+\frac{1}{2} \phi''(H_{n,i}^{\circ})(\frac{X_{i+1}}{\sqrt{n}})^{2}
+\frac{1}{3!}\phi'''(t_{1})(\frac{X_{i+1}}{\sqrt{n}})^{3}\\
& \phi(H_{n,i+1})
=\phi(H_{n,i}^{\circ})
+\phi'(H_{n,i}^{\circ})(\frac{g_{i+1}}{\sqrt{n}})
+\frac{1}{2} \phi''(H_{n,i}^{\circ})(\frac{g_{i+1}}{\sqrt{n}})^{2}
+\frac{1}{3!}\phi'''(t_{2})(\frac{g_{i+1}}{\sqrt{n}})^{3}\\

& \text{I\kern-0.15em E}\phi(H_{n,i})-\text{I\kern-0.15em E}\phi(H_{n,i+1}) \le C_{3} \sup_{x \in \mathbb{R}} |\phi'''(x)| n^{-\frac{3}{2}} \in O\left(n^{-\frac{3}{2}}\right)\in o(\frac{1}{n})
\end{aligned}
$$

###### Alternative proof of CLT: Stein's method
A powerful method to show weak convergence to certain dist, especially Gaussian.

Prop. $X \sim N(0,1)$ iff $\forall f:\mathbb{R} \to \mathbb{R}$ continuously differentiable with bounded $f, f'$, $\text{I\kern-0.15em E}[f'(X)-Xf(X)]=0$.

Thm. (**Stein continuity thm**) $X_{n}$ is a sequence of real. r.v.s. with $\text{I\kern-0.15em E}|X_{i}|^{2} \le C_{2} <\infty$, then $X_{n}  \overset{D}{\to} N(0,1)$ iff $\forall f:\mathbb{R} \to \mathbb{R}$ continuously differentiable with bounded $f, f'$, $\text{I\kern-0.15em E}[f'(X_{n})-X_{n}f(X_{n})]\to 0  \text{ as } n \to \infty$.

Again, define $Y_{n}:=\frac{1}{\sqrt n} \sum_{i=1}^{n} X_{i}$. We assume $\text{I\kern-0.15em E}|Y_{i}|^{2} \le C_{2} <\infty$ required by the thm. Then, to show the convergence between $f$ and $f'$, we estimate by Tarlor expansion (with Lagrange remainder) again:

$$
\begin{aligned}
Y_{n}^{(j)}&:=\frac{1}{\sqrt n} \sum_{j \ne i} X_{i} \\

&\text{I\kern-0.15em E} Y_{n}f(Y_{n}) \\
=& \text{I\kern-0.15em E} \frac 1 {\sqrt{n}} \sum_{j} X_{j} f(Y_{n}) \\
=& \frac 1 {\sqrt{n}} \sum_{j} \text{I\kern-0.15em E}  X_{j} (\sum_{k=0}^\infty f^{(k)}(Y_{n}^{(j)})(\frac{X_{j}}{\sqrt{n}})^{k}) \\
\sim & \sum_{j} \sum_{k=0}^{\infty} n^{-\frac{k+1}{2}} \text{I\kern-0.15em E} f^{(k)}(Y_{n}^{(j)})X_{j}^{k+1} \\
= & \sum_{j} \sum_{k=0}^{\infty} n^{-\frac{k+1}{2}} \text{I\kern-0.15em E} f^{(k)}(Y_{n}^{(j)})\text{I\kern-0.15em E}X_{j}^{k+1}, \text{due the independence} \\
=& \sum_{j} \sum_{\text{odd }k} n^{-\frac{k+1}{2}} \text{I\kern-0.15em E} f^{(k)}(Y_{n}^{(j)})\text{I\kern-0.15em E}X_{j}^{k+1}, \text{ because odd order moment are 0} \\
=& \sum_{j} (n^{-1} \text{I\kern-0.15em E} f'(Y_{n}^{(j)})+O(n^{-3/2})) \\
=& O(n^{-1/2})+n^{-1} (\sum_{j} \text{I\kern-0.15em E} f'(Y_{n}^{(j)})-\text{I\kern-0.15em E} f'(Y_{n})+\sum_{j} \text{I\kern-0.15em E} f'(Y_{n})) \\
=& O(n^{-1/2})+\text{I\kern-0.15em E} f'(Y_{n}),\text{due to bounded }f' \\
\end{aligned}
$$

###### Thm: A general CLT
Motiv. When every error is so minor that doesn't dominate the total error.

Thm. Let $X_{1}, X_{2} \dots$ be independent; define $\sigma^{2}_{n}=Var(S_{n})=\sum_{j=1}^{n} \sigma_{j}^{2}$ with $\text{I\kern-0.15em E} X_{j}=0, Var X_{j}=\sigma_{j}^{2}, \text{I\kern-0.15em E} |X_{j}^{3}|<\infty$,  and such that 
$$
\frac{1}{\sigma_{n}^{3}}\sum_{j=1}^{n} \text{I\kern-0.15em E} |X_{j}^{3}| \to 0 \text{ as } n\to \infty 
$$
Then $\frac{1}{\sigma_{n}}S_{n} \overset{D}{\to} N(0,1)$. 

# Ch6 Markov
Skipped.

# Ch7 Convergence of r.v.
Convergence in distribution only reflects one aspect of r.v. It's reasonable to consider the nature of r.v.: a function from $[0,1]$ to $\mathbb{R}$.

Recall. Convergence of real functions $f_{n}, f: [0,1] \to \mathbb{R}$,
1. (**Pointwise convergence**) $\forall x, f_{n}(x) \to f(x)$ as $n \to \infty$. 
2. (**Convergence in norm**) $||f_{n} - f|| \to 0$ as $n \to \infty$. (bad point is not too bad in norm)
3. (**Convergence in measure $\mu$**) Bad point is not too much.
    - For $\epsilon>0, E_{\epsilon}=\{u\in[0,1]: |g(u)-h(u)| > \epsilon \}$, $d_{\epsilon}(g,h)=\mu(E_\epsilon):=\int_{E_{\epsilon}} \ \mathrm{d} \mu$.
    - $d_{\epsilon} (f_{n} , f) \to 0$ as $n \to \infty$ for all $\epsilon>0$.
    - Notice that proving on $\exists \delta>0, \forall \epsilon \in (0,\delta)$ will be sufficient.

Rmk. 
1. Convergence in $L_{p}$ norm is stronger than convergence in measure.
2. Convergence pointwise is stronger than convergence in measure.
3. The pointwise convergence and convergence in $L_{1}$ norm are not comparable.

---
## 7.1 Convergence mode of r.v.s.
We have introduced convergence in distribution, which is the only one that allows r.v.s. living in different probability spaces. Now let's go into the convergence of r.v.s. 

> Def. (**Almost sure convergence** $X_{n} \overset{a.s.}{\to} X$, $X_{n} \overset{a.e.}{\to} X$, or $X_{n} {\to} X$ w.p. 1) $X_{n}$ converges to $X$ almost surely, or almost everywhere, or with probability 1, when  $\text{I\kern-0.15em P}(\{ \omega \in \Omega: X_{n}(\omega) \to X(\omega) \text{ as } n \to \infty \})=1$.

> Def. (**Convergence in r-th mean** $X_{n} \overset{r}{\to} X$)  $\text{I\kern-0.15em E}|X_{n} - X |^{r} \to 0$ as $n \to \infty$. Note that $\text{I\kern-0.15em E}|Y|^{r}= \int_{\Omega} |y|^{r} \ \mathrm{d} F_{Y}$, and $(\text{I\kern-0.15em E}|Y|^{r})^{\frac{1}{r}}$ is $L_{r}$ norm. (Care about the degree of badness of bad events)

> Def. (**Convergence in probability (measure)** $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$)  $\exists \delta>0, \forall \epsilon \in (0,\delta)$, $\text{I\kern-0.15em P}(\{ \omega \in \Omega: |X_{n}(\omega) - X(\omega)| \ge \epsilon \}) \to 0$ as $n \to \infty$. (Care about the size of bad events)

Rmk. Almost sure convergence is an adoption of pointwise convergence, where the requirement of convergence over zero-probability events is drop.

Rmk. Convergence in probability is essentially using $d_{\epsilon}(g,h)=\int_\text{I\kern-0.15em E} \ \mathrm{d} \text{I\kern-0.15em P}(x)$ in the convergence in measure.

###### Thm. 7.1.1
Let $A_{n}(\epsilon):=\{\omega:|X_{n}(\omega)-X(\omega)| > \epsilon \}, B_{m}(\epsilon ):=\bigcup_{n \ge m} A_{n}(\epsilon)$. Here $\{B_{m}\}$ is decreasing, and therefore we denote by $A(\epsilon):=\lim_{m \to \infty} B_{m}(\epsilon)=\bigcap_{m=0}^{\infty} \bigcup_{n \ge m} A_{n}(\epsilon)=\limsup_{n} A_{n}(\epsilon)$, and denoted by $A(\epsilon):=\{A_{n}(\epsilon) \text{ i.o.}\}$, standing for infinitely often. Then the following hold:
1.  $X_{n} \overset{a.s.}{\to} X \iff \forall \epsilon>0, \text{I\kern-0.15em P}(A(\epsilon))=0$.
2. $X_{n} \overset{a.s.}{\to} X \Leftarrow \forall \epsilon>0, \sum_{n=1}^{\infty} \text{I\kern-0.15em P}(A_{n}(\epsilon)) < \infty$.

###### Proof.
Proof of 1.
Notice that $A(\epsilon)$ is decreasing as $\epsilon$ getting larger.
$$
\begin{aligned}
&\text{I\kern-0.15em P}(\{ \omega \in \Omega: X_{n}(\omega) \to X(\omega) \text{ as } n \to \infty \})=1 
\\ \iff &\text{I\kern-0.15em P}(\{ \omega \in \Omega: \forall \epsilon>0, \exists n_{0}, \forall n>n_{0,} |X_{n}(\omega)-X(\omega)| \le \epsilon\})=1
\\ \iff &\text{I\kern-0.15em P}(\{ \omega \in \Omega: \exists \epsilon_{0}>0, \forall n_{0}, \exists n>n_{0,} |X_{n}(\omega)-X(\omega)|>\epsilon_{0}\})=0
\\ \iff &\text{I\kern-0.15em P}( \cup_{\epsilon>0} \{ \omega \in \Omega: \forall n_{0}, \exists n>n_{0,} |X_{n}(\omega)-X(\omega)|>\epsilon\})=0
\\ \iff &\text{I\kern-0.15em P}( \cup_{\epsilon>0} \{ \omega \in \Omega: |X_{n}(\omega)-X(\omega)| > \epsilon \text{ for infinitely many n}\})=0
\\ \iff &\text{I\kern-0.15em P}( \cup_{\epsilon>0} \limsup_{n} A_{n}(\epsilon) )=0
\end{aligned}
$$
From left to right: notice that $\forall \epsilon>0, \text{I\kern-0.15em P}(\limsup_{n} A_{n}(\epsilon)) \le \text{I\kern-0.15em P}(\cup_{\epsilon>0} \limsup_{n} A_{n}(\epsilon))=0$. From right to left is obvious too.

Proof of 2.
$\text{I\kern-0.15em P}(B_{m}(\epsilon)) \le \sum_{n=m}^{\infty} \text{I\kern-0.15em P}(A_{n}(\epsilon))$, and the latter goes to 0 as m go to infinity.

###### Thm. 7.1.2
1. $X_{n} \overset{a.s.}{\to} X$ implies $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$.
2. $X_{n} \overset{r}{\to} X$ implies $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$.
3. $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$ implies $X_{n} \overset{D}{\to} X$.
4. $X_{n} \overset{r}{\to} X$ implies $X_{n} \overset{s}{\to} X$, if $r \ge s \ge 1$.
5. No other implication hold in general.

###### Proof of 5 (No other implication hold in general)
($X_{n} \overset{D}{\to} X$ doesn't imply $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$)
Trivial.

($X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$ doesn't imply $X_{n} \overset{r}{\to} X$)
Tiny bad point with very bad value. E.g. pick $X_{n}:=n^{3}$ with proba $n^{-2}$, otherwise 0.

($X_{n} \overset{\text{s}}{\to} X$ doesn't imply $X_{n} \overset{r}{\to} X$, if $r > s \ge 1$)
We want small s-th moment with large r-th moment. E.g. pick $X_{n}:=n$ with proba $n^{-\frac{1}{2}(r+s)}$, otherwise 0.

($X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$ doesn't imply $X_{n} \overset{a.s.}{\to} X$):
- $I_{i,j}:=[\frac{j}{i},\frac{j+1}{i}], I_n:=ordering_{n}(I_{i,j})=(I_{1,0},I_{2,0},I_{2,1},I_{3,0}, \dots)_{n}$.
- $X_{n}:=\mathbb{1}_{I_{n}}, X:=0$.
- Take $\delta=1$, $\text{I\kern-0.15em P}(\{ \omega \in \Omega: |X_{n}(\omega) - X(\omega)| \ge \epsilon \})=\text{I\kern-0.15em P}(I_{n}) \to 0$.
- For no $\omega$, $X_{n}(\omega) \to X(\omega) \text{ as } n \to \infty$, i.e. $\text{I\kern-0.15em P}=0$ instead.
- Intuition: a.s. convergence want to make sure many $\omega$ that can run away from bad events in a limiting sence.

($X_{n} \overset{r}{\to} X$ doesn't imply $X_{n} \overset{a.s.}{\to} X$) 
$X_{n}=\begin{cases} 1, w.p. n^{-1} \\ 0, w.p. 1-n^{-1} \end{cases}$

($X_{n} \overset{a.s.}{\to} X$ doesn't imply $X_{n} \overset{r}{\to} X$)
$X_{n}=\begin{cases} n^{3}, w.p. n^{-2} \\ 0, w.p. 1-n^{-2} \end{cases}$


###### Proof of 3
($X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$ implies $X_{n} \overset{D}{\to} X$)
$$
\begin{align*}
\forall \epsilon>0,
\text{I\kern-0.15em P}(X_{n} \le x)&=\text{I\kern-0.15em P}(X_{n} \le x, X \le x+\epsilon)+\text{I\kern-0.15em P}(X_{n} \le x, X > x+\epsilon) \\\\
&\le \text{I\kern-0.15em P}(X \le x+\epsilon)+\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon) \\\\

\text{I\kern-0.15em P}(X \le y)&=\text{I\kern-0.15em P}(X \le y, X_{n} \le y+\epsilon)+\text{I\kern-0.15em P}(X \le y, X_{n} > y+\epsilon) \\\\
&\le \text{I\kern-0.15em P}(X_{n} \le y+\epsilon)+\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon) \\\\
\text{Let } y=x-\epsilon& ,\\
\text{I\kern-0.15em P}(X \le x-\epsilon)-&\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon) 
\le \text{I\kern-0.15em P}(X_{n} \le x) 
 \le \text{I\kern-0.15em P}(X \le x+\epsilon)+\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon)\\

F_{X}(x-\epsilon)
-&\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon) 
\le F_n(x) 
\le F_{X}(x+\epsilon)
+\text{I\kern-0.15em P}(|X_{n}-X|>\epsilon)\\
n \to \infty &, F_{X}(x-\epsilon) \le \liminf_{n} F_n(x) \le \limsup_{n} F_n(x) \le F_{X}(x+\epsilon)
\end{align*}
$$

When $F_{x}$ is continuous at x, let $\epsilon \to 0$, we get $F_{n}(x) \to F_{X}(x)$ and concludes the proof.

###### Proof of 2
($X_{n} \overset{1}{\to} X$ implies $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$) 
Directly result from Markov's inequality.

$$
\begin{gather}
\text{Markov’s inequality } X \ge 0, \forall a>0, P(X \ge a) \le E(X)/a \\ \text{Chebyshev's inequality } \forall k>0, P(|X-\mu| \ge k \sigma) \le 1/k^2 
\end{gather}
$$
###### Proof of 4
($X_{n} \overset{r}{\to} X$ implies $X_{n} \overset{s}{\to} X$)
$$
\begin{gather}
\text{Lyapunov's inequality } (\text{I\kern-0.15em E} |Z|^{r})^{\frac{1}{r}} \ge (\text{I\kern-0.15em E} |Z|^{s})^{\frac{1}{s}}, r \ge s>0 \\
\text{Hölder's inequality } ||fg||_{1} \le ||f||_{p}||g||_{q}, \frac{1}{p}+\frac{1}{q}=1\\
\text{Jensen's inequality } \phi(\text{I\kern-0.15em E}X) \le \text{I\kern-0.15em E}(\phi(X)), \phi\text{ is convex}
\end{gather}
$$
In Hölder, let $X:=|Z|^{s}, Y=1, p=\frac{r}{s}, q=\frac{r}{r-s}$.
In Jensen, let $X:=|Z|^{s}, \phi(x)=x^{\frac{r}{s}}$.

###### Proof of 1
($X_{n} \overset{a.s.}{\to} X$ implies $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$) 
$X_{n} \overset{\text{I\kern-0.15em P}}{\to} X \iff \exists \delta>0, \forall 0<\epsilon<\delta, \text{I\kern-0.15em P}( A_{n}(\epsilon)) \to 0$ is true whenever $\text{I\kern-0.15em P}(B_{n}(\epsilon)) \to 0$ is true, which holds iff $X_{n} \overset{a.s.}{\to} X$ by Thm 7.1.1(1).

## 7.2 Partial converse statements
###### Thm.
1. If $X_{n} \overset{D}{\to} c$, where c is a constant, then $X_{n} \overset{\text{I\kern-0.15em P}}{\to} c$. 
2. If $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$, $\text{I\kern-0.15em P}(|X_{n}| \le k)=1$ for all n and some constant k, then $X_{n} \overset{r}{\to} X, r \ge 1$.
3. If $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$, there's a non-random subsequence such that $X_{n_{i}} \overset{a.s.}{\to} X$ as $i \to \infty$.
4. If $\forall \epsilon>0, \sum_{n} \text{I\kern-0.15em P}(|X_{n}-X| > \epsilon)<\infty$, then $X_{n}  \overset{a.s.}{\to} X$.

###### Proof of 1
(If $X_{n} \overset{D}{\to} c$, where c is a constant, then $X_{n} \overset{\text{I\kern-0.15em P}}{\to} c$)
Intuition from counter example: because no way to switch the $\omega$ if only one possible choice, i.e. $c$.

Application. to prove the law of large number, no need to prove the convergence in probability anymore.

###### Proof of 2
(If $X_{n} \overset{\text{I\kern-0.15em P}}{\to} X$, $\text{I\kern-0.15em P}(|X_{n}| \le k)=1$ for all n and some constant k, then $X_{n} \overset{r}{\to} X, r \ge 1$)

###### Proof of 3
#TODO 

###### Proof of 4
#TODO 

## 7.3 More applications of WLLN
###### Thm. (**Continuous mapping theorm**) 
Suppose function $g$ has the discontinuity points $D_{g}$ such that $\text{I\kern-0.15em P}(X \in D_{g})=0$, then:
$$
\begin{aligned}
X_{n} \overset{D}{\to} X \implies g(X_{n}) \overset{D}{\to} g(X) \\
X_{n} \overset{\text{I\kern-0.15em P}}{\to} X \implies g(X_{n}) \overset{\text{I\kern-0.15em P}}{\to} g(X) \\
X_{n} \overset{a.s.}{\to} X \implies g(X_{n}) \overset{a.s.}{\to} g(X)
\end{aligned}
$$

###### Application. 1 (Bernstein approximation)
Let $f$ be continuous on $[0,1]$ (i.e. uniform continuous and bounded). Define the Bernstein polynomial of degree n:
$$
f_{n}(x)=\sum_{m=0}^{n} {n \choose m} x^{m}(1-x)^{n-m} f(\frac{m}{n})
$$
Then $\sup_{x \in [0,1]} |f_{n}(x)-f(x)| \to 0$ as $n \to \infty$ (uniform convergence).

Proof. 
1. For $x \in [0,1]$, define $X_{x,i} \sim Be(x), S_{x,n}:=\sum_{i=1}^{n} X_{x,i} \sim Bin(n,x)$, then $f_{n}(x)=\text{I\kern-0.15em E} f(\frac{S_{x,n}}{n})$. Now we want to show $\text{I\kern-0.15em E} f\left(\frac{S_{x,n}}{n}\right) \rightrightarrows f(x)$. 
2. By WLLN and partial converse statement 1, $\frac{S_{x,n}}{n}=\frac{1}{n} \sum_{i=1}^{n} X_{i} \overset{\text{I\kern-0.15em P}}{\to } x$. By continuous mapping thm, we can get $f\left(\frac{S_{x,n}}{n}\right)  \overset{\text{I\kern-0.15em P}}{\to} f(x)$. But this's not used because such convergence depends on $x$.
3. We look back at the uniform continuity. $\forall \epsilon>0, \exists \delta:=\delta(\epsilon)>0, \forall x,n, |\frac{S_{x,n}}{n} - x|<\delta \implies |f(\frac{S_{x,n}}{n}) - f(x)|<\epsilon$.
4. Note that $\text{I\kern-0.15em E}\frac{S_{x,n}}{n}=x, Var(\frac{S_{x,n}}{n})=x(1-x)/n$, then:

$$
\begin{aligned}
&\forall \epsilon>0, \exists \delta:=\delta(\epsilon)>0, \forall x,n, \\
&\left|\text{I\kern-0.15em E}\left[ f\left(\frac{S_{x,n}}{n}\right)\right]-f(x)\right| \\

\le & \text{I\kern-0.15em E}\left| f\left(\frac{S_{x,n}}{n}\right)-f(x)\right| \\

= &\text{I\kern-0.15em E}\left| f\left(\frac{S_{x,n}}{n}\right)-f(x)\right|  \mathbb{1}(|\frac{S_{x,n}}{n}-x|<\delta)\\
&+\text{I\kern-0.15em E}\left| f\left(\frac{S_{x,n}}{n}\right)-f(x)\right|  \mathbb{1}(|\frac{S_{x,n}}{n}-x|\ge \delta) \\

\le & \epsilon \text{I\kern-0.15em E}\mathbb{1}(|\frac{S_{x,n}}{n}-x|<\delta) +2 \sup_{x}|f| \cdot \text{I\kern-0.15em E}\mathbb{1}(|\frac{S_{x,n}}{n}-x|\ge \delta)\\
= & \epsilon \text{I\kern-0.15em P}(|\frac{S_{x,n}}{n}-x|<\delta) +2 \sup_{x}|f| \cdot \text{I\kern-0.15em P}(|\frac{S_{x,n}}{n}-x|\ge \delta)\\
\le & \epsilon  +2 \sup_{x}|f| \cdot \frac{Var(\frac{S_{x,n}}{n})}{\delta^{2}}, \text{by Chebyshev ineq}\\
= & \epsilon+ 2 \sup_{x}|f| \cdot \frac{x(1-x)}{n\delta^{2}} \le \epsilon + \frac{\sup_{x}|f|}{2n\delta^{2}}
\end{aligned}
$$

5. $\forall \epsilon>0, \exists \delta:=\delta(\epsilon)>0,\forall n,\sup_{x} \left|f_{n}(x)-f(x)\right| \le \epsilon + \frac{\sup_{x}|f|}{2n\delta^{2}}$.
6. $\forall \epsilon>0, \exists \delta:=\delta(\epsilon)>0,\limsup_{n} \sup_{x} \left|f_{n}(x)-f(x)\right| \le \epsilon$.
7. $\lim_{n} \sup_{x} \left|f_{n}(x)-f(x)\right| \epsilon=0$.

###### Application 2. (Borel's geometric concentration) 
Let $\mu_{n}$ be the uniform probability measure on the n-dimentional cube $[-1,1]^{n}$. Let $H$ be a hyperplane that's orthogonal to a principal diagonal of $[-1,1]^{n}$, i.e. $H = (1,1, \dots, 1)^{\perp}$. Let $H_{r}=\{ x \in [-1,1]^{n}: dist(x,H) \le r \}$. Then $\forall \epsilon>0, \lim_{n \to \infty} \mu_{n}(H_{\epsilon \sqrt n}) = 1$.

Proof. 
$$
\begin{gather}
\mu_{n}(H_{\epsilon \sqrt n})
=\text{I\kern-0.15em P}(dist(\vec x,H) \le \epsilon\sqrt n ) \\
=\text{I\kern-0.15em P}\left( \frac{|<\vec x,(1,1,\dots,1)>|}{\sqrt n}\le \epsilon\sqrt n \right) 
=\text{I\kern-0.15em P}( \frac{|\sum x_{i}|}{n} \le \epsilon )
\end{gather}
$$
#TODO 

## 7.4 Other versions of WLLN
###### Thm. $L^2-WLLN$
Let $X_{1}, X_{2}, \dots$ be **uncorrelated** r.v.s. with $\forall i,\text{I\kern-0.15em E}X_{i}=\mu, Var X_{i} \le C < \infty$ Then $\frac{1}{n} \sum_{i=1}^{n} X_{i} \overset{2}{\to } \mu$.

Proof. By def, $\text{I\kern-0.15em E} (\frac{S_{n}}{n}-\mu)^{2}=Var(\frac{S_{n}}{n})=\frac{1}{n^{2}}\sum_{i=1}^{n} Var(X_{i}) \le \frac{C}{n}\to 0  \text{ as } n \to \infty$.

###### Thm. WLLN for triangular array
Thm. Let $\{ X_{n,i} \}$ be a triangular array, where in each level, $X_{n,i}$ are i.i.d. with $Var X_{i}=\sigma^{2}$. Let $S_n:=\sum_{i=1}^{n} X_{n,i}, \mu_{n}:=\text{I\kern-0.15em E}S_{n}=n \text{I\kern-0.15em E} X_{n,1}$. Suppose $\frac{Var(S_{n})}{b_{n}^{2}} \to 0$ for some real sequence chosen by ourselves (non-random) $\{b_{n}\}$, then $\frac{S_{n}-\mu_{n}}{b_{n}}  \overset{2}{\to} 0$.

E.g. $X_{n,i}:=\frac{Y_{i}}{n}$, then $S_{n}=\sum_{i=1}^{n} \frac{Y_{i}}{n}$.

Proof. $\text{I\kern-0.15em E} (\frac{S_{n}-\mu_{n}}{b_{n}}-0)^{2}=b_{n}^{-2} Var(S_{n}) \to 0  \text{ as } n \to \infty$.

Motiv. We use $b_{n}=n$ in the L2-WLLN, and eventually $\frac{C}{n}\to 0$ very fast. But we only need an $o(1)$ for it.

Rmk. We can try an extreme case inspired from CLT, where $b_{n}=n^{1/2+\epsilon}$. Then $\frac{S_{n}-n \text{I\kern-0.15em E}X_{n,1}}{n^{1/2+\epsilon}} \overset{\text{I\kern-0.15em P}}{\to} 0 \Rightarrow S_{n}=n \text{I\kern-0.15em E}X_{n,1}+o_{\text{I\kern-0.15em P}}(n^{1/2+\epsilon})$. The principle is that if possible, we shall not choose $b_{n} >> \mu_{n}=n \text{I\kern-0.15em E} X_{n,1}$, otherwise meaningless.

###### E.g.1 Coupon collection problem
$Y_{n,i}$: i.i.d. uniform on $\{1,2,\dots, n\}$. Let $\psi_{k}^{n}:=\inf_{m}\{ |\{Y_{n,1},Y_{n,2} \dots Y_{n,m}\}|=k \}$, $X_{n,k}:=\psi_{k}^{n}-\psi_{k-1}^{n} \sim Geom(1-\frac{k-1}{n})$ and $X_{n,k}$ are independent.
#TODO 
By WLLN for triangular array, 
#TODO 

###### E.g.2 Occupacy problem
#TODO 

## 7.5 Borel-Cantelli lemma
###### Thm.
For a sequence of events $A_{n}$ from the same probability space,
$A:=\bigcap_{m=0}^{\infty} \bigcup_{n \ge m} A_{n}=\{A_{n} \text{ i.o.}\}$.
1. $\text{I\kern-0.15em P}(A)=0$ if $\sum_{n} \text{I\kern-0.15em P}(A_{n})<\infty$.
2. $\text{I\kern-0.15em P}(A)=1$ if $\sum_{n} \text{I\kern-0.15em P}(A_{n})=\infty$ and $A_i$ are mutually independent events.

Rmk. We can state the lemma as an example of "zero-one law": when $A_i$ are mutually independent events, $\text{I\kern-0.15em P}(A)$ equals either 0 or 1.

###### Proof.
Proof of 1.
$\forall m, A \subset \cup_{n=m}^{\infty}A_{n}$, therefore $\text{I\kern-0.15em P}(A) \le \sum_{n=m}^{\infty} \text{I\kern-0.15em P}(A_{n})$, and the latter goes to 0 as $n \to \infty$ (Cauchy criterion).

Proof of 2.
To prove $\text{I\kern-0.15em P}(A)=1$, we typically prove $\text{I\kern-0.15em P}(A^C)=0$.
$$
\begin{aligned}
\text{I\kern-0.15em P}(\bigcap_{n=m}^{\infty} A_{n}^{C})
&=\prod_{n=m}^{\infty} (1-\text{I\kern-0.15em P}(A_{n})), \text{by independence} \\
&\le \prod_{n=m}^{\infty} \exp(-\text{I\kern-0.15em P}(A_{n})), \text{by } 1-x \le e^{-x} \\
& = \exp(-\prod_{n=m}^{\infty} \text{I\kern-0.15em P}(A_{n})) \to 0  \text{ as } m \to \infty 
\end{aligned}
$$

###### Application. Infinite Monkey 
Consider an infinite-length string produced from a finite alphabet by picking each letter independently at random, uniformly from the alphabet (say the alphabet has n letters). Fix a string S of length m from the same alphabet. Let $E_{k}$ be the event "the m-substring starting at position k is the string S". Then, infinitely many of the $E_{k}$ occur with probability 1.

Proof. Note that the events $\{E_{m \cdot j}\}_{j=0}^{\infty}$, a subsequence of $\{E_{k}\}$, are independent because disjoint, where $\sum_{j=1}^{\infty} \text{I\kern-0.15em P}(E_{mj})=\sum_{j=1}^{\infty} (\frac{1}{n})^{m}=\infty$ and $\text{I\kern-0.15em P}(E_{mj} \text{ i.o.})=1$. Therefore  $\text{I\kern-0.15em P}(E_{k} \text{ i.o.})=1$.

###### Another zero-one law
Thm. For a sequence of events $A_{n}$ from the same probability space, let $\mathcal{A}:=\sigma(A_{1},A_{2},\dots)$. If $A \in \mathcal{A}$ and for any n, A is independent of the finite collection $A_{1},A_{2},\dots,A_{n}$, then $P(A)$ is either 0 or 1.

Proof. $A \in \mathcal{A}$ means A is definable in terms of $A_{1},A_{2},\dots$ From measure theory, that means $\exists \{C_{n}\}$ s.t. $C_{n}\in \mathcal{A_{n}}$ and $\text{I\kern-0.15em P}(A \triangle C_{n}) \to 0  \text{ as } n \to \infty$, i.e.  $\text{I\kern-0.15em P}(A \cap C_{n}) \to \text{I\kern-0.15em P}(A)$. On the other hand, A being independent of events in $\mathcal{A_{n}}$, $\text{I\kern-0.15em P}(A \cap C_{n})=\text{I\kern-0.15em P}(A) \text{I\kern-0.15em P}(C_{n})\to P(A)^{2}$, therefore $\text{I\kern-0.15em P}(A)=\text{I\kern-0.15em P}(A)^{2}$.

###### Kolmogorov's zero-one law
Def. (**Tail $\sigma$-field**): Consider a sequence of r.v.s. $X_{n}$ in the same probability space. We define $\mathcal{H}_{n}:=\sigma(X_{n}, X_{n+1},\dots )$ be the $\sigma$-field induced by r.v.s. defined above in Part 3.4. Then $\mathcal{H}_{n}$ is decreasing ($\mathcal{H_{n}} \supset \mathcal{H_{n+1}} \supset \mathcal{H_{n+2}} \dots$), as the number of r.v.s. is decreasing. $\mathcal{H}_\infty:=\cap_{n} \mathcal{H}_{n}$, called the tail $\sigma$-field.

Def. (**Tail events**): Elements in $\mathcal{H}_{\infty}$, which must be events that do not refer to any finite subcollections $\{X_{1},X_{2},\dots, X_{n}\}$. For examples, $\{ X_{n}>0, \text{ i.o.} \}, \{ \limsup_{n} X_{n}=\infty \}, \{ \sum_{n} X_{n} \text{ converges} \}$.

Thm. (**Kolmogorov's zero-one law**) If $\{X_{n}\}$ is a independent r.v. sequence, then $\forall H \in \mathcal{H}_{\infty}$, $\text{I\kern-0.15em P}(H)$ is either 0 or 1. 

Def. (**Tail function**) A r.v. Y defined based on independent r.v. sequence $\{X_{n}\}$ that is $\mathcal{H}_{\infty}$-measurable.

E.g. $Y:=\limsup_{n} X_{n}$ is a tail func, while $Y':=X_{1}+X_{2}$ is not. By Kolmogorov's zero-one law, when $\{\omega:Y<y\} \in \mathcal{H}_{\infty}$, $\text{I\kern-0.15em P}(Y \le y)$ is either 0 or 1, i.e., $Y$ is a constant r.v.

Appli. Let Y be a tail func, then $\exists k, -\infty \le k \le +\infty$, s.t., $\text{I\kern-0.15em P}(Y=k)=1$.

## 7.6 Strong LLN
Motiv. In WLLN, the condition is i.i.d. sequence $\{X_{n}\}$ that $\text{I\kern-0.15em E}X_{i}=\mu, |\mu|<\infty$, and the result is $\frac{S_{n}}{n}  \overset{\text{I\kern-0.15em P}}{\to} \mu$. But what's the necessary condition?

Thm. For i.i.d. sequence $\{X_{n}\}$ and some constant $\mu$, $\frac{S_{n}}{n}  \overset{\text{I\kern-0.15em P}}{\to} \mu$ iff (1) or (2).
1. $\text{I\kern-0.15em P}(|X_{1}|>n) \in o(\frac{1}{n})$ and $\int_{[-n,n]}x \ \mathrm{d} F \to \mu  \text{ as } n \to \infty$. The latter can also be written as $\text{I\kern-0.15em E}(X_{1}\mathbb{1}(|X_{1}| \le n))$.
2. The c.f. of $X_{j}$ is differentiable at $t=0$, and $\phi'(0)=i \mu$.

Thm. (**Strong law of large number**) For i.i.d. sequence $\{X_{n}\}$,
1. $\frac{S_{n}}{n}   \overset{a.s.}{\to} \mu$ iff $|\text{I\kern-0.15em E}X_{i}|<\infty$.
2. $\frac{S_{n}}{n} \overset{2}{\to} \mu$ iff $|\text{I\kern-0.15em E}X_{i}^{2}|<\infty$.

## 7.7 The law of the iterated logarithm
Skipped.