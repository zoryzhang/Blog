Course MATH 540@UIUC

# Reference
- nabla: https://ppasupat.github.io/a9online/wtf-is/nabla.html

# Guide
> Took the class with him back in 2018. I would say his exams are pretty similar to the comps, for example: [https://math.illinois.edu/system/files/2021-02/MATH 540 - Jan 2021.pdf](https://math.illinois.edu/system/files/2021-02/MATH%20540%20-%20Jan%202021.pdf) . The homework from folland's book is kind of easy compare to the exams. I mean, this is a comprehensive exam class for the Math PhD people, so you shouldn't expect it to be any less, and real analysis is known to be hard for many people.

# Textbook
Gerald B. Folland, Real Analysis

# CH0
## Reminder
- Do algebra with $\mu(E)$ carefully, since it can be infinity.

## Notation
- X: the universal set.
- $\mathcal{E}$: a collection of subsets.
- $\mathcal{P}(X)$: the power set $\{E:E\subset X\}$.
- ":=" means can be done by definition.

## Set theory
Nota. $A \subset B$: A can be B.

Nota. A set $A$ is smaller than set $B$ is defined as $A \subset B$ but $A \ne B$.

> Def. (**Product set $X \times Y$**)

> Def. (**map**)

> Def. (**todo**) Let $\{X_{\alpha}\}_{\alpha \in A}$ be an indexed collection of nonempty sets, $X:=\prod_{\alpha \in A} X_{\alpha}$, and $\pi_{\alpha}: X \to X_{\alpha}$ the coordinate maps.
> 
> $f: A \to \bigcup_{\alpha \in A} X_{\alpha}$.

> Def. (**Arbitrary infinite sum**) For a set E, $\sum_{x \in E} f(x):=\sup \{\sum_{x\in F} f(x): \text{finite set } F \subset E \}$.

> Def. (**Set limit**) Given $A_{1}, A_{2}, \dots \in \mathcal{F}$, 
$$\limsup_{n \to  \infty}A_{n}:=\bigcap_{m=1}^{\infty} \bigcup_{n=m}^{ \infty} A_{n}=\bigcap_{m=1}^{\infty} B_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for infinitely many n}\}$$

$$\liminf_{n\to  \infty}A_{n}:=\bigcup_{m=1}^{  \infty} \bigcap_{n=m}^{ \infty} A_{n}=\bigcup_{m=1}^{\infty} C_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for all but finitely many n}\}$$

Recall:
1. $f$ is continuous at x if $\forall \{x_{n}\}, x_{n} \to x, n \to  \infty \Longrightarrow \lim_{n \to  \infty} f(x_{n})= f(\lim_{n\to\infty} x_{n} ) = f(x)$.
2. $\limsup_{n}x_{n}=\lim_{m \to  \infty} \sup_{n \ge m} x_{n}=\lim_{m \to  \infty} c_{m}$, where $c_m$ is monotonic, so that it must converge if we include $\pm \infty$.

Proof. 
Consider $\omega \in RHS$ or not. If yes, $\omega \in B_{m}, \forall m$; if not, disappear eventually.

Proof. 
Consider $\omega \in RHS$ or not. If yes, appear eventually; otherwise fail.

Rmk. $\liminf A_{n} \subset \limsup A_{n}$; if equal, we say $A_{n}$ converges.

E.g. Monotonic set sequence converges (if including $\infty$).
# CH1 Measure theory
## 1.2 $\sigma$-algebra/field
> Def. (**Algebra** of sets of X) A non-empty collection $\mathcal{A}$ of subsets of X, that is closed under finite union and complements. In other word,
1. $E_{1}, E_{2} \in \mathcal{A} \to E_{1} \cup E_{2} \in \mathcal{A}$.
2. $E\in \mathcal{A} \to E^{C} \in \mathcal{A}$.

Rmk. a) Algebra is closed under finite intersection; b) $\emptyset, X \in \mathcal{A}$.

> Def. (**$\sigma$-algebra** of sets of X) A non-empty collection $\mathcal{A}$ of subsets of X, that is closed under countable union and complements.
E.g. $\mathcal{A}=\{ E\in X:\text{E is co-countable} \}$.

Prop. $\mathcal{A}$ is a $\sigma$-algebra iff (a) $\mathcal{A}$ is a algebra; (b)$$E_{j} \text{ mutually disjoint}, E_{j}\in \mathcal{A} \to \bigcup_{j=1}^{\infty} E_{j} \in \mathcal{A}$$

Proof. $\cup E_{j}=\cup_{j} [E_{j} \setminus (\cup_{k<j} E_{k})] \in \mathcal{A}$. "This device of replacing a sequence of sets by a disjoint sequence is worth remembering."

Lemma. The intersection of any family of $\sigma$-algebras on X is again a $\sigma$-algebras.

> Def. (**$\sigma$-algebra generated by $\mathcal{E}$**) For $\mathcal{E} \subset \mathcal{P}(X)$, i.e. a collection of subsets of X, there's a **unique** **smallest** $\sigma$-algebra $\mathcal{M(E)}$ containing $\mathcal{E}$, namely, the intersection of all $\sigma$-algebras containing $\mathcal{E}$. 

Lemma. (1.1) $\mathcal{E\subset M(F) \implies M(E) \subset M(F)}$.

> Def. (**Toplogy** of subsets of X) A non-empty collection $\mathcal{F}$ of subsets of X , satisfying (a) $\emptyset, X \in \mathcal{F}$; (b) closed under arbitrary union; (c) closed under finite intersection.
> 
> Def. (**Toplogical space**) A pair $(X, \mathcal{F})$.

Nota. $G$ is the family of open sets; $F$ is the family of closed sets; $G_{\delta}$ is the countable intersection of open sets; $F_{\delta \sigma}$ is the countable union of  $F_{\delta}$ ...

> Def. (**Borel $\sigma$-algebra** of $(X, \mathcal{F})$) The $\mathcal{M}$(G), denoted as $\mathcal{B}_X$, where G is the aforementioned family of open sets. 

Prop. $\mathcal{M}$(G) is the same as $\mathcal{M}(\text{open intervals})$, $\mathcal{M}(F)$, $\mathcal{M}(\text{the open rays } \{(a, \infty)\})$, etc.

> Def. (**Borel set**) A Borel set is a member of $\mathcal{B}_X$. E.g. $G_{\delta}, F_{\sigma}$ are Borel set. (Many sets look like either one of these two.)

> Def. (**Product $\sigma$-algebra**) We ask for $\mathcal{B}_{\mathbb{R}^{n}} = \bigotimes_{j=1}^{n} \mathcal{B}_{\mathbb{R}}$. This definition enables it by: let $\{X_{\alpha}\}_{\alpha \in A}$ be an indexed collection of nonempty sets, $X:=\prod_{\alpha \in A} X_{\alpha}$, $\pi_{\alpha}: X \to X_{\alpha}$ the coordinate maps, and $\mathcal{M}_{\alpha}$ is a $\sigma$-algebra on $X_{\alpha}$, then define $\bigotimes \mathcal{A_{\alpha}}:=\{ \pi_{\alpha}^{-1}(E_{\alpha}):E_{\alpha} \in \mathcal{M}_{\alpha}, \alpha \in A \}$.

#NotCovered Prop 1.1-1.6
## 1.3 Measure
> Def. (**Measure** $\mu$ on **measurable space** (X, $\mathcal{A}$)) $\mu:\mathcal{A} \to [0,\infty]$, s.t.
> 1. $\mu(\emptyset)=0$;
> 2. Countable additivity ($\sigma$-additivity). If $E_{1}, E_{2}, \dots$ is a collection of **disjoint** members of $\mathcal{A}$, i.e. $E_{i} \cap E_{j} = \emptyset$ for all $i \ne j$, then $\mu(\bigcup_{i=1}^ {\infty} E_{i})=\sum_{i=1}^ {\infty} \mu(E_{i})$.

> Def. (**Finite measure**) $\mu(X)<\infty$.
> 
> Def. (**$\sigma$-finite measure**) $X=\bigcup E_{j}, s.t., \forall j, \mu(E_{j})<\infty$.
> 
> Def. (**Semifinite measure**) $\forall E\in \mathcal{A}, \mu(E)=\infty \to (\exists F \subset E, 0<\mu(F)<\infty)$ .
> 
> Def. (**Null set and "almost everywhere (a.e.)"**) E is a null set if $\mu(E)=0$. Proposition A is true almost everywhere if it is true on all but null set.

E.g. Given $f: X \to [0,\infty]$, we can define a measure by $\mu(E)=\sum_{x \in E} f(x)$.
1. It's semifinite iff $f(x)<\infty$.
2. It's $\sigma$-finite iff it's semifinite and $\{x:f(x)>0\}$ is countable.
3. It's called **counting measure** if for some $x_{0}\in X$, $f(x)=\mathbb{1}(x=x_{0})$.
4. It's called **point mass or Dirac measure** if $f(x)=1$.

Thm. Properties of measure:
1. (**Monotone**) $E, F \in  \mathcal{A}, E\subset F \implies \mu(E) \le \mu(F)$.
2. (**$si$-subadditive**) $\mu(\cup_{j=1}^{\infty} E_{j}) \le \sum_{j=1}^{\infty} \mu(E_{j})$.
3. (**Continuity from below**) $E_{1} \subset E_{2} \dots \implies \mu(\cup E_{j})=\lim \mu(E_{j})$.
4. (**Continuity from above**) $E_{1} \supset E_{2} \dots; \mu(E_{1})<\infty \implies \mu(\cap E_{j})=\lim \mu(E_{j})$. The $\mu(E_{1})<\infty$ is to enable $\mu(E_{1} \setminus E_{j})=\mu(E_{1})-\mu(E_{j})$, in the convertion between union and intersection.

Prop. $\sigma$-finite implies semifinite. 

Proof. For every E s.t. $\mu(E)=\infty$, given $X=\cup E_{j}$, define $F_{j}:=E_{j} \cap E$. By subadditivity, $\infty = \mu(E)=\mu(\bigcup F_{j}) \le \sum \mu(F_{j})$, then $\exists j, \mu(F_{j})>0$. By monotoncity, $\mu(F_{j}) \le \mu(E_{j}) < \infty$. These two gives the $F:=F_{j}$ as the non-trivial measure subset for each $E$.

> Def. (**Complete**) A measure whose domain contains all subsets of null sets. #NotCovered  THM1.9.

### Continuity
> Def. (**Continuity of general measure**) $\mu$ is continuous if $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n):=\mu(A)$. Notice the closeness under union&intersection gives that $A:=\limsup_{n}A_{n} \in \mathcal{F}$.

Thm. (**Countable additivity implies continuity**)

Proof. For all convergent sequence $\{A_{n}\}$, which means

1. Case1: monotonic increasing An ($A_{n-1} \subset A_{n}$)
Recall countable additivity, construct $D_{n}=A_{n} \setminus A_{n-1}$, then 

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
&:=\mu(\lim_{n \to  \infty} A_n)
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

Prop. (**Finite additivity + continuity iff countable additivity**)
Proof. (only => is needed) 
Recall continuity: $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n)=\mu(A)$
and (countable additivity) If $A_{1}, A_{2}, \dots$ is a collection of disjoint members of $\mathcal{F}$, then 

$$
\mu(\bigcup_{i=1}^ {\infty} A_{i})
=\mu( \lim_{n \to  \infty} \bigcup_{i=1}^{n}A_{i}  )
= \lim_{n \to  \infty} \mu( \bigcup_{i=1}^{n}A_{i}  )
= \lim_{n \to  \infty} \sum_{i=1}^ {n} \mu(A_{i}  )
=\sum_{i=1}^ {\infty} \mu(A_{i})
$$
## 1.4 Outer measure: the tools to construct measure
Motiv. In calculus, one defines area by marking grids inside and outside. Approximation from the outside is what we're going to build in this session.

> Def. (**Outer measure** on X) $\mu^{*}: \mathcal{P}(X) \to [0,\infty]$, s.t.
> 1. $\mu^{*}(\emptyset)=0$;
> 2. Monotonicity;
> 3. ($\sigma$-subadditivity) $\mu^{*}( \cup A_{j}) \le \sum \mu^{*}(A_{j})$.

Prop. (1.10) Let $\mathcal{E} \subset \mathcal{P}(X)$ be a family of "elementary sets" that we can later choose, and $\rho: \mathcal{E} \to [0,\infty]$, such that $\emptyset, X \in \mathcal{E}, \rho(\emptyset)=0$. These elementary sets are enough to define a outer measure:
$$
\mu^{*}(A):= \inf_{ \{E_{j}\} } \{ \sum_{j=1}^{\infty} \rho(E_{j}): E_{j} \in \mathcal{E}, A \subset \bigcup_{j=1}^{\infty} E_{j} \}
$$

Proof. The first and the second condition come immediately from the definition of infimum. For the third one, again, consider $\mu^{*}(A_{j})$ as a infimum the largest lowerbound, then for any j and $\epsilon_j>0$, $\mu^{*}(A_{j})+\epsilon_{j}$ is not a lowerbound, therefore exists $\sum_{k=1}^{\infty} \rho(E_{j,k}) < \mu^{*}(A_{j})+\epsilon_{j}$. Suming up LHS gives a value that's less than $\sum \mu^{*}(A_{j})+\sum \epsilon_{j}$ but greater than $\mu^{*}( \cup A_{j})$. Let $\epsilon_{j}=\epsilon*2^{-j}$ and send $\epsilon$ to 0 gives the desired inequality.

> Def. (**$\mu^{*}$-measuable**) A set $A \subset X$ is called $\mu^{*}$-measuable if
> $$
\forall E\subset X, \mu^{*}(E)=\mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})
$$

Rmk. Notice that to show a set is $\mu^{*}$-measuable, it suffices to show $$
\forall E\subset X,s.t. \mu^{*}(E)<\infty, \mu^{*}(E) \ge \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})
$$
Motiv. Given a well-behaved set E, the outer measure of A, $\mu^{*}(E)-\mu^{*}(E\cap A^{c})$, is equal to the inner measure of A, $\mu^{*}(E\cap A)$.

Thm. (**Caratheodory's thm**) If $\mu^{*}$ is an outer measure on X, then the collection $\mathcal{M}$ of $\mu^{*}$-measuable sets is a $\sigma$-algebra, and $\mu^{*}|_{\mathcal{M}}$ is a measure on measuable space $(X, \mathcal{M})$.