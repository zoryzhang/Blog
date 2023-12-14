>  The note of UIUC course MATH 540 Real Analysis in Fall 2023, by Zory Zhang. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (maybe not up-to-date) can be found [here](real%20analysis.pdf).

# Reference
- nabla: https://ppasupat.github.io/a9online/wtf-is/nabla.html

# Guide
> Took the class with him back in 2018. I would say his exams are pretty similar to the comps, for example: [https://math.illinois.edu/system/files/2021-02/MATH 540 - Jan 2021.pdf](https://math.illinois.edu/system/files/2021-02/MATH%20540%20-%20Jan%202021.pdf) . The homework from folland's book is kind of easy compare to the exams. I mean, this is a comprehensive exam class for the Math PhD people, so you shouldn't expect it to be any less, and real analysis is known to be hard for many people.

# Textbook
Gerald B. Folland, Real Analysis
[Sol1](https://people.umass.edu/bban/Solutions.html), [Sol2](https://www.math.wustl.edu/~sawyer/m5051f09/hwindex.html), [Sol3](https://drive.google.com/file/d/16Qn-uS54XDMrnI18poGnOzlWrl50l4Vo/view?usp=sharing)

# Ch0 Preliminaries

## High level techniques
1. When we want to show an inequality related to measure, it's usually easier to enlarge it, since the subadditivity is giving you more terms during enlarging. Otherwise, you need to organize your terms and take a pair of it to apply subadditivity. Also, during enlarging, you can directly drop unnecessary terms in intersection, due to monotonicity.
2. When showing general inequality, though, try both. Sometimes either is easier.
3. Do algebra with $\mu(E)$ carefully, since it can be infinity.

## Technical tricks
1. (Chebyshev’s inequality in $L^{1}$) $m(|f-g|>\lambda) \le \int_{|f-g|>\lambda} 1 \le \int_{|f-g|>\lambda} \frac{|f-g|}{\lambda} \le \frac{1}{\lambda} ||f-g||_{1}$. ^cd31a5

## Notation
- X: (in plain text) the universal set.
- $\mathcal{E}$: (mathcal in tex) a collection of subsets.
- $A, E$: (in tex) a set.
- $\mathcal{P}(X)$: the power set $\{E:E\subset X\}$.
- $\cup A_{j}$ can be finite, countable, or arbitrary union(same for other symbols like summation/intersection) and should be clear in context. Arbitrary union usually will be stressed by using $\cup_{\alpha}^{\infty} A_{\alpha}$.
- ":=" means this is definition, or can be done by definition.
- WLOG: without loss of generality
- WTS: want to show
- OTAH: on the other hand
- $A \subset B$: interchangeable with $A \subseteq B$. note that A can be equal to B.
## Set theory

Nota. A set $A$ is called **smaller** than set $B$, if $A \subset B$ but $A \ne B$.

> [!note] Def. (**Product set $X \times Y$**)

> [!note] Def. (**map**)

> [!note] Def. (**todo**) 
> Let $\{X_{\alpha}\}_{\alpha \in A}$ be an indexed collection of nonempty sets, $X:=\prod_{\alpha \in A} X_{\alpha}$, and $\pi_{\alpha}: X \to X_{\alpha}$ the coordinate maps.
> 
> $f: A \to \bigcup_{\alpha \in A} X_{\alpha}$.

> [!note] Def. (**Arbitrary infinite sum**) 
> For a set E, $\sum_{x \in E} f(x):=\sup \{\sum_{x\in F} f(x): \text{finite set } F \subset E \}$.

> [!note] Def. (**Set limit**) 
> Given $A_{1}, A_{2}, \dots \in \mathcal{F}$, 
$$\limsup_{n \to  \infty}A_{n}:=\bigcap_{m=1}^{\infty} \bigcup_{n=m}^{ \infty} A_{n}=\bigcap_{m=1}^{\infty} B_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for infinitely many n}\}$$
$$\liminf_{n\to  \infty}A_{n}:=\bigcup_{m=1}^{  \infty} \bigcap_{n=m}^{ \infty} A_{n}=\bigcup_{m=1}^{\infty} C_m=\{\omega \in \Omega : \omega \in  A_{n} \text{ for all but finitely many n}\}$$

Recall:
1. $f$ is continuous at x if $\forall \{x_{n}\}, x_{n} \to x, n \to  \infty \Longrightarrow \lim_{n \to  \infty} f(x_{n})= f(\lim_{n\to\infty} x_{n} ) = f(x)$.
2. $\limsup_{n}x_{n}=\lim_{m \to  \infty} \sup_{n \ge m} x_{n}=\lim_{m \to  \infty} c_{m}$, where $c_m$ is monotonic, so that it must converge if we include $\pm \infty$.

Proof. 
1. Consider $\omega \in RHS$ or not. If yes, $\omega \in B_{m}, \forall m$; if not, disappear eventually.
2. Consider $\omega \in RHS$ or not. If yes, appear eventually; otherwise fail.

Rmk. $\liminf A_{n} \subset \limsup A_{n}$; if equal, we say $A_{n}$ converges.

E.g. Monotonic set sequence converges (if including $\infty$).

## Elementary real analysis
- Compact set: for any open cover of S, there's a finite subcover for S.
- On real line: 
    - A set is compact as long as closed + bounded, or sequentially campact.
    - Any open set can be expressed as **countable** union of mutually **disjoint** open intervals.
- Arbitrary union of open set still open, arbitrary intersection of closed set still closed.
- $f:X \to Y$ is continuous on X iff for any open set U in Y, $f^{-1}(U)$ is open in X.
- $\sum_{j=1}^{n} \sum_{k=1}^{\infty}=\sum_{k=1}^{\infty} \sum_{j=1}^{n}$ is interchangable. Proof by induction on n.
- $\forall n, f_{n}$ continuous at $a$ implies that $f:=\lim f_{n}$ continuous at $a$.


# Ch1 Measure theory
## 1.2 Some algebraic structures

^f3e312

> [!note] Def. (**Algebra** of sets of X) 
> A non-empty collection $\mathcal{A}$ of subsets of X, that is closed under finite union and complement. In other word,
> 1. $E_{1}, E_{2} \in \mathcal{A} \to E_{1} \cup E_{2} \in \mathcal{A}$.
> 2. $E\in \mathcal{A} \to E^{C} \in \mathcal{A}$.

Rmk. a) Algebra is closed under finite intersection; b) $\emptyset, X \in \mathcal{A}$. This is important when it comes to covering.

> [!note] Def. (**$\sigma$-algebra** of sets of X) 
> A non-empty collection $\mathcal{A}$ of subsets of X, that is closed under countable union and complements. E.g. $\mathcal{A}=\{ E\in X:\text{E is co-countable} \}$.

> Prop. $\mathcal{A}$ is a $\sigma$-algebra iff (a) $\mathcal{A}$ is a algebra; (b)$$E_{j} \text{ mutually disjoint}, E_{j}\in \mathcal{A} \to \bigcup_{j=1}^{\infty} E_{j} \in \mathcal{A}$$

Proof. $\cup E_{j}=\cup_{j} [E_{j} \setminus (\cup_{k<j} E_{k})] \in \mathcal{A}$. "This device of replacing a sequence of sets by a disjoint sequence (yet preserving the union) is worth remembering."

> Lemma. The intersection of any family of $\sigma$-algebras on X is again a $\sigma$-algebra.

> [!note] Def. (**$\sigma$-algebra generated by $\mathcal{E}$**) 
> For $\mathcal{E} \subset \mathcal{P}(X)$, i.e. a collection of subsets of X, there's a **unique** **smallest** $\sigma$-algebra $\mathcal{M(E)}$ containing $\mathcal{E}$, namely, the intersection of all $\sigma$-algebras containing $\mathcal{E}$. 

> Prop. (1.1) $\mathcal{E\subset M(F) \implies M(E) \subset M(F)}$.

^db1186

> [!note] Def. (**Toplogy** of subsets of X) 
> A non-empty collection $\mathcal{F}$ of subsets of X , satisfying (a) $\emptyset, X \in \mathcal{F}$; (b) closed under arbitrary union; (c) closed under finite intersection.

> [!note] Def. (**Toplogical space**) A pair $(X, \mathcal{F})$.

Nota. $G$ is the family of open sets in X; $F$ is the family of closed sets; $G_{\delta}$ is the countable intersection of open sets; $F_{\delta \sigma}$ is the countable union of  $F_{\delta}$ ... **G is a toplogy**.

> [!note] Def. (**Borel $\sigma$-algebra** of $(X, \mathcal{F})$) 
> The $\mathcal{M}$(G), denoted as $\mathcal{B}_X$, where G is the aforementioned family of open sets. 

> Prop. (1.2) $\mathcal{M}$(G) is the same as $\mathcal{M}(\text{open intervals})$, $\mathcal{M}(F)$, $\mathcal{M}(\text{the open rays } \{(a, \infty)\})$, $\mathcal{M}(\text{the closed rays } \{[a, \infty)\})$, etc. These will be shown in 1.5.

> [!note] Def. (**Borel set**) 
> A Borel set is a member of $\mathcal{B}_X$. E.g. $G_{\delta}, F_{\sigma}$ are Borel set. (Many sets look like either one of these two.)

> [!note] Def. (**Product $\sigma$-algebra**) 
> We ask for $\mathcal{B}_{\mathbb{R}^{n}} = \bigotimes_{j=1}^{n} \mathcal{B}_{\mathbb{R}}$. The following definition enables it by: let $\{X_{\alpha}\}_{\alpha \in A}$ be an indexed collection of nonempty sets, $X:=\prod_{\alpha \in A} X_{\alpha}$, $\pi_{\alpha}: X \to X_{\alpha}$ the coordinate maps, and $\mathcal{M}_{\alpha}$ is a $\sigma$-algebra on $X_{\alpha}$, then define $\bigotimes \mathcal{A_{\alpha}}:=\{ \pi_{\alpha}^{-1}(E_{\alpha}):E_{\alpha} \in \mathcal{M}_{\alpha}, \alpha \in A \}$.

#NotCovered Prop 1.1-1.6

> [!note] Def. (Elementary family)
> A collection $\mathcal{E}$ of subsets of X, s.t.
> 1. $\emptyset \in \mathcal{E}$;
> 2. Closed under finite intersection;
> 3. If $E \in \mathcal{E}$, then $E^{c}$ is a finite disjoint union of members of $\mathcal{E}$.

> Prop. (1.7) For elementary family $\mathcal{E}$, the collection of finite disjoint union of members of $\mathcal{E}$ is an algebra.

^668d67

> [!note] Def. (**Ring**) 
> Closed under finite union and differences.

Rmk. 
1. A ring $\mathcal{R}$ is closed under finite intersections.
2. A ring is an algebra iff $X \in \mathcal{R}$.

## 1.3 Measure
> [!note] Def. (**Measure** $\mu$ on **measurable space** (X, $\mathcal{A}$)) 
> $\mu:\mathcal{M} \to [0,\infty]$, s.t.
> 1. $\mu(\emptyset)=0$;
> 2. Countable additivity ($\sigma$-additivity). If $E_{1}, E_{2}, \dots$ is a collection of **disjoint** members of $\mathcal{M}$, i.e. $E_{i} \cap E_{j} = \emptyset$ for all $i \ne j$, then $\mu(\bigcup_{i=1}^ {\infty} E_{i})=\sum_{i=1}^ {\infty} \mu(E_{i})$.

> [!note] Def. (**Finite measure**) 
> $\mu(X)<\infty$.

> [!note] Def. (**$\sigma$-finite measure**) 
> $X=\bigcup E_{j}, s.t., \forall j, \mu(E_{j})<\infty$.

> [!note] Def. (**Semifinite measure**) 
> $\forall E\in \mathcal{M}, \mu(E)=\infty \to (\exists F \subset E, 0<\mu(F)<\infty)$ .

> [!note] Def. (**Null set and "almost everywhere (a.e.)"**) 
> E is a null set if $\mu(E)=0$. Proposition A is true almost everywhere if it is true on all but null set.

E.g. Given $f: X \to [0,\infty]$, we can define a measure by $\mu(E)=\sum_{x \in E} f(x)$.
1. It's semifinite iff $f(x)<\infty$.
2. It's $\sigma$-finite iff it's semifinite and $\{x:f(x)>0\}$ is countable.
3. It's called **counting measure** if $f(x)=1$.
4. It's called **point mass or Dirac measure** if for some $x_{0}\in X$, $f(x)=\mathbb{1}(x=x_{0})$.

> [!important] Thm. Properties of measure:
> 1. (**Monotone**) $E, F \in  \mathcal{M}, E\subset F \implies \mu(E) \le \mu(F)$.
> 2. (**$\sigma$-subadditive**) $\mu(\cup_{j=1}^{\infty} E_{j}) \le \sum_{j=1}^{\infty} \mu(E_{j})$.
> 3. (**Continuity from below**) $E_{1} \subset E_{2} \dots \implies \mu(\cup E_{j})=\lim \mu(E_{j})$.
> 4. (**Continuity from above**) $E_{1} \supset E_{2} \dots; \mu(E_{1})<\infty \implies \mu(\cap E_{j})=\lim \mu(E_{j})$. The $\mu(E_{1})<\infty$ is to enable $\mu(E_{1} \setminus E_{j})=\mu(E_{1})-\mu(E_{j})$, in the convertion between union and intersection.

Ex. (Ch1 q8) $\mu(\liminf E_{j}) \le \liminf \mu(E_{j})$; If $\mu(\cup E_{j})<\infty$, then $\mu(\limsup E_{j}) \ge \limsup \mu(E_{j})$.

> Prop. $\sigma$-finite implies semifinite. 

Proof. For every E s.t. $\mu(E)=\infty$, given $X=\cup E_{j}$, define $F_{j}:=E_{j} \cap E$. By subadditivity, $\infty = \mu(E)=\mu(\bigcup F_{j}) \le \sum \mu(F_{j})$, then $\exists j, \mu(F_{j})>0$. By monotoncity, $\mu(F_{j}) \le \mu(E_{j}) < \infty$. These two gives the $F:=F_{j}$ as the non-trivial measure subset for each $E$.

Ex. Given E, define $\mu_{E}(A):=\mu(A \cap E)$. Then it's a measure.

> [!note] Def. (**Complete**) 
> A measure whose domain contains all subsets of null sets.

#NotCovered  THM1.9. Completion of measure.

### Continuity of measure (not covered)
> [!note] Def. (**Continuity of general measure**) 
> $\mu$ is continuous if $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n):=\mu(A)$. Notice the closeness under union&intersection gives that $A:=\limsup_{n}A_{n} \in \mathcal{F}$.

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

## 1.4 Tools to construct measure
Motiv. In calculus, one defines area by marking grids inside and outside. Approximation from the outside is what we're going to build in the following.

> [!note] Def. (**Outer measure** on X) 
> $\mu^{*}: \mathcal{P}(X) \to [0,\infty]$, s.t.
> 1. $\mu^{*}(\emptyset)=0$;
> 2. Monotonicity;
> 3. ($\sigma$-subadditivity) $\mu^{*}( \cup A_{j}) \le \sum \mu^{*}(A_{j})$.

> Prop. (1.10) Let $\mathcal{E} \subset \mathcal{P}(X)$ be a family of "elementary sets" that we can later choose, and $\rho: \mathcal{E} \to [0,\infty]$, such that $\emptyset, X \in \mathcal{E}, \rho(\emptyset)=0$. These elementary sets are enough to define a outer measure:
$$
\mu^{*}(A):= \inf_{ \{E_{j}\} } \{ \sum_{j=1}^{\infty} \rho(E_{j}): E_{j} \in \mathcal{E}, A \subset \bigcup_{j=1}^{\infty} E_{j} \}
$$

Proof. The first and the second condition come immediately from the definition of infimum. For the third one, again, consider $\mu^{*}(A_{j})$ as a infimum the largest lowerbound, then for any j and $\epsilon_j>0$, $\mu^{*}(A_{j})+\epsilon_{j}$ is not a lowerbound, therefore exists $\sum_{k=1}^{\infty} \rho(E_{j,k}) < \mu^{*}(A_{j})+\epsilon_{j}$. Suming up LHS gives a value that's less than $\sum \mu^{*}(A_{j})+\sum \epsilon_{j}$ but greater than $\mu^{*}( \cup A_{j})$. Let $\epsilon_{j}=\epsilon*2^{-j}$ and sending $\epsilon$ to 0 gives the desired inequality.

> [!note] Def. (**$\mu^{*}$-measurable**) 
> A set $A \subset X$ is called $\mu^{*}$-measurable if
> $$ \forall E\subset X, \mu^{*}(E)=\mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})$$

Motiv. This definition can be understood as, when A is "good", we can use A to evaluate any $E\subset X$, such that the inner measure of A (intersection of two, approximate from inside), $\mu^{*}(E\cap A)$, is equal to the outer measure of A, $\mu^{*}(E)-\mu^{*}(E\cap A^{c})$.

Rmk. Notice that to show a set A is $\mu^{*}$-measurable, due to the subadditivity, it suffices to show 
$$
\forall E\subset X,s.t. \mu^{*}(E)<\infty, \mu^{*}(E) \ge \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})
$$

> Lemma. For a sequence of disjoint $\mu^*$-measurable sets $A_{j}$, let $B_{n}=\cup_{i=1}^{n} A_{i}$, then we have:
> $$\begin{aligned}
\mu^{*}(E\cap B_{n})
&=\mu^{*}(E\cap B_{n}\cap A_{n})+\mu^{*}(E\cap B_{n}\cap A_{n}^{c}) \\
\text{given disjoint}, &=\mu^{*}(E\cap A_{n})+\mu^{*}(E\cap B_{n-1}) \\
\text{by induction}, &= \sum_{i=1}^{n} \mu^{*}(E\cap A_{i})
\end{aligned} $$

Rmk. The above result can be extended to infinite sum since only one side is needed given subadditivity.

> [!important] Thm. (**Caratheodory's thm**) 
> If $\mu^{*}$ is an outer measure on X, then the collection $\mathcal{M}$ of $\mu^{*}$-measurable sets is a $\sigma$-algebra, and $\mu^{*}|_{\mathcal{M}}$ is a complete measure on measurable space $(X, \mathcal{M})$.

Proof.
1. $\mathcal{M}$ is an algebra: the goal is, given $A, B \in \mathcal{M}$, show that $\forall E\subset X,\mu^{*}(E)= \mu^{*}(E\cap (A \cup B))+\mu^{*}(E\cap (A \cup B)^{c})$. Taking the fact that $A$ is $\mu^{*}$-measurable, and let E be the latter two respectively, 
    $$
    \begin{aligned}
    \mu^{*}(E\cap (A \cup B))
    =&\mu^{*}(E\cap (A \cup B)\cap A)+\mu^{*}(E\cap (A \cup B)\cap A^c)\\
    =&\mu^{*}(E\cap A)+\mu^{*}(E\cap B\cap A^c)\\
    \mu^{*}(E\cap (A \cup B)^c)
    =&\mu^{*}(E\cap (A \cup B)^c\cap A)+\mu^{*}(E\cap (A \cup B)^c\cap A^c)\\
    =&\mu^{*}(E\cap (A \cup B)^c)=\mu^{*}(E\cap A^c \cap B^c)
    \end{aligned}
    $$
2. $\mathcal{M}$ is a $\sigma$-algebra: it suffices to prove it's closed under disjoint $\sigma$-union, and we only need to check one side of inequality. Define $B_{n}=\cup_{i=1}^{n} A_{i}$, 
$$
\begin{aligned}
\mu^{*}(E\cap B_{n})&= \sum_{i=1}^{n} \mu^{*}(E\cap A_{i}) \\
\mu^{*}(E)
&=\mu^{*}(E \cap (\cup_{i=1}^{n} A_{i} ))+\mu^{*}(E \cap (\cup_{i=1}^{n} A_{i} )^{c}) \\
&\ge\mu^{*}(E \cap B_{n})+\mu^{*}(E \cap (\cup_{i=1}^{\infty} A_{i} )^{c}) \\
&\ge\sum_{i=1}^{n} \mu^{*}(E \cap A_{i})+\mu^{*}(E \cap (\cup_{i=1}^{\infty} A_{i} )^{c}) \\
\text{take limit}, & \ge \sum_{i=1}^{\infty} \mu^{*}(E \cap A_{i})+\mu^{*}(E \cap (\cup_{i=1}^{\infty} A_{i} )^{c}) \\
\text{by subadditivity}, &\ge \mu^{*}(E \cap (\cup_{i=1}^{\infty} A_{i} ))+\mu^{*}(E \cap (\cup_{i=1}^{\infty} A_{i} )^{c})
\end{aligned}
$$
3. $\mu^{*}|_{\mathcal{M}}$ is a measure: we now know $\cup_{i=1}^{\infty} A_{i} \in \mathcal{M}$ is in the domain, which enable us to use the inequality above but with $\sigma$-union as E:
$$
\mu^{*}(\cup_{i=1}^{\infty} A_{i} ) \ge\sum_{i=1}^{n} \mu^{*}((\cup_{j=1}^{\infty} A_{j} ) \cap A_{i})+\mu^{*}((\cup_{i=1}^{\infty} A_{i} ) \cap (\cup_{i=1}^{\infty} A_{i} )^{c})
$$
The other side is again by $\sigma$-subadditivity.
4. $\mu^{*}|_{\mathcal{M}}$ is complete. Given $B \subset A,\mu^{*}(A)=\mu^{*}(B)=0$, $\forall E\subset X, \mu^{*}(E) \ge \mu^{*}(E\cap B^{c})=\mu^{*}(E\cap B)+\mu^{*}(E\cap B^{c})$.

> [!note] Def. (**Premeasure**) 
> $\mu_{0}:\mathcal{A} \to [0,\infty]$, $\mathcal{A}$ is a algebra, with:
> 1. $\mu_{0}=0$;
> 2. Any $\{ A_{j} \}_{j=0}^{\infty} \subset A$ that are sequence of disjoint sets s.t. $\bigcup_{j=1}^{\infty}A_{j} \in \mathcal{A}$, then $\mu_{0}(\cup A_{j})=\sum_{i=1}^{\infty} \mu_{0}(A_{j})$.

> Prop. Monotonicity of premeasure.

> Prop. (1.13) By applying Prop. 1.10 with $\rho=\mu_{0}$, one can construct outermeasure $\mu^{*}:\mathcal{P}(X) \to [0,\infty]$, which extends the domain of $\mu_{0}$. Then,
> 1. $\mu^{*}|_\mathcal{A}=\mu_{0}$;
> 2. $\forall A \in \mathcal{A}$, $A$ is $\mu^{*}$-measurable.

Proof. 
1. (Recall) $\mu^{*}(D):= \inf_{ \{A_{j}\} } \{ \sum_{j=1}^{\infty} \mu_{0}(A_{j}): A_{j} \in \mathcal{A}, D \subset \bigcup_{j=1}^{\infty} A_{j} \}$;
2. $\mu^{*}|_\mathcal{A} \le \mu_{0}$ is true since LHS is a lowerbound of a set containing $\mu_{0}(A)$ induced by sequence $\{ A, \emptyset, \emptyset, \emptyset, \dots \}$.
3. To show the other side, need to show the RHS is a lowerbound. We only have disjoint complete sequence additivity. For $A \in \mathcal{A}, \text{covering }\{A_{j}\}$, construct $B_{n}=A \cap (A_{n} \setminus \cup_{i<n} A_{i})$, then $\cup B_{i}=A \in \mathcal{A}$ given covering. Then $\mu_{0}(A)=\sum_{j} \mu_{0}(B_{j}) \le \sum_{j} \mu_{0}(A_{j})$.
4. Want to show: $\forall A \in \mathcal{A}, E \subset X, \mu^{*}(E) \ge \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})$. It suffices to show $\forall \epsilon>0, \mu^{*}(E)+\epsilon \ge \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})$. The LHS isn't a lowerbound, therefore exists covering $\{A_{j}\} \subset \mathcal{A}$ s.t.
$$
\begin{aligned}
\mu^{*}(E)+\epsilon 
&>\sum_{j} \mu_{0}(A_{j}) \\
\text{By disjoint additivity}, &= \sum_{j} \mu_{0}(A_{j} \cap A)+\mu_{0}(A_{j} \cap A^{c}) \\
&= \sum_{j} \mu^{*}(A_{j} \cap A)+\mu^{*}(A_{j} \cap A^{c}) \\
\text{By subadditivity}, &\ge  \mu^{*}(\cup_{j} (A_{j} \cap A))+\mu^{*}(\cup_{j} (A_{j} \cap A^{c}))\\
&=\mu^{*}(E \cap A)+\mu^{*}(E \cap A^c)
\end{aligned}
$$

> [!important] Thm. (1.14) 
> Algebra $\mathcal{A}$, $\sigma$-algebra $\mathcal{M}:=\mathcal{M(A)}$, premeasure $\mu_{0}$ on $\mathcal{A}$, and $\mu^{*}$ the outermeasure given in last thm. Then:
> 1. $\mu:=\mu^{*}|_{\mathcal{M}}$ is a measure on $\mathcal{M}$; (This gives the existence of measure extending $\mu_{0}$)
> 2. Any other measure $\tilde \mu$ that extends $\mu_{0}$ has $\forall E \in \mathcal{M}, \tilde \mu(E) \le \mu(E)$, with equality when $\mu(E)<\infty$.
> 3. If $\mu_{0}$ is $\sigma$-finite, then $\mu$ is unique. (This gives the uniqueness of measure extending $\mu_{0}$ under stronger condition)

^63f1c6

Proof. 
1. Let $\mathcal{B}$ the collection of $\mu^{*}$-measurable sets. By C-thm, $\mathcal{B}$ is a $\sigma$-algebra and $\mu^{*}|_{\mathcal{B}}$ is a measure. By Prop 1.13, $\mathcal{A} \subset \mathcal{B}$, and $\mathcal{M}$ is the smallest $\sigma$-algebra containing A, therefore $\mathcal{M} \subset \mathcal{B}$, $\mu^{*}|_{\mathcal{M}}$ is a measure.
2. Goal: $\forall E \in \mathcal{M}, \tilde \mu(E) \le \mu(E)$. Notice that for any covering $\{A_{j}\} \subset \mathcal{A}$ of E, $\tilde \mu(E) \le \tilde \mu(\cup A_{j}) \le \sum \tilde \mu(A_{j})=\sum \mu_{0}(A_{j})=\sum \mu(A_{j})$, therefore a lowerbound, which is not greater than the greatest lowerbound $\mu^{*}$.
3. Claim $\mu^{*}(\cup A_{j})=\tilde \mu(\cup A_{j})$: since both are measure extending $\mu_{0}$ defined on $\mathcal{A}$ where finite union is closed, consider using contituity by $$\begin{aligned}\mu^{*}(\cup A_{j})=\lim \mu^{*}(\cup_{j=1}^{\infty} A_{j})=\lim \mu^{*}(\cup_{j=1}^{\infty} A_{j}) \\ =\lim \mu_{0}(\cup_{j=1}^{\infty} A_{j})=\lim \tilde \mu(\cup_{j=1}^{\infty} A_{j})=\tilde \mu(\cup_{j=1}^{\infty} A_{j}) \end{aligned}$$.
4. Goal: $\forall E \in \mathcal{M}, \tilde \mu(E) \ge \mu(E)$ when $\mu(E)<\infty$. Notice that for any covering $\{A_{j}\} \subset \mathcal{A}$ of E, $\mu^{*}(E) \le \mu^{*}(\cup A_{j})=\tilde \mu(\cup A_{j})=\tilde \mu(E)+\tilde \mu(\cup A_{j} \setminus E)$. It suffices to show that $\tilde \mu(\cup A_{j} \setminus E) \le \epsilon$ for any $\epsilon>0$, and further more, $\mu^{*}(\cup A_{j} \setminus E) \le \epsilon$, given part 2. Consider adding $\epsilon$ to the infimum, i.e.  $\forall\epsilon>0$, there's a covering $\{A_{j}\} \subset \mathcal{A}$ of E, s.t. $\mu^{*}(E)+\mu^{*}(\cup A_{j} \setminus E)=\mu^{*}(\cup A_{j}) \le \sum \mu_{0}(A_{j}) < \mu^{*}(E)+\epsilon$. When $\mu(E)<\infty$, subtracting it on both sides gives the desired.
5. Goal: $\forall E \in \mathcal{M}, \tilde \mu(E)=\mu(E)$. Recall definition, $X=\cup A_{j}$, s.t. $A_{j} \in \mathcal{A}, \mu_{0}(A_{j})<\infty$. Make it disjoint by $B_{j}:=A_{j} \setminus (\cup_{k<j} A_{k})$ to have a partition of E. Then $\tilde \mu(E)=\sum \tilde \mu(E \cap B_{j})=\sum \mu(E \cap B_{j})=\mu(E)$, given part 4.

> Ex. (Ch1 q18)
> 1. If $\mu^{*}(E)<\infty$, then $E$ is $\mu^{*}$-measurable iff $\exists B \in \mathcal{A}_{\sigma \delta}$ with $E \subset B$ and $\mu^{*}(B \setminus E)=0$;
> 2. If $\mu_{0}$ is $\sigma-$finite, the restriction of $\mu^{*}(E)<\infty$ is superfluous.

Proof. 
1. (<=) By showing both $B, B \setminus E$ are $\mu^{*}$-measurable and within the $\mathcal{M}$. Or by enlarging $\mu^{*}(A \cap E)+\mu^{*}(A \cap E^{c})$ into $\mu^{*}(A \cap B)+\mu^{*}(A \cap B^{c})$ to bound above $\mu^{*}(A)$. (=>) Just take intersection of open set covering.
2. (=>) Partition E into disjoint finite pieces, find $B_{n,j} \in \mathcal{A_{\sigma}}$, s.t., $\mu^{*}(B_{n,j}) \le \mu^{*}(E_{j})+ \frac{1}{n}2^{-j}, i.e. \mu^{*}(B_{n,j} \setminus E) \le \epsilon_{n,j}$. Then we can show $\mu^{*}(B \setminus E) \le \frac{1}{n}$.

> Ex. (Ch1 q19) For an outer measure induced from a finite premeasure, then $\mu^{*}(E)+\mu^{*}(E^{c})=\mu^{*}(X)$ implies E is $\mu^{*}$-measurable.

Proof. As usual, take $\epsilon=\frac{1}{n}$ so that there's $B_{n} \in A_{\sigma}, B_{n} \supset E$, $\mu^{*}(B_{n}) \le \mu^{*}(E) + \frac{1}{n}$, therefore $B:=\cap B_{n}\in A_{\sigma \delta}$, $\mu^{*}(B)=\mu^{*}(E)$. Notice B is measurable, therefore we can have $\mu^{*}(B)+\mu^{*}(B^{c})=\mu^{*}(X)$, and further, $\mu^{*}(B^{c})=\mu^{*}(E^{c})$. To get $B \setminus E$ to apply ex. ch1q18, consider, $\mu^{*}(B^{c})=\mu^{*}(E^{c})=\mu^{*}(E^{c} \cap B)+\mu^{*}(E^{c} \cap B^{c})=\mu^{*}(B \setminus E)+\mu^{*}(B^{c})$.

> Ex. (Ch1 q24) $\mu$ is a finite measure. Suppose that $E \subset X, E \notin \mathcal{M}$ satisfies $\mu^{*}(E)=\mu^{*}(X)$.
> 1. If $A,B \in \mathcal{M}, A \cap E=B \cap E$, then $\mu(A)=\mu(B)$;
> 2. Let $\mathcal{M}_{E}:=\{ A \cap E : A \in \mathcal{M} \}$, and define function $v$ as $v(A \cap E)=\mu(A)$. Then $\mathcal{M}_{E}$ is a $\sigma$-algebra on E and $v$ is a measure on $\mathcal{M}_{E}$.

## 1.5 Borel measure on $\mathbb{R}$
Recall. $\mathcal{B_{\mathbb{R}}}:=\mathcal{M}(G)$.

> [!note] Def. 
> 1. **Open invervals** $\mathcal{A_{0}}:=\{ (a,b) : -\infty \le a < b \le +\infty \}$;
> 2. **h-intervals** $\mathcal{A_{h}}:=\{ (a,b]: -\infty \le a < b < +\infty \} \cup \{ (a, \infty) : -\infty \le a < +\infty  \} \cup \{\emptyset \}$
> 3. $\mathcal{A_{2}}:=$ finite union of disjoint h-intervals.

> Prop. $\mathcal{M(A_{0})}=\mathcal{M(A_{h})}=\mathcal{M(A_{2})}=\mathcal{M}(G):=\mathcal{B_\mathbb{R}}$.

Proof. By lemma 1.1, it suffices to show that $\mathcal{A_{0}}, \mathcal{A_{h}},\mathcal{A_{2}} \subset \mathcal{M}(G), \mathcal{A}(G) \subset \mathcal{M(A_{0})} \cap \mathcal{M(A_{h})}\cap \mathcal{M(A_{2})}$.

> Prop. $\mathcal{A_{2}}$ is a algebra.

> [!important] Thm. 
> $F:\mathbb{R} \to \mathbb{R}$ (non-strictly) increasing and right-continuous. We can construct premeasure $\mu_{0}$ by $\mu_{0}(\emptyset)=0$ and $\mu_{0}(\cup_{j=1}^{n} (a_{j},b_{j}])=\sum_{i=1}^{n} F(b_{j})-F(a_{j})$ where $(a_{j}, b_{j}]$ are disjoint.

Proof.
1. Goal: $\mu_{0}$ is well-defined (consistent with different union partition). Draw diagram.
2. Goal: For any disjoint sequence s.t. $\cup_{j=1}^{\infty} I_{j} \in \mathcal{A_{2}}$, we have $\mu_{0}(\cup_{j=1}^{\infty} I_{j}) = \sum_{j=1}^{\infty} \mu_{0}(I_{j})$. Since the union is in $\mathcal{A_{2}}$, it can be expressed in a finite union of disjoint h-intervals. By considering each h-interval as a trunk, the sequence can be partitioned into **finitely many subsequences**, each is with a trunk and disjoint to others. With finite additivity and relabelling, consider each trunk and corresponding subsequence seperately, WOLG, say $I:=\cup_{j=1}^{\infty} I_{j}:=(a,b]$.  For $I_{j}=(a_{j}, b_{j}]$, discard contained ones to get disjoint intervals.
3. Goal: For $I:=\cup_{j=1}^{\infty} I_{j}:=(a,b]$, show $\mu_{0}(\cup_{j=1}^{\infty} I_{j}) \le \sum_{j=1}^{\infty} \mu_{0}(I_{j})$. It's obvious given monotonicity.
4. Goal: For $I:=\cup_{j=1}^{\infty} I_{j}:=(a,b]$, show $\mu_{0}(\cup_{j=1}^{\infty} I_{j}) \ge \sum_{j=1}^{\infty} \mu_{0}(I_{j})$.
    - First suppose a and b  are finite. Recall that any open set on real line can be expressed as countable union of disjoint open intervals, and a open cover of a compact set on real line (closed) can be reduced to a finite yet valid subcover. 
    - To have open interval and compact set from h-interval, we make use of right-continuity, which gives us that $\forall \epsilon>0, \exists \delta>0, F(a+\delta)-F(a) < \epsilon$, and further more, $\forall j, \exists \delta_{j}, F(b_{j}+\delta_{j})-F(b_{j}) < \epsilon \cdot 2^{-j}$. Now we can adjust the boundary of sets.
    - Extend $I$ from $(a,b]$ into $[a+\delta, b]$, which is compact, and extend $I_{j}$ from $(a_{j}, b_{j}]$ into $(a_{j}, b_{j}+\delta_{j})$. To simpify, we can adjust so that we have $b_{j}+\delta_{j} \in (a_{j+1}, b_{j+1})$. Now that we have an open cover $I \subset \cup_{j=1}^{\infty} (a_{j}, b_{j}+\delta_{j})$, we obtain a finite subcover (with relabelling) $I \subset \cup_{j=1}^{n} (a'_{j}, b'_{j}+\delta_{j})$. Summing up $$\begin{aligned} \mu_{0}((a'_{j}, b'_{j}])&=F(b'_{j})-F(a'_{j}) \\&\ge F(b'_{j}+\delta_{j})-F(a'_{j})-\epsilon \cdot 2^{-j} \\&\ge F(a'_{j+1})-F(a'_{j})-\epsilon \cdot 2^{-j} \end{aligned}$$, we get $$\begin{aligned}\sum_{j=1}^{\infty} \mu_{0}(I_{j}) &\ge \sum_{j=1}^{n} \mu_{0}((a'_{j}, b'_{j}]) \\&\ge F(b'_{n}+\delta_{n})-F(a'_{1})-\epsilon \\&\ge F(b)-F(a+\delta)-\epsilon \\&\ge F(b)-F(a)-2\epsilon \\&=\mu_{0}(I)-2\epsilon\end{aligned}$$.
    - Corner case of a, b being infinite is omitted.

> [!important] Thm. 
> Given F increasing and right-continuous, then
> 1. There's a unique Borel measure $\mu_{F}$ on $\mathbb{R}$ s.t. $\mu_{F}((a,b])=F(b)-F(a)$. To be explicit, $\mu_{F}=\inf \{ \sum_{j=1}^{\infty} \mu_{0}((a_{j}, b_{j}]) : E \subset \cup_{j=1}^{\infty} (a_{j}, b_{j}] \}$.
> 2. If other distribution function G, then $\mu_{F}=\mu_{G}$ iff $F-G$ is constant.
> 3. Conversely, if $\mu$ is a Borel measure on $\mathbb{R}$ that is finite on all bounded Borel sets, and we define $F(x)=\mu((0,x]), x>0$, $F(0)=0$, $F(x)=-\mu((x,0]), x<0$, then F is increasing and right continuous, and $\mu=\mu_F$.

Proof.
1. The constructed $\mu_{0}$ is $\sigma$-finite, since $\mathbb{R}=\cup_{-\infty}^{\infty} (j, j+1]$. Then it follows from the Thm 1.14;
2. $\mu_{F}=\mu_{G} \iff \forall a,b, F(b)-G(b)=F(a)-G(a)$.
3. Take $x>0$ as example. The monotonicity is from the monotonicity of F, and the right-continuous can be get from the continuity. $\mu$ and $\mu_{F}$ is the same on $\mathcal{A_{2}}$, therefore the same on $\mathcal{B_{\mathbb{R}}}$.

Rmk. 
1. The collection $\mathcal{M}_\mu$ of $\mu^{*}$-measurable in Caratheodory's thm is the largest $\sigma$-algebra (in fact strictly larger than $\mathcal{B_\mathbb{R}}$, denoted as $\mathcal{E}$) and gives the domain of the completion $\bar \mu_{F}$ of $\mu_{F}$ (Ex22a), which is called the **Lebesgue-Stieltjes measure** associated to F.
2. When $F(x)=x$, the Lebesgue-Stieltjes measure associated is called the **Lebesgue measure** $m$. The domain is denoted as $\mathcal{L}$.

> Lemma. (1.17) $\mu|_\mathcal{E}(E)=\inf \{ \sum_{j=1}^{\infty} \mu((a_{j}, b_{j})): E \subset \cup_{j=1}^{\infty} (a_{j}, b_{j}) \}$.

Proof. Say the RHS is $\tilde \mu(E)$.
1. Goal: $\mu(E) \le \tilde \mu(E)$. Since $(a, b)=\cup_{n=1}^{\infty} (a, b-\frac{1}{n}]$, $E \subset \cup (a_{j}, b_{j}) \subset \cup \cup (a_{j}, b_{j}- \frac{1}{n})$, therefore the set in left contains the set in right;
2. Goal: $\mu(E) +\epsilon \ge \tilde \mu(E), \forall \epsilon>0$. Use right-continuity. $$\begin{aligned}\exists \{(a_{j}, b_{j}]\}, \mu(E)+\epsilon &\ge \sum \mu_{0}((a_{j}, b_{j}])=\sum  F(b_{j})-F(a_{j}) \\&\ge \sum  F(b_{j}+\delta_{j})-F(a_{j})-\epsilon \cdot 2^{-j} \\&=-\epsilon+\sum  \mu_{0}((a_{j}, b_{j}+\delta_{j}]) \\& \ge -\epsilon+\sum  \mu((a_{j}, b_{j}+\delta_{j})) \\& \ge -\epsilon + \tilde \mu(E) \end{aligned}$$

> [!note] Thm. (1.18) 
> $\mu|_\mathcal{E}(E)=\inf\{ \mu(U):U \supset E, U\ open \}$, and $\mu|_\mathcal{E}(E)=\sup\{ \mu(K):K \subset E, K\ compact \}$. 
> This is so important that it's used as definition in some textbooks.

Proof. Say, to show $\mu(E)=\tilde \mu(E)=\mu'(E)$, with the formula given in lemma 1.17:
1. Goal: $\mu(E) \le \tilde \mu(E)$. This is because $\mu(E) \le \mu(U), \forall U$;
2. Goal: $\mu(E) +\epsilon \ge \tilde \mu(E), \forall \epsilon>0$. Again, $\exists \{(a_{j}, b_{j}]\}, \mu(E)+\epsilon \ge \sum \mu((a_{j}, b_{j})) \ge \mu(\cup (a_{j}, b_{j})) \ge \tilde \mu(E)$.
3. Goal: $\mu(E) \ge \mu'(E)$. The same as 1.
4. Goal: $\mu(E) \le \mu'(E)$. Use the first equality.
    1. If E is bounded:
        1. Subcase: If E is compact. Just take K:=E.
        2. Subcase: If otherwise. Consider $\bar E \setminus E$, then by the first equality, $\exists open\ U \supset \bar E \setminus E, s.t. \mu(\bar E \setminus E)+\epsilon > \mu(U)$. Let $K=\bar E \setminus U$, then it's compact and $K \subset E$. $$\begin{aligned}\mu(K)&=\mu(E)-\mu(E \cap U)=\mu(E)-(\mu(U)-\mu(U \setminus E))\\&=\mu(E)-\mu(U)+\mu(U \setminus E) \\&\ge \mu(E)-\mu(U)+\mu(\bar E \setminus E) \ge \mu(E)-\epsilon \end{aligned}$$
    2. If E is unbounded, partition it as $E_{j}=E \cap (j, j+1]$. By case 1, $\forall \epsilon>0, \exists K_{j}\subset E_{j}, s.t. \mu(K_{j})\ge \mu(E_{j})-\epsilon \cdot 2^{-|j|}$. $\mu'(E) \ge \mu(\cup_{-n}^{n} K_{j}) \ge \mu(\cup_{-n}^{n} E_{j}) -\epsilon$.

> [!note] Thm. (1.19) 
> If $E \subset \mathbb{R}$, then TFAE:
> 1. $E \in \mathcal{E}$;
> 2. $E=V \setminus N_{1}$, where $V \in G_{\delta}, \mu(N_{1})=0$;
> 3. $E=H \cup N_{2}$, where $H \in F_{\sigma}, \mu(N_{2})=0$.

Proof. We know $V, H \in \mathcal{E}$. Since $\mu$ is complete on $\mathcal{E}$, all $N_{1}, N_{2} \in \mathcal{E}$, and $\sigma$-algebra is closed under countable union and intersection, (2) and (3) each imply (1). Now to show the converse,
1. Suppose $\mu(E)<\infty$. Based on thm 1.18, for $j \in \mathbb{N}$, we can have open $U_{j} \supset E$ and compact $K_{j} \subset E$, s.t. $\mu(U_{j})-2^{-j} \le \mu(E) \le \mu(K_{j})+ 2^{-j}$. Let $V:= \cap U_{j}, H:=\cup K_{j}$, then $H \subset E \subset V$. While $\mu(E) \le \mu(V) \le \mu(U_{j}) \le \mu(E)+2^{-j}, \forall j$ and $\mu(E)-2^{-j} \le \mu(K_{j}) \le \mu(H) \le \mu(E)$, we can have $\mu(H)=\mu(E)=\mu(V)<\infty$. $N_{1}:=V \setminus E, N_{2}:=E \setminus H$, then $\mu(N_{1})=\mu(V)-\mu(E)=0, \mu(N_{2})=\mu(E)-\mu(H)=0$.
2. Otherwise. Again, the constructed $\mu_{0}$, is $\sigma$-finite, since $\mathbb{R}=\cup_{-\infty}^{\infty} (j, j+1]$, and therefore $E_{j}:=E \cap (j, j+1], \mu(E_{j})<\infty, E=\cup E_{j}$.
    1. Notice that (1)->(3) implies (1)->(2). So we only need to show the former.
    2. Consider the partition, in which we have $E_{j}=H_{j} \cup N_{j}$. Let $H:=\cup H_{j}, N=\cup N_{j}$. Then $E=\cup (H_{j} \cup N_{j})=H \cup N$.

> [!important] Prop. (1.20)
> If $E \in \mathcal{E}, \mu(E)<\infty$, then $\forall \epsilon>0, \exists A$ that is a finite union of open intervals such that $\mu(E \bigtriangleup A) < \epsilon$.

^47ce71

Proof. Based on thm 1.18, we can have open $U \supset E$ and compact $K \subset E$, s.t. $\mu(U) \le \mu(E) \le \mu(K)+ \epsilon$. Since $U=\cup_{j=1}^{\infty} (a_{j}, b_{j})$ gives a open cover of compact set K, we can have the subcover $A:=\cup_{j=1}^{n} (a_{j}, b_{j}) \supset K$. Then $\mu(E)-\epsilon \le \mu(K) \le \mu(A) \le \mu(U) \le \mu(E)+\epsilon$ and $\mu(E)-\epsilon \le \mu(K) \le \mu(A \cap E) \le \mu(U) \le \mu(E)+\epsilon$. Then $|\mu(E)-\mu(A)| \le \epsilon, |\mu(E)-\mu(A \cap E)| \le \epsilon$, which means $$\begin{aligned}&\mu(E \bigtriangleup A)\\&\le \mu(E \setminus A)+\mu(A \setminus E)\\&=\mu(A)-\mu(E)+\mu(E)-\mu(A \cap E)+\mu(E)-\mu(A \cap E) \\&\le 3\epsilon\end{aligned}$$.

> Prop. For any $E \in \mathcal{L}$, we have $E+s, rE \in \mathcal{L}$, and $\mu(E+s)=\mu(E), \mu(rE)=|r|\mu(E)$. 

Proof. They agree on the algebra, and by uniqueness of thm 1.14 (3), they also agree on $\mathcal{B_{\mathbb{R}}}$. Further more, since Lebesgue measure zero is preserved by translations and diluations, by thm 1.19, they agree on $\mathcal{L}$. #TODO 

E.g. (**Cantor set** C) Repeadly remove the middle thirds open interval, starting from $[0,1]$. It's compact, totally disconnected, no where dense, no isolated points, $m(C)=0$, and $0, 1 \in C$. Moreover, it's uncountable and with the cardinality of $\mathbb{R}$. This can be proved by constructing $f:C \to [0,1]$ and let it onto. $f: \sum a_{j} 3^{-j} \mapsto \sum \frac{a_{j}}{2}2^{-j}$.

> [!note] Thm. 
> If $F \subset \mathbb{R}$, s.t. $\forall G \subset F, G \in \mathcal{L}$, then $m(F)=0$.

Cor. (**Existence of non-measurable set**) For F that $m(F)>0$, $\exists G \subset F, G \notin \mathcal{L}$.

> [!note] Def. (**Coset**) 
> A coset of $\mathbb{Q}$ in additive group $(\mathbb{R}, +)$ is $\mathbb{Q}+x$, where $x \in \mathbb{R}$.

Proof of Thm.
1. Let E be the set that contains exactly one point from each coset. The existence of E is given by the axiom of choice.
2. Claim: $\forall r_{1}, r_{2} \in \mathbb{Q}, r_{1} \ne r_{2} \to (E+r_{1}) \cap (E+r_{2})=\emptyset$. Otherwise, that means $e_{1}, e_{2}\in E, e_{1}\ne e_{2}, e_{1}-e_{2}\in \mathbb{Q}$, contradicts with the "exactly one point".
3. Claim: $\mathbb{R} = \cup_{r \in \mathbb{Q}} (E+r)$. For any $x \in \mathbb{R}$, there's a coset $\mathbb{Q}+x$, in which E contains exactly an element $q+x$. Then $x=q+x+(-q)$ will be contained in $E+(-q)$, which is when $r=-q$, in the union.
4. Now $F=F \cap \mathbb{R}=\cup_{r \in \mathbb{Q}} (F \cap (E+r))=\cup F_{r}$, it suffices to show $m(F_{r})=0$. Given that $m(F_{r})=\sup\{ m(K): compact\ K \subset F_{r} \}$, this holds iff $\forall compact\ K\subset F_{r},m(K)=0$. We're going to use the fact that K is bounded.
5. Suppose not, i.e. there's a K, s.t. $m(K)>0$. Due to to the same reason as 2, we have $\forall r_{1}, r_{2} \in \mathbb{Q}, r_{1} \ne r_{2} \to (K+r_{1}) \cap (K+r_{2}) = \emptyset$. Note that it's still bounded after translation. Further more, let's bound the translation scale. Let $H=\cup_{r \in \mathbb{Q} \cap [0,1]} (K+r)$, which is a disjoint union of bounded set and should be bounded as a whole (within the union of $(-M_{r}, M_{r})$). Yet since every summand in this $\sigma$-additivity (infinite) summation, $m(K+r)>0$, we have $m(H)=\infty$, contradict.

> Ex. (Ch1 q30) If $E \in \mathcal{L}, m(E)<0$, then $\forall \alpha<1, \exists open\ interval\ I$, s.t. $m(E \cap I) > \alpha m(I)$.

> [!important] Thm. (**Steinhams' thm**) 
> If $E \in \mathcal{L}, m(E)<0$, the set $E-E=\{x-y: x,y \in E\}$ contains an interval centered at 0.

Proof. 
1. Based on ex.ch1q30, let $F:=E \cap I=(a,b)$, then $F-F=(E-E) \cap (I-I)$, therefore $F-F \subset E-E$. To show $(-\delta, \delta) \subset E-E$, it suffices to show that $\forall x, |x|<\delta, (F+x) \cap F \ne \emptyset$. 
2. Suppose not, then $2m(F) > 2 \alpha m(I)$ according to ex.ch1q30. OTAH, $2 m(F)=m((F+x)\cup F) \le m((I+x) \cup I)=b-a+|x|=b-a+\delta$, if $|x| < m(I)$. But if we let $\delta=(2\alpha-1)(b-a)$, then $2m(F) \le 2 \alpha(b-a)$, contradicts.

# Ch2 Integration
## 2.1 Measurable function
Motiv. $f^{-1}(E)=\{ x \in X:f(x) \in E \}$ preserves unions, intersections, and complements on E. Thus $f^{-1}(\mathcal{B})$ and $\mathcal{H}=\{ E \in \mathcal{B} : f^{-1}(E) \in \mathcal{A} \}$ are $\sigma$-algebra.

> [!note] Def. (**Measurable function**) 
> Measurable spaces $(X, \mathcal{A}), (Y, \mathcal{B})$, we say $f:X \to Y$ is $(\mathcal{A,B})$-measurable if $\mathcal{f^{-1}(\mathcal{B}) \subset A}$, or equivalently, $\mathcal{H} \supset \mathcal{B}$.

Rmk. 
1. Random variables are special cases of measurable function.
2. Composition of measurable mappings are measurable.
3. For $E \in \mathcal{A}$, the indicator function $\mathbb{1}_{E}$ or $\mathcal{X}_{E}$ is $\mathcal{A}$-measurable.

> Prop. (2.1) $f:X \to Y$ is $(\mathcal{A,B})$-measurable iff $\mathcal{H} \supset \mathcal{B_{0}}$, where $\mathcal{M}( B_{0})=\mathcal{B}$.

Proof. $\mathcal{H}$ is a $\sigma$-algebra, then $\mathcal{H \supset B_{0}} \implies \mathcal{H \supset \mathcal{M}( B_{0})=B}$ by prop1.1 ([[Real Analysis#^db1186]]).

> Cor. Let X, Y be metric or topological spaces, then every continuous $f:X \to Y$ is $(\mathcal{B}_{X},  \mathcal{B}_{Y} )$-measuable.

Proof. Recall that $f:X \to Y$ is continuous on X iff for any open set U in Y, $f^{-1}(U)$ is open in X. By prop 2.1, it follows.

> [!important] Thm. (2.3)
> Based on prop 1.2 and 2.1, T.F.A.E:
> 1. $f:X \to \mathbb{R}$ is $\mathcal{A}$-measuable.
> 2. $\{(a, \infty): \forall a \in \mathbb{R}\} \subset \mathcal{H}$;
> 3. $\{[a, \infty): \forall a \in \mathbb{R}\} \subset \mathcal{H}$;
> 4. $\{(-\infty, a): \forall a \in \mathbb{R}\} \subset \mathcal{H}$;
> 5. $\{(-\infty, a]: \forall a \in \mathbb{R}\} \subset \mathcal{H}$;
> 6. (ch2q4) $\{(r, \infty): \forall r \in \mathbb{Q}\} \subset \mathcal{H}$;
> 7. If $f: X \to \bar{ \mathbb{R}}$, change the above intervals as including infinity.

> Ex. (ch2q1) $f:X \to \bar{\mathbb{R}}$ is measurable iff $f^{-1}(\{-\infty\}), f^{-1}(\{+\infty\}) \in \mathcal{A}$ and $f$ is measurable on $f^{-1}(\mathbb{R})$.

> Ex. (ch2q3) $\{f_{n}\}$ measurable, then $\{x: \lim f_{n}(x) \text{ exists}\} \in \mathcal{M}$.

> [!note] Def. (**Measurable on subset of X**)
> $f$ is measurable on $E \in \mathcal{M}$, if $f|_{E}$ is $\mathcal{M}_{E}$-measurable, i.e. $\forall B \in \mathcal{B}_{ \mathbb{R}}, f^{-1}(B) \cap E \in \mathcal{M}$.

> [!important] Prop. (2.4)
> Let $(X, \mathcal{M})$ and $(Y_{\alpha}, \mathcal{N}_{\alpha})$ be measurable spaces, and $Y:=\prod_{\alpha} Y_{\alpha}, \mathcal{N}:=\otimes \mathcal{N}_{\alpha}$, and $\pi_\alpha$ the coordinate maps. Then $f:X \to Y$ is measurable iff $f_{\alpha}:=\pi_{\alpha} \circ f$ is $(\mathcal{M, N_\alpha})$-measurable for all $\alpha$.

> Cor. $f: X \to \mathbb{C}$ is measurable iff $Re f, Im f$ are measurable.

> [!important] Thm. (2.6)
> If $f, g: X \to \mathbb{C}$ are $\mathcal{A}$-measurable, then $f+g, fg$ are $\mathcal{A}$-measurable.

Proof. Work on level sets. Consider $fg=\frac{1}{2}((f+g)^{2} -f^{2} -g^{2})$.

> [!note] Def. 
> $\mathcal{B}_{\bar{\mathbb{R}}}=\{ E \subset \bar{\mathbb{R}} : E \cap \mathbb{R} \subset \mathcal{B}_{\mathbb{R}} \}$. 

> [!important] Prop. (2.7, 2.8)
> In $\bar{\mathbb{R}}$, $\liminf, \limsup$ exist. Let $\{f_{j}\}$ be a sequence of $\mathcal{A}$-measurable function, then $g_{1}=\sup f_{j}, g_{2}=\inf f_{j}, g_{3}=\limsup f_{j}, g_{4}=\liminf g_{j}$ are measurable. Thus, if $f,g$ are measurable, then $\max(f,g), \min(f,g)$ are measurable.

^bfc106

Proof. $\limsup_{j} = \inf_{k} \sup_{j>k}$.

Rmk. We prefer to work on $\bar{\mathbb{R}}$ from now on since the limsup and liminf always exists.

> [!note] Def. (Decomposition of real-valued func)
> $f^{+}:=\max (f(x),0),f^{-}:=\max (-f(x),0)$, then $f=f^{+}-f^{-}, |f|=f^{+}+f^{-}$. By Prop. 2.7, if f is measurable, so are $f^{+}, f^{-}$.

> [!note] Def. (Polar decomposition of complex-valued func)
> $f=(sgn \circ f) |f|$, where $sgn (z)=\frac{z}{|z|}\mathbb{1}(z \ne 0)$. If f is measurable, so are $|f|, sgn \circ f$.

Rmk. Note that $|sgn (z)|=1$. Conversely, to decompose absolute value of complex number, consider $|z|=\frac{z \cdot \bar {z}}{|z|}=\frac{1}{sgn(z)} \cdot z$.

Proof. Note that the map $z \mapsto |z|$ is continuous except at the origin. Thus if $U \subset \mathbb{C}$ is open, $sgn^{-1}(U) \setminus \{0\}$ is open. By prop 2.1, $sgn$ is measurable. Therefore $|f|=| \cdot | \circ f, sgn f=sgn \circ f$ are also measurable.

> [!note] Def. (**Simple function**)
> A finite linear combination of $\mathbb{1}_{E}$ of sets in A as the E, i.e. $$f=\sum_{j=1}^{m} a_{j} \mathbb{1}_{E_{j}}, E_{j}\in \mathcal{A}$$

> [!important] Prop. (Standard representation)
> Any simply function can be written so that disjoint $\cup E_{j}=X$.

Proof. Simply function takes finite many values, say $z_{1}, z_{2}, \dots z_{n}$. Let $E_{j}:=f^{-1}(\{z_{j}\})$, which is disjoint. Let $E_{0}=X \setminus (\cup E_{j})$ and $a_{0}=0$, then $f(x)=\sum_{j=1}^{n} z_{j} \mathbb{1}_{E_{j}}(x)$ gives the existence of standard representation.

> [!important] Thm. (2.10)
> 1. If $f$ is $\mathcal{A}$-measurable, $f:X\to [0,\infty]$, then $\exists simple\ \{ \phi_{j} \}$ s.t. $\phi_{j} \nearrow$, $\forall x, \phi_{j}(x) \to f(x)$, and $\phi_{j} \to  f$ uniformly on any set on which f is bounded;
> 2. If $f$ is $\mathcal{A}$-measurable, $f:X\to \mathbb{C}$, then $\exists simple\ \{ \phi_{j} \}$ s.t. $|\phi_{j}| \nearrow$, $\forall x, \phi_{j}(x) \to f(x)$, and $\phi_{j} \to  f$ uniformly on any set on which f is bounded. 

^d33331

Proof. 
1. Consider n as a parameter to control a partition over the codomain. For any n, define **Dyatic intervals** $I_{k,n}:=[k 2^{-n}, (k+1)2^{-n})$ for $k=0 \dots 2^{2n}$, and also let $F_{n}:=[2^{n}, \infty]$. Then $[0,\infty]=(\cup_{k} I_{k,n})\cup F_{n}$.
2. Define an approximation from below of $f$ on each intervals, i.e. $E_{k,n}:=f^{-1}(I_{k,n}), \phi_{n}(E_{k,n}):=k2^{-n}$. The same for $F_{n}$. Then in summary, $$\phi_{n}=\sum_{k=1}^{2^{2n}-1} k2^{-n} \mathcal{X}_{E_{k,n}}+2^{n} \mathcal{X}_{F_{n}} $$
3. Claim $\phi_{n} \le f$.
4. Claim $\phi_{n} \le \phi_{n+1}$.
5. Claim $\forall x \in [0,\infty] \setminus F_{n}, 0 \le f(x)-\phi_{n}(x) \le 2^{-n}$.
6. Claim $\forall x, \phi_{n}(x) \to f(x)$.
7. Claim $\forall A \subset X, s.t. f(A)\subset [0, \infty), \sup_{x \in A} |f-\phi_{n}| \to 0$.

> [!important] Prop. (2.11)
> Each of the following is valid iff $\mu$ is complete:
> 1. If $f$ is measurable and $f=g$ a.e., then $g$ is measurable;
> 2. If $f_{n}$ is measurable and $f_{n}(x) \to f(x)$ a.e., then $f$ is measurable.

Proof.
1. (1<=) Note that $\mu(\{x: f(x) \ne g(x\})=0$. $\forall B \in \mathcal{B}_{\mathbb{R}}$, $g^{-1}(B)=\{x:g(x)\in B\}$, i.e., $( \{x:f(x)\in B\} \cap \{f=g\} )\cup( \{x:g(x)\in B\} \cap \{f \ne g\}  ) \in \mathcal{A}$;
2. (2<=) Note that $E:=\{ x: f_{n}(x) \to f(x) \text{ as } n \to \infty \}, \mu(E^{c})=0$. Then $f|_{E}$ is measurable given prop2.7 ([[Real Analysis#^bfc106]]), thus $f|_{E}^{-1}(B) \cap E \in \mathcal{A}$. Apply the same trick of partition.
3. (1=>) For any null set E and its any subset F, construct $f:=\mathcal{X}_{E}, g:=2\mathcal{X}_{F}$, then $\mu(\{f \ne g\})=\mu(E)=0$. Now $g$ is measurable, then $F:=g^{-1}(\{2\}) \in \mathcal{A}$.
4. (2=>) For any null set E and its any subset F, construct $f_{n}:=0, f:=\mathcal{X}_{F}$, then $\mu(\{f_{n}(x) \to f(x)\}^{c})=\mu(F)=0$. Now $g$ is measurable, then $F:=g^{-1}(\{1\}) \in \mathcal{A}$.
## 2.2 Integration of non-negative func.
> [!note] Def. (Integral)
> 1. $L^{+}:=\{ \text{all } \mathcal{A}-\text{measurable } f: X \to [0,\infty] \}$;
> 2. For a simple func $\phi(x)=\sum_{j=1}^{n} a_{j} \mathbb{1}_{E_{j}}(x)$ with standard representation, define $\int_{X} \phi \ \mathrm{d} \mu:=\sum_{j=1}^{n} a_{j}\mu(E_{j})$; (Here $0 \cdot \infty=0$)
> 3. $\int_{A} \phi := \int_{X} \phi \mathcal{X}_{A} \ \mathrm{d} \mu$;
> 4. $\int_{X} f \ \mathrm{d} \mu:=\sup_{\phi} \{ \int_{X} \phi \ \mathrm{d} \mu : 0 \le \phi \le f, simple\ \phi \}$.

> [!important] Prop. (2.13)
> For simple functions $\phi, \varphi$:
> 1. If $c>0$, then $\int c \phi \ \mathrm{d} \mu=c \int \phi \ \mathrm{d}\mu$;
> 2. $\int (\phi + \varphi) = \int \phi + \int \varphi$;
> 3. If $\varphi \le \phi$, then $\int \varphi \le \int \phi$;
> 4. $v: A \mapsto \int_{A} \phi \ \mathrm{d} \mu$ is a measure on $\mathcal{A}$.

Proof.
1. 3. Can be easily shown and easily extended to general $L^{+}$ function case.
2. In standard form, $\phi=\sum_{j=1}^{n} a_{j} \mathbb{1}_{E_{j}},\varphi=\sum_{k=1}^{m} b_{k} \mathbb{1}_{F_{k}}$. Since $E_{j}=\cup_{k} (E_{j} \cap F_{k})$, we can have $\phi=\sum_{j=1}^{n} a_{j} \sum_{k} \mathbb{1}_{E_{j} \cap F_{k}}$, and similarly for $\varphi$. Then $$\begin{aligned}\int (\phi+\varphi)=\int (\sum_{j,k} (a_{j}+b_{k}) \mathcal{X}_{E_{j} \cap F_{k}})\\=\sum_{j,k} (a_{j}+b_{k}) \mu(E_{j} \cap F_{k})=\int \phi+\int \varphi\end{aligned}$$.
4. For disjoint $\{A_{k}\}$, $$\begin{aligned}v(\cup_{k=1}^{\infty} A_{k})=\int_{\cup A_{k}} \phi=\sum_{j=1}^{n} a_{j} \mu(\cup A_{k})=\sum_{j=1}^{n} a_{j} \sum_{k=1}^{\infty}\mu(A_{k})\\=\sum_{k=1}^{\infty} (\sum_{j=1}^{n} a_{j} \mu(A_{k}))=\sum_{k=1}^{\infty} \int_{A_{k}} \phi =\sum_{k=1}^{\infty}v(A_{k})\end{aligned}$$.

> [!important] Thm. Monotone convergence thm (MCT)
> If $f_{n} \in L^{+}, \{ f_{n}\} \nearrow$ and $\forall x, f_{n}(x) \to f(x)$, then $\int f=\lim_{n \to \infty} \int f_{n}$.

Rmk. This relex the computation of $\int f$ from supremum of all simple func to a monotone sequence of func, which exists by thm 2.10 ([[Real Analysis#^d33331]]).

Proof. 
1. Note that $f(x)=\sup_{n} f_{n}(x)$. For any n, $\int f_{n}\le \int f$, and $\{ \int f_{n} \} \nearrow$ by prop2.13 (4), thus $\lim \int f_{n} \le \int f$. To the other direction, try to take a fraction of RHS.
2. For simple func $\phi, s.t., 0 \le \phi \le f$, for any $\alpha \in (0,1)$, let $E_{n}=\{ x: f_{n}(x) \ge \alpha \phi(x) \}$, we claim that (a) $X=\cup E_{n}$; (b) $E_{n} \nearrow$; (c) $v_{\phi}(X):=\int \phi=\lim \int_{E_{n}} \phi =: \lim v_{\phi}(E_{n})$.
3. (c) is the continuity from below property of measure.
4. Then, $\lim_{n} \int f_{n} \ge \lim \int_{E_{n}} f_{n} \ge \lim \int_{E_{n}} \alpha \phi=\alpha \int \phi$. By taking limit on $\alpha$, we get $\lim_{n} \int f_{n} \ge \int  \phi$.
5. Take supremum on $\phi$, $\lim_{n} \int f_{n} \ge \sup \{ \int_{X} \phi \ \mathrm{d} \mu \}=:\int_{X} f \ \mathrm{d} \mu$.

> Cor. (2.15) $\{f_{n}\}\subset L^{+}$, then $\int f :=\int \sum_{n} f_{n} =\sum_{n} \int f_{n}$. ^12cbd9

Proof. 
1. When there's only two, use prop 2.10 to get two increasing sequence of each, then use MCT to express w/ simply func, then use prop 2.13(2), then use MCT to transform simple func back to f.
2. Induction on n, then take limit with MCT on partial sum sequence to show infinite sum.

> Cor. (2.16) If $f \in L^{+}$, then $\int f=0$ iff $f=0$ a.e.

> Cor. (Null set contribute nothing) If $f \in L^{+}, \mu(E)=0$, then $\int_{E} f=0$.

> [!important] (Fatou's lemma, equivalent to MCT)
> If $\{ f_{n} \} \subset L^{+}$, then $\int \liminf_{n} f_{n} \le \liminf_{n} \int f_{n}$.

Proof. Recall $\liminf_{n} a_{n}:= \lim_{n} (\inf_{k \ge n} a_{k})$. Then $\forall n, \forall j \ge n, \inf_{k\ge n} f_{k} \le f_{j}$, thus $\int \inf_{k\ge n} f_{k} \le \int f_{j}$. Take infimum on j, we have $\int \inf_{k \ge n} \le \inf_{j \ge n} \int f_{j}$. By MCT, $\int \liminf_{n} f_{n} = \lim_{n} \int \inf_{k \ge n} f_{k} \le  \lim_{n} \inf_{j \ge n} \int f_{j}=\liminf_{n} \int f_{n}$.

Rmk. (Show MCT using Fatou's lemma) If $f_{n} \in L^{+}, \{ f_{n}\} \nearrow$ and $\forall x, f_{n}(x) \to f(x)$, then apply Fatou's lemma to $\{ f_{n} \}$, we get $\int f = \int \liminf f_{n} \le \liminf_{n} \int f_{n}$. OTAH, apply Fatou's lemma to $\{f-f_{n}\}$, we get $0=\int \liminf (f-f_{n}) \le \liminf_{n} \int (f-f_{n})=\int f - \limsup_{n} \int f_{n}$, i.e. $\limsup\int  f_{n} \le \int f$. Thus $\{ \int  f_{n} \}_{n}$ converges to $\int f$.

> Cor. If $\{ f_{n} \} \subset L^{+}, f \in L^{+}$, and $f_{n}(x) \to f(x)$ a.e., then $\int f \le \liminf \int f_{n}$. If further more, $f_{n} \le f$, then $\int f = \lim \int f_{n}$. (Shown by apply the lemma twice)

> Ex. (ch2q13) If $\{ f_{n} \} \subset L^{+}$, $f_{n}(x) \to f(x)$ pointwise, and $\int f=\lim \int f_{n}<\infty$, then $\forall E \in \mathcal{M}, \int_{E} f=\lim \int_{E} f_{n}$. This need not be true if $\int f=\lim \int f_{n}=\infty$.

Proof. 
1. By Fatou's lemma, $\int_{E} f=\int_{E} \liminf f_{n} \le \liminf \int_{E} f_{n}$.
2. OTAH, note that we can also apply Fatou's lemma on $E^{c}$ since $\int_{E^{c}} f=\int f-\int_{E} f$: $\int_{E^{c}} \liminf f_{n} \le \liminf \int_{E^{c}} f_{n}$, then $LHS=\int f-\int_{E}f, RHS=\int f-\limsup \int_{E} f_{n}$, which gives $\int_{E}f \ge \limsup \int_{E} f_{n}$, thus $\{ \int_{E}  f_{n} \}_{n}$ converges to $\int_{E} f$.
3. Counter example on $\int f=\lim \int f_{n}=\infty$: consider $f_{n}:=\mathcal{X}_{[n, n+1)}+\mathcal{X}_{(-\infty, 0)}$, then $f:=\mathcal{X}_{(-\infty, 0)}; \forall x, f_{n}(x) \to f(x)$. Then $\int f=\lim \int f_{n}=\infty$, yet for $E=[0,\infty), \int_{E} f=0, \lim \int_{E} f_{n}=1$.

> [!important] Prop. (2.20) 
> If $f \in L^{+}, \int f < \infty$, then $H:=\{ x: f(x)=\infty \}$ is a null set and $F:=\{ x: f(x)>0 \}$ is $\sigma-$finite.

^49150d

Proof.
1. H is measurable. Suppose H is not null set, then $\int f \ge \int f \mathcal{X}_{H}=\infty   \cdot m(H)=\infty$, contradict.
2. $F_{n}:=\{ x: f(x) > \frac{1}{n} \}$ is measurable and $F = \cup F_{n}$. Suppose $\mu(F_{n})=\infty$, then again, $\int f \ge \int f \mathcal{X}_{F_{n}} \ge \frac{1}{n}   \cdot m(F_{n})=\infty$, contradict.

> Cor. If $f \in L^{+}, \int f<\infty$, then $\forall  \epsilon>0, \exists E \in \mathcal{A}$, s.t. $\mu(E)<\infty, \int_{E} f > (\int f )- \epsilon$.
## 2.3 Integration of complex func
> [!note] Def. (**Integral**)
> If either $\int f^{+}, \int f^{-} < \infty$, the integral is defined as $\int f:=\int f^{+} - \int f^{-}$.

> [!note] Def. (Integrable)
> $f: X \to \mathbb{C}$ is integrable if $\int |f| < \infty$. The set (vector space) of integrable function is called $L^{1}(X, \mu)$.

> [!important] Thm. 
> If $f,g \in L^{1}$, then
> 1. (Linearity) $\int (\alpha f+ \beta g) = \alpha \int f + \beta \int g$;
> 2. $|f| \le |g|\ a.e. \implies \int |f| \le \int |g|$;
> 3. $\forall A \in \mathcal{M}, \lambda_{f}: A \mapsto \int_{A} |f| \ \mathrm{d} \mu$ is a measure.

> [!important] Prop. (2.22)
> $|\int f| \le \int |f|$.

Proof.
1. In the case of $f:X \to \mathbb{R}$, $|\int f| = | \int f^{+} - \int f^{-} | \le |\int f^{+} + |\int f^{-}|=\int |f|$.
2. In the case of $f:X \to \mathbb{C}$, use polar decomposition. $|\int f|=\frac{1}{sgn (\int f)} (\int f):=\int \alpha f$, where $\alpha=\frac{1}{sgn (\int f)}, |\alpha|=1$. Since $|\int f| \in \bar{\mathbb{R}}$, we know $\int \alpha f=Re(\int \alpha f)=\int Re(\alpha f) \le \int |\alpha f|=\int |\alpha| |f|=\int |f|$.

> Cor. (Null set contributes nothing) If $f \in L^{1}, \mu(E)=0$, then $\int_{E} f=0$. Follows from $|\int_{E} f| \le \int_{E} |f|=0$.

> Prop. (2.23) 
> 1. If $f \in L^{1}$, then $F:=\{ x: f(x) \ne 0 \}$ is $\sigma-$finite.
> 2. $\left(\forall E \in \mathcal{A}, \int_{E} f=\int_{E} g\right)\iff \int |f-g|=0 \iff f=g\ a.e.$

Rmk. For the purposes of integration, it makes no difference if we alter functions on null sets. Thus we can treat $\bar{\mathbb{R}}$-valued function that are finite a.e. as real-valued funtions. It's more convenient to redefine $L^{1}$ as the equivalence classes of a.e.-defined integrable func, where f and g are considered equivalent iff $f=g$ a.e. This new vector space with distance $\rho(f,g)=\int |f-g|$ is a metric space.

Proof. 
1. Follows from prop 2.20([[Real Analysis#^49150d]]);
2. The second equivalence follows from prop 2.16;
3. (<=) $|\int_{E} f-\int_{E} g| \le \mathcal{X}_{E} |f-g|=0$;
4. (=>) It suffices to show under real-valued. $\forall E \in \mathcal{M}, \int_{E} (f-g)=0$. Suppose $f=g$ not a.e., then one of $(f-g)^{+}, (f-g)^{-}$ is nonzero on a set of positive measure. Let $E$ be that set, then $\int_{E} (f-g) \ne 0$. Contradict.

> [!important] Thm. (Dominated convergence thm, DCT)
> $\{ f_{n} \} \subset L^{1} s.t.$
> 1. $f_{n}(x) \to f(x)$ a.e.;
> 2. $\exists g \in L^{1}, g:X \to \mathbb{ R}, s.t., \forall n, |f_{n}| \le g$ a.e.;
> 
> Then $\int f=\lim \int f_{n}$.

Proof.
1. $\int |f| \le \int g < \infty$, thus $f \in L^{1}$;
2. Case1: $f_{n}:X \to \mathbb{\bar R}$. Since $|f_{n}| \le g$, we have $f_{n}+g, g-f_{n}\ge 0$ a.e. Applying Fatou's lemma on them gives two inequality: $\int f \le \liminf \int f_{n}$ and $\int f \ge \limsup f_{n}$.
3. Case2: $f_{n}:X \to \mathbb{C}$. Trivial.

> Ex. (2.3.20, **Generalized DCT**) If $f_{n}, g_{n}, f,g \in L^{1}$, $f_{n}\to f$ a.e., $g_{n}\to g$ a.e., $|f_{n}| \le g_{n}$, and $\int g_{n} \to \int g$, then $\int f_{n}\to \int f$. Proof is similar to DCT.

> Ex. (2.3.21) If $f_{n},f \in L^{1}, f_{n} \overset{a.e.}{\to} f$, then $\int |f_{n}-f| \to 0$ iff $\int |f_{n}| \to \int |f|$. Based on ex2.3.20.

> Thm. (2.25, **Exchange summation and integral**) $\{ f_{n} \} \subset L^{1}, s.t. \sum \int |f_{j}|<\infty$, then $\exists f \in L^{1}, \sum f_{j} \to f$ a.e. and $\int f=\sum \int f_{j}$.

Proof. With cor2.15([[Real Analysis#^12cbd9]]), $g:=\sum |f_{j}|, \int g = \sum \int |f_{j}| <\infty$, so $g \in L^{1}$. With prop2.20([[Real Analysis#^49150d]]), $g$ is finite a.e., thus the series $\sum f_{j}(x)$ converges a.e. with bound $g$. Apply DCT.

> Thm. (2.26, **Simple functions are dense in $L^{1}$**) 
> 1. Let $f \in L^{1}, \forall \epsilon>0, \exists simple:=\sum a_{j} \mathcal{X}_{E_{j}} \ \phi, s.t. ||f-\phi||_{1} \le \epsilon$;
> 2. If $\mu$ is a L-S measure on $\mathbb{R}$, then the sets $E_{j}$ can be taken to be finite unions of open intervals;
> 3. Moreover, there is a continuous func g that vanishes outside a bounded interval such that $\int |f-g| \ \mathrm{d} \mu<\epsilon$.

Proof. 
1. With prop2.10([[Real Analysis#^d33331]]),  $\exists simple\ \{ \phi_{j} \}$ s.t. $|\phi_{j}| \nearrow$, $\forall x, \phi_{j}(x) \to f(x)$. Then $|f-\phi_{n}| \le |f|+|\phi_{n}| \le 2|f|$, thus $f-\phi_{n} \in L^{1}$. By DCT, $\lim \int (f-\phi_{n})=\int 0=0$.
2. If $E, F \in \mathcal{M}$, then $\mu(E \bigtriangleup F) = \int |\mathcal{X}_{E} - \mathcal{X}_{F}|$. With prop1.20([[Real Analysis#^47ce71]]), that means when $\mu(E_{j})<\infty$, we can approximate $\mathcal{X}_{E_{j}}$ with a finite sum of functions $\mathcal{X}_{I_{k}}$, where $I_{k}$'s are open intervals, arbitrarily close in the $L^{1}$ metric. In this case, $\mu(E_{j})=|a_{j}|^{-1} \int_{E_{j}} |\phi_{n}| \le \infty$. The $\epsilon_{j}$'s for each $E_{j}$ can be chosen as $2^{-j}$.
3. We can approximate $\mathcal{X}_{I_{k}}$ with continuous func in the $L^{1}$ metric. #TODO 

Thm. (**Exchange differentiation and integral**) #NotCovered 

> [!note] Def. (Riemann sum)
> Let $\{x_{0}, x_{1}, x_{2} \dots\}, a = x_{0} <x_{1}\dots <x_{n}=b$ be a partition, with mesh $||P||:=\max_{j=1}^{n} (x_{j}-x_{j-1})$. Define upperbound func $U_{P}=\sum_{j=1}^{n} \sup_{x \in I_{j}} f \cdot \mathcal{X}_{I_{j}}$, where $I_{j}:=[x_{j-1}, x_{j})$. Then the **Riemann sum** is $\sum_{j=1}^{n} \sup_{x \in I_{j}} f \cdot (x_{j}-x_{j-1})=\int_{[a,b]} U_{P} \ \mathrm{d} m=:U(f,P)$, and similarly $L(f, P)$.

> [!note] Def. (Riemann integral)
> $f$ is **Riemann integrable** if for any sequence of partition $P_{1} \subset P_{2} \dots$ with $\lim_{n} ||P_{n}||=0$, we have $L(f):= \lim L(f, P_{n}) = \lim U(f, P_{n}) =: U(f)$. And $\int_{a}^{b} f \ \mathrm{d}x :=L(f)$.

> [!important] Thm. (Riemann integrable)
> Let $f:[a,b] \to \mathbb{R}$ be bounded, $D_{f}:=\{ x: f \text{ is discontinuous at } x \}$, then 
> 1. If f is Riemann integrable, then it is Lebesgue measurable;
> 2. f is Riemann integrable iff $m(D_{f})=0$.

Proof.
1. f is Riemann integrable iff $\forall \{P_{n}\}, \lim_{n} ||P_{n}||=0 \to U(f)=L(f)$.
2. Note that $L_{P_{1}} \le L_{P_{2}} \dots \le f \le \dots \le U_{P_{2}} \le U_{P_{1}}$. Let $L(x)=\lim_{n} L_{P_{n}} (x)$ be the pointwise limit due to monotone sequence. Then $L \le f \le U$. Since $|L| \le |U| \le \sup|f(x)|<\infty$, by DCT, $\int L= \int \lim L_{P_{n}} = \lim \int L_{P_{n}} = \lim L(f, P_{n}) =L(f)$. Therefore, Riemann integrable iff $L(f)=U(f)=\int f$  iff $\int L  =\int U$ iff $L=U$ a.e. 
4. If Riemann integrable, then $L=f$ a.e since $m(L \ne f) \le m(L \ne U)=0$. Then f is measurable according to prop2.11.
5. Define $\omega_{f}(A):=\sup_{x \in A} f(x)- \inf_{x \in A} f(x)$ the **oscillation** of f on A. $\lim_{\delta \to 0} \omega_{f}(x_{0}-\delta, x_{0}+\delta) := \lim G(\delta) := \Omega_{f}^{(x_{0})}$, where $G(\delta) \searrow\ as\ \delta \to 0$. We claim that $f$ is continuous at $x_{0}$ iff $\Omega_{f}^{(x_{0})}=0$. 
6. Let $x \in [a,b] \setminus (\cup_{n=1}^{\infty} P_{n})$, define $I_{n}(x):=(x_{j-1}, x_{j})$ s.t. $x \in I_{n}(x)$. Note that $m(\cup_{n=1}^{\infty} P_{n})=0$. Then $\Omega_{f}^{(x_{0})}=\lim_{n} \omega_{f}(I_{n}(x))=\lim (U_{P_{n}}(x)-L_{P_{n}}(x))=U(x)-L(x)$. Then $D_{f}=\{x: \Omega_{f}^{(x_{0})} \ne 0\}=\{U \ne L\}$.

E.g. The Cantor set $\mathcal{C}$. Then both $\mathcal{X}_{\mathbb{Q}}$ and $\mathcal{X_{C}}$ are Riemann integrable since both are discontinuous everywhere and $\int_{[0,1]} \mathcal{X}_{\mathbb{Q}}=0=\mathcal{X_{C}}$.

> Ex (Ch2q26). Show that if $f \in L^{1}(\mathbb{R}, \mathcal{L}, m), F(x)=\int_{-\infty}^{x} f(t) \ \mathrm{d}t$, then F is continuous on $\mathbb{R}$.

Proof. F cts on $\mathbb{R}$ iff $\forall \{x_{n}\} \subset \mathbb{R}$, #TODO 

> [!note] Def. (Gamma function $\Gamma$)
> $$\Gamma(z):=\int_{(0,\infty)} t^{z-1} e^{-t} \ \mathrm{d} t,$$ where $z \in \mathbb{C}, Re(z)>0, t^{z-1}:=\exp[(z-1)\log t]$.

Rmk.
1. $f_{z}(t):=t^{z-1} e^{-t}, |f_z(t)| \le |t^{z-1}|=t^{Re(z)-1}$ and $\forall t\ge 1, |f_{z}(t)| \le C_{z} \exp(\frac{-t}{2})$. For $a>-1 , \int_{(0,1)} t^{a}\ \mathrm{d} t<\infty$; also $\int_{1}^{\infty} \exp(\frac{-t}{2})<\infty$. Thus $f_{z} \in L^{1}((0,\infty))$ for $Re(z)>0$.
2. $\forall z \in \mathbb{C}, Re(z)>0 \to \Gamma(z+1)=z \Gamma(z)$;
3. Use (2) to extend. By induction on n, define $\Gamma(z):=\Gamma(z+1)/z$ for $Re(z)>-n-1$;
4. $\Gamma(1)=1, \Gamma(n+1)=n!$.

## 2.4 Modes of convergence
> [!important] Thm.
>  1. $({f_{n}}^{\rightarrow}_{\rightarrow} f)\implies (f_{n} \to f) \implies (f_{n} \overset{a.e.}{\to} f)$;
>  2. $(f_{n} \overset{L_{1}}{\to} f) \implies (f_{n} \overset{\mu}{\to} f)$;
>  3. $(f_{n} \overset{L_{r}}{\to} f) \implies (f_{n} \overset{L_{s}}{\to} f)$ if $r \ge s \ge 1$.
>  4. If $f_{n} \overset{a.e.}{\to} f, |f_{n}| \le g \in L^{1}$, then $f_{n} \overset{1}{\to} f$.

Proof. #TODO 

> [!note] Def. (Converge in measure)
> $\forall  \epsilon>0, \lim_{n \to \infty} \mu( \{ x: | f_{n}(x) - f(x) | > \epsilon \}  )=0$.

^deb71b

> [!note] Def. (Cauchy in measure)
> $\forall \sigma, \epsilon>0, \exists N \in \mathbb{N}, \forall n,m>N, \mu(\{x: |f_{n}(x)-f_{m}(x) | >\epsilon \})<\sigma$. It's usually denoted as $\mu(\{x: |f_{n}(x)-f_{m}(x) | >\epsilon \} \to 0$ as $m,n \to \infty$.

> [!important] Thm.
> Suppose $\{ f_{n} \}$ is Cauchy in measure, then
> 1. $\exists measurable\ f , s.t., f_{n} \overset{\mu}{\to} f$;
> 2. There is a subsequence $\{ f_{n_{j}} \}  s.t. f_{n_{j}} \overset{a.e.}{\to} f$; 
> 3. If also $f_{n} \overset{\mu}{\to} g$, then $g=f$ a.e.

^4529a6

Proof. 
1. Given Cauchy in measure, pick subsequence s.t. if $E_{j}:=\{x: |f_{n_{j}}(x)-f_{n_{j+1}}(x) | >2^{-j} \}$, then $\mu(E_{j})< 2^{-j}$. Let $F_{k}:=\cup_{j=k}^{\infty}E_{j}$, then $\mu(F_{k}) < 2^{1-k}$ by subadditivity. OTAH, for $x \notin F_{k}, i \ge j \ge k, |f_{n_{i}}(x)-f_{n_{j}}(x) | \le 2^{1-j} \le 2^{1-k} (*)$. Thus $\{ f_{n_{j}} \}_{j=k}^\infty$ is pointwise Cauchy and therefore convergent on $F_{k}^{c}$.
2. Let $F:= \cap F_{k}=\limsup E_{j}$, then $\mu(F)=0$. If we take $f(x):=\mathcal{X}_{F^{c}} \lim_{j} f_{n_{j}}(x)$, then f is measurable and $f_{n_{j}} \to f$ a.e. (the 2)
3. Then for $x \in F^{c}, \exists N, \forall j>N, | f_{n_{j}}(x)-f(x) | \le 2^{1-j}$. Then $f_{n_{j}} \overset{\mu}{\to} f$. #TODO 
4. Since $\{ | f_{n}-f | \ge \epsilon \} \subset \{ | f_{n}-f_{n_{j}} | \ge \frac{\epsilon}{2} \}\cup \{ | f_{n_{j}}-f | \ge \frac{\epsilon}{2} \}$, and the second term is small due to Cauchy in measure, we get $f_{n} \overset{\mu}{\to} f$ (the 1);
5. If also $f_{n} \overset{\mu}{\to} g$, and $\{ | f-g | \ge \epsilon \} \subset \{ | f-f_{n} | \ge \frac{\epsilon}{2} \}\cup \{ | f_{n}-g | \ge \frac{\epsilon}{2} \}$, then $\forall \epsilon>0, \mu(\{|f-g|>\epsilon\})=0$. Let $\epsilon\to 0$ using some sequence, then $f=g$ a.e. (the 3)

> [!important] Cor. (Cauchy Criterion)
> $\{ f_{n} \}$ is Cauchy in measure iff $\exists measurable\ f , s.t., f_{n} \overset{\mu}{\to} f$.

Proof. (<=) $\{ | f_{n}-f_{m} | \ge \epsilon \} \subset \{ | f_{n}-f | \ge \frac{\epsilon}{2} \}\cup \{ | f-f_{m} | \ge \frac{\epsilon}{2} \}$, take $n, m \to \infty$, and the two measures on RHS diminish.

> [!important] Cor. (This implication appears more often)
> If $f_{n} \overset{L_{1}}{\to} f$, then there is a subsequence $\{ f_{n_{j}} \}  s.t. f_{n_{j}} \overset{a.e.}{\to} f$.

> Ex. (ch2q33) Replace the condition of "$f:=\liminf f_{n}$" into "$f_{n} \overset{\mu}{\to} {f}$" in Fatou's lemma, it still holds.

> [!note] (Almost uniform convergence)
> ${f_{n}}_{\to}^{\overset{a}{\to}} f$ on F if $\forall \epsilon>0, \exists E \subset F, s.t., \mu(F \setminus E) < \epsilon, {f_{n}}_{\to}^{\to} f$ on E.

> [!important] Thm. (**Egorov's thm**)
> $\mu(X)<\infty, f_{n}(x) \to f(x)$ a.e. on X, then ${f_{n}}_{\to}^{\overset{a}{\to}} f$ on X.

Proof.
1. $\forall \epsilon>0$, we want to find $E \subset F$. It suffices to find $E \subset \{x \in F:  f_{n}(x) \to f(x) \text{ as } n \to \infty\}$, since the difference is a null set. Then WLOG, $f_{n}(x) \to f(x)$ everywhere.
2. Define $E_{n}(k):=\cup_{m=n}^{\infty} \{ x: |f_{m}(x) - f(x) |> \frac{1}{k} \}=: \cup_{m=n}^{\infty} F_{m}(k)$.
3. Claim: $\forall k,n, E_{n}(k) \supset E_{n+1}(k)$.
4. Claim: $\cap_{n} E_{n}(k)= \limsup_{m} F_{m}=\emptyset$. Otherwise, $\exists x \in \cap_{n} \cup_{m=n}^{\infty} F_{m}(k)$, i.e., $\forall n, \exists m \ge n, | f_{m}(x)-f(x) | > \frac{1}{k}$, i.e. $\exists \{ m_{t} \}_{t=1}^{\infty}, s.t. | f_{m_{t}}(x)-f(x) | > \frac{1}{k}$. Contradict with (1).
5. Since $\mu(E_{1}(k)) \le \mu(X) < \infty$, by continuity from above, $\mu(E_{n}(k))\to \mu(\emptyset)=0$. 
6. Then let k varies, then by definition,  $\forall k, \forall \epsilon>0,\exists N_{k} \in \mathbb{N}$, s.t. $\forall n \ge N_{k}, \mu(E_{n}(k)) < \epsilon 2^{-k}$. Thus $\forall \epsilon>0,H:=\cup_{k=1}^{\infty} E_{N_{k}}(k), \mu(H)<\epsilon$. The goal is to show ${f_{n}}_{\to}^{\to} f$ on $E:=H^{c}$.
7. $\forall x\in H^{c}, \forall  k, x \in E_{N_{k}}^{c}(k)$. Then $\forall m \ge N_{k}, x \in F_{m}(k), i.e. |f_{m}(x)-f(x)| \le \frac{1}{k}$. Thus $\forall k, \forall m \ge N_{k}, \sup_{H^{c}} | f_{m}-f | \le \frac{1}{k}$. Let $k \to \infty$, then it follows.

Rmk. #TODO 

> Ex. (ch2q40) The condition "$\mu(X)<\infty$" in Egorov's thm can be changed into "$|f_{n}| \le g \in L^{1}$".

Proof.
1. Step 1-4 remain valid. If we can fix step 5, then the following steps are still valid.
2. Note that $y \in E_{1}(k) \iff \exists m\ge 1, |f_{m}(y)-f(y)|>\frac{1}{k}$, which is $\sup_{m} |f_{m}(y)-f(y)|>\frac{1}{k}$. OTAH, $2g(y) \ge \sup_{m}|f_{m}(y)-f(y)|$. Then $E_{1}(k) \subset \{ 2g(x)>\frac{1}{k} \}$. $\mu(E_{1}(k)) \le \mu( \{ 2g(x)>\frac{1}{k} \}) \le 2k \int g < \infty$.

> [!important] Lemma. (Measurable function is almost simple func)
> $f:E \to \mathbb{C}, \mu(E)<\infty$, then $\forall \epsilon>0, \exists simple\ \phi, \exists F \subset E, F \in \mathcal{M}$, s.t. $\mu(E \setminus F)<\epsilon, \forall x \in F, |f(x)-\phi(x)|<\epsilon$.

Proof. #TODO 

> [!important] Cor. (Almost everywhere bounded)
> $f: E \to \mathbb{C}, \mu(E)<\infty$, then $\forall \epsilon>0, \exists M \in \mathbb{R}, E \in \mathcal{M}$, s.t., $\mu(E^{c})<\epsilon, |f(x)|<M$ on E.

Proof. Lemma, and then $|f(x)| \le |f(x)-\phi(x)| + |\phi(x)| = : M$. 

> [!important] Lemma. (cts func are dense in $L^{1}$)
> $\mu$ is Lebesgue-Stieltjes measure, $f:E \to \mathbb{C}$ where $\mu(E)<\infty$. Then $\forall \epsilon>0, \exists$ continuous func $g, F \in \mathcal{M}, F \subset E$, s.t. $m(E \setminus F)<\epsilon, ||f-g||_{1}<\epsilon$.

Proof. #TODO thm2.26

we can turn simple func into cts func

> [!important] Thm. (Lusin's thm)
> $\mu$ is Lebesgue-Stieltjes measure, measurable $f:E \to \mathbb{C}$ where $\mu(E)<\infty$. Then $\forall \epsilon>0, \exists$ continuous func $g,  \exists F \in \mathcal{M}, F \subset E$, s.t. $m(E \setminus F)<\epsilon, \forall x, |f(x)-g(x)|<\epsilon$.

Proof. #TODO 

> Cor. $\mu$ is Lebesgue-Stieltjes measure, $f:E \to \mathbb{C}$. Then f is measurable iff $\forall \epsilon>0, \exists$ closed $F \in \mathcal{M}, F \subset E$, s.t. $m(E \setminus F)<\epsilon, f|_{F}$ is continuous. https://heil.math.gatech.edu/6337/spring11/lusin.pdf

Rmk. (Littlewood's three principles of real analysis)
1. Every measurable set in $\mathbb{R}$ is nearly a finite union of intervals (prop1.20 #TODO );
2. Every function (of class Lp) on $\mathbb{R}$ is nearly continuous (Egorov's);
3. Every convergent sequence of measurable functions on finite measure set is nearly uniformly convergent / every measurable function is nearly continuous (Lusin's).

Rmk. $\forall f \in L^{1}, \epsilon>0, \exists$ complex-valued continuous func $g$ with compact support, s.t. $||f-g||_{1}<\epsilon$. https://mathproblems123.files.wordpress.com/2011/02/density-1.pdf

## 2.5 Product measure
In this part, we mainly talk about product of two spaces. But all in fact can generalize to any finite dimension.

> [!note] Def. (Rectangle)
> Consider measure spaces $(X, \mathcal{A}, \mu)$ and $(Y, \mathcal{B}, v)$, a rectangle is in the form $A \times B:=\{ (x,y): x \in A, y \in B \}$, where $A \in \mathcal{A}, B \in \mathcal{B}$. Let $\mathcal{R_{0}}$ be the collection of **finite disjoint union of rectangles**. 

Rmk.
1. $(A \times B) \cap (E \times F)=(A \cap E) \times (B \cap F)$ is still rectangle;
2. $(A \times B)^{c}=(X \times B^{c}) \cup (A^{c} \times B) \in \mathcal{R_{0}}$;
3. The rectangle set is a elementary family;
4. By prop1.7 ([[Real Analysis#^668d67]]), $\mathcal{R_{0}}$ is an algebra.
5. $\mathcal{R_{0}}$ can generate the product $\sigma$-algebra $\mathcal{A \otimes B}$, which is defined in ch1.2 ([[Real Analysis#^f3e312]]).

> Prop. (**Product measure**)
> 1. $\forall E = \cup_{j=1}^{m} (A_{j} \times B_{j}) \in \mathcal{R_{0}}$, define $\pi(E):=\sum_{j=1}^{m} \mu(A_{j})v(B_{j})$. (Again, $0 \cdot \infty=0$)
> 2. $\pi(E)$ is well-defined;
> 3. $\pi(E)$ is a premeasure;
> 4. The induced outermeasure $\pi^{*}(E):=\inf_{ \{R_{j}\} }\{ \sum_{j=1}^{\infty} \pi(R_{j}) : R_{j}\in \mathcal{R_{0}}, \cup R_{j} \supset E  \}$;
> 5. The **product measure** $\mu \times v$ on $\mathcal{A \otimes B}$ can be defined as $\pi^{*}|_{\mathcal{A \otimes B}}$.

> Prop. If $\mu, v$ are $\sigma$-finite, then 1) $\mu \times v$ is $\sigma$-finite; 2) therefore, by thm1.14 ([[Real Analysis#^63f1c6]]), $\mu \times v$ is the unique one among those that extend $\pi|_{\mathcal{R_{0}}}$ , i.e. $(\mu \times v)(\cup_{j=1}^{m} (A_{j} \times B_{j})):=\sum_{j=1}^{m} \mu(A_{j})v(B_{j})$.

Proof. $X \times Y=\cup_{j=1}^{\infty} \cup_{k=1}^{\infty} (X_{j} \times Y_{k})$ is a big union, and $(\mu \times v)(X_{j} \times Y_{k})<\infty$.

#TODO extend results in 2.1-2.3

> [!note] Def.
> 1. x-session of E: $E_{x}:=\{ y \in Y : (x,y) \in E \}$, y-session of E: $E^{y}$.
> 2. x-session of f: $f_{x}:=y \mapsto f(x,y)$, y-session of f: $f^{y}$.
> 3. E.g. say $f: E \to H$, then $f_{x}: E_{x} \to H$; $\mathcal{X}_{E}^{y}=\mathcal{X}_{E^{y}}$.

> Prop.
> 1. If $E \in \mathcal{A \otimes B}$, then $E_{x} \in \mathcal{B}, E^{y} \in \mathcal{A}$;
> 2. If $f$ is $\mathcal{A \otimes B}$-measurable, then $f_{x}$ is $\mathcal{B}$-measurable, $f^{y}$ is $\mathcal{A}$-measurable.

Proof.
1. It suffices to show $\mathcal{R}:=\{ E \subset X \times Y: E \in \mathcal{A} \otimes \mathcal{B}; \forall x\in X, E_{x}\in \mathcal{B} \} \supset \mathcal{A} \otimes \mathcal{B}$. Note that it is a $\sigma$-algebra, and it contains $\mathcal{R_{0}}$, thus contains $\mathcal{M(R_{0})}=\mathcal{A} \otimes \mathcal{B}$.
2. #TODO 

> [!note] Def. (**Monotone class**) 
> $\mathcal{C} \subset P(X)$, s.t.,
> 1. Closed under countable increasing union;
> 2. Closed under countable decreasing intersection.

Rmk.
1. The motivation is to make use of the continuity of measure.
2. Every $\sigma$-algebra is a monotone class for sure.
3. The intersection of any family of monotone classses is a monotone class. Thus the unique smallest monotone class containing $\mathcal{E}$ is generated by $\mathcal{E}$.

> [!important] Lemma. (**Monotone class lemma**)
> If $\mathcal{A}$ is an algebra, then the generated monotone class coincides with the generated $\sigma$-algebra.

Proof. #TODO 

> Prop.
> If $\mu_{1}, \mu_{2}$ are finite measure, $E \in \mathcal{A \otimes B}$, and $f= x \mapsto \mu_{2}(E_{x})$ are $\mathcal{A}$-measurable, $g= x\mapsto \mu_{1}(E^{y})$ are $\mathcal{B}$-measurable, then $$\begin{aligned}(\mu_{1} \times \mu_{2})(E)&=\int_{X} \mu_{2}(E) \ \mathrm{d} \mu_{1}=\int_{X}\left(\int _{Y} \mathcal{X}_{E_{x}} \ \mathrm{d} \mu_{2} \right) \ \mathrm{d} \mu_{1}\\&=\int_{Y} \mu_{1}(E) \ \mathrm{d} \mu_{2}=\int_{Y}\left(\int _{X} \mathcal{X}_{E^{y}} \ \mathrm{d} \mu_{1} \right) \ \mathrm{d} \mu_{2}\end{aligned}$$
> If $\mu_{1}, \mu_{2}$ are $\sigma$-finite measure, the above still holds.

Proof.
1. It suffices to show that $\mathcal{C}:=\{ E \subset X \times Y: \text{ satisfy all 3 conditions} \} \supset \mathcal{A \otimes B}$. According to the monotone class lemma, $\mathcal{A \otimes B=M(R_{0})=C(R_{0})}$. Now it suffices to show $\mathcal{C}$ is a monotone class and $C \supset R_{0}$.
2. $\mathcal{C}$ is a monotone class:
3. #TODO 
4. $\sigma$-finite case:

> [!important] Thm. (**Funibi-Tonelli thm**)
> If $\mu_{1}, \mu_{2}$ are $\sigma$-finite measure,
> 1. (**Tonelli**) If $f \in L^{+}(X \times Y)$, then $x \mapsto \int f_{x} \ \mathrm{d} \mu_{2} \in L^{+}(X), y \mapsto \int f^{y} \ \mathrm{d} \mu_{1} \in L^{+}(Y)$, and  $$\begin{aligned} \int f \ \mathrm{d} (\mu_{1} \times \mu_{2})&=\int_{X} ( \int_{Y} f(x,y) \ \mathrm{d} \mu_{2}(y) ) \ \mathrm{d} \mu_{1}(x)\\&=\int_{Y} ( \int_{X} f(x,y) \ \mathrm{d} \mu_{1}(x) ) \ \mathrm{d} \mu_{2}(y)\end{aligned}(*)$$
> 2. (**Fubini**) If $f \in L^{1}(\mu_{1} \times \mu_{2})$, then $f_{x} \in L^{1}(\mu_{2})$ for a.e. $x$, $f_{y} \in L^{1}(\mu_{1})$ for a.e. $y$ , the a.e.-defined functions $x \mapsto \int f_{x} \ \mathrm{d} \mu_{2} \in L^{1}(X), y \mapsto \int f^{y} \ \mathrm{d} \mu_{1} \in L^{1}(Y)$ and $(*)$ holds.

Proof. #TODO 

E.g. Show that $\int_{0}^{\infty} \frac{\sin x}{x} \ \mathrm{d}x=\frac{\pi}{2}$.  Note that $\frac{1}{x}=\int_{0}^{\infty} \exp(-xt) \ \mathrm{d}t, \forall x \ge 0$. #TODO 

# Ch3 Signed measures and differentiation
## 3.4 Lebesgue Differential Thm, LDT
In this part, remember that $n$ refers to the dimension. We may use $c_{n}$ to denote a constant that only depends on $n$.

> [!note] Def. 
> 1. (**Locally integrable**) $f: \mathbb{R}^{n} \to \mathbb{C}, s.t., \int_{K} |f| \ \mathrm{d} m < \infty$ for any compact $K$. The set of them is denoted as $L_{loc}^{1}(\mathbb{R}^{n})$, which is a superset of $L^{1}(\mathbb{R}^{n})$;
> 2. (**Hardy-littlewood max function**) $M_{f}:= x \mapsto \sup_{r>0} \frac{1}{m(B_{r}(x))} \int_{B_{r}(x)} |f| \ \mathrm{d}m$;
> 3. (**Variants**) **Uncentered max func** $\tilde M_{f}:=x \mapsto \sup_{B} \{ \frac{1}{m(B)} \int_{B} |f| \ \mathrm{d}m : x \in B \}$. **Rectangle version** $M^{*}_{f}:=x \mapsto \sup_{R} \{ \dots : x \in R, R\text{ is rectangle with any direction} \}$. **Kakeya/Besicovitch set**: a set containing unit line segments pointing all possible directions.
> 4. (operator $T$ of type **weak(p,p)**) Let $E_{\lambda}:=\{ x \in \mathbb{R}^{n}: |Tf(x)|>\lambda \}$, then $\exists C \in \mathbb{R}^{ >0}, \forall \lambda >0, \forall f \in L^{p}$, $m(E_{\lambda})\le \frac{ C \cdot ||f||_{p}^{p} }{\lambda^{p}}$.
> 5. (operator $T$ of type **strong(p,p)**) $\exists C \in \mathbb{R}^{ >0},  \forall f \in L^{p}$, $|| Tf(x) ||_{p} \le C \cdot ||f||_{p}^{p}$.

Rmk.
1. $m(B_{r}(x))=r^{n} \cdot m(B_{1}(0))$;
2. $M_{f} \le \tilde M_{f} \le 2^{n} M_{f}$;
3. There is a Kakeya set with zero measure, resulting in the failure of Vitali Covering lemma, thus LDT, on the rectangle version.

> [!important] Lemma. (**Vitali Covering lemma**)
> Suppose measurable $E \subset \cup_{\alpha \in A} B_{\alpha}$, where $\sup_{\alpha \in A} r(B_\alpha)<\infty$. Then there is a disjoint countable subcollection $\alpha_{1}, \dots \alpha_{k} \dots$, s.t.  $m(E) \le c_{n} \sum_{k=1}^{\infty} m(B_{\alpha_{k}})$. 

Proof.
1. When RHS is infinite, we are done. WLOG, $\sum_{k=1}^{\infty} m(B_{\alpha_{k}}) < \infty$, which means $\lim_{k \to \infty} m(B_{\alpha_{k}})=0$, i.e. $\lim_{k \to \infty} r(B_{\alpha_{k}})=0$.
2. It's sufficient to show that $\forall  \alpha, B_\alpha \subset \cup_{k=1}^{\infty} 5B_{\alpha_{k}}$. Here the dilution of ball $5B_{r}(x):=B_{5r}(x)$. The heuristic is that we keep choosing the largest available ball and then crossing out all balls that overlap with the chosen to get a disjoint collection. Then we need to show the dilution of these balls can still cover the whole set;
4. The largest ball may not exist. An operational construction makes use of supremum. Pick $\alpha_{k+1}$, s.t.  $r(B_{\alpha_{k+1}}) > \frac 1 2 \sup_{\beta}\{ r(B_{\beta}): B_{\beta} \cap (\cup_{j=1}^{k} B_{\alpha_{j}})= \emptyset \}$, which is finite.
5. Now $\forall \alpha$, find the first $k, s.t. r(B_{\alpha_{k+1}}) < \frac{1}{2} r(B_{\alpha})$, i.e. $\forall j \le k, r(B_{\alpha_{j}}) \ge \frac{1}{2} r(B_{\alpha})$. Such k exists since the limit of radius is zero. If we can find an overlaping ball for $B_{\alpha}$ in the first k balls, we are done, because the dilution of it will cover $B_{\alpha}$.
6. Note that $B_{\alpha}$ is itself not a potential option for supremum when getting $\alpha_{k+1}$, otherwise won't get a smaller one: $B_{\alpha_{k+1}}$. Hence we know $B_{\alpha} \cap (\cup_{j=1}^{k} B_{\alpha_{j}}) \ne \emptyset$. Find any $j \le k, s.t. B_{\alpha}\cap B_{\alpha_{j}} \ne \emptyset$, then we are done.

> [!important] Thm. (**Hardy-littlewood maximum thm**)
> The H-L max func is of weak(1,1). In other word, let $E_{\lambda}:=\{ x \in \mathbb{R}^{n}: M_{f}(x)>\lambda \}$, then $\exists c_{n} \in \mathbb{R}^{ >0}, \forall \lambda >0, \forall f \in L^{1}$, $m(E_{\lambda})\le \frac{ c_{n} \cdot ||f||_{1} }{\lambda}$.

Proof.
1. $\forall x \in E_{\lambda}, M_{f}(x) := \sup_{r} \frac{1}{m(B_{x}(r))} \int_{B_{x}(r)} |f|  > \lambda$. Then $\exists B_{x}, s.t. \frac{1}{m(B_{x})} \int_{B_{x}} |f|  > \lambda$ and $E_{\lambda} \subset \cup_{x \in E_{\lambda}} B_{x}$.
2. Note that $m(B_{x}) \le \frac{1}{\lambda} \int_{B_{x}} |f| \le \frac{||f||_{1}}{\lambda}<\infty$, we can take supremum. Then by covering lemma, $m(E_{\lambda}) \le c_{n} \sum_{k=1}^{\infty} m(B_{x_{k}}) \le c_{n}\sum_{k=1}^{\infty}  \frac{1}{\lambda} \int_{B_{x}} |f|=\frac{c_{n}}{\lambda} \int_{\cup B_{x}} |f| \le c_{n} \frac{||f||_{1}}{\lambda}$.

> Lemma. For $f \in L_{loc}^{1}$, define an operator $T_{f}(x):=\lim_{r\to 0} \frac{1}{m(B_{r}(x))} \int_{B_{r}(x)} |f(x)-f(y)| \ \mathrm{d} m (y)$. Define **Lebesgue set** $L_{f}:=\{x: T_{f}(x) =0  \}$. If $f$ is continuous at $x$, then $x \in L_{f}$. 

Proof. By continuity, $\forall \epsilon>0, \exists \delta>0$ s.t. $\forall y\in B_{\delta}(x), |f(y)-f(x)|<\epsilon$. Then $\forall \epsilon>0, \forall r<\delta, \frac{1}{m(B_{r}(x))} \int_{B_{r}(x)} |f(x)-f(y)| \ \mathrm{d} y<\epsilon$. Take r to 0 to get $\forall \epsilon>0, T_{f}(x)<\epsilon$, and then take $\epsilon$ to 0.

> [!important] Thm. (Lebesgue Differential Thm, LDT)
> For $f \in L_{loc}^{1}(\mathbb{R}^{n}), T_{f}(x)=0$ a.e. In other word, $\mu(L_{f}^{c})=0$.

Proof. 
1. Claim: $T_{f}$ exists in $\mathbb{R}$ a.e. i.e. $\theta(f):= x \mapsto (\limsup_{r}-\liminf_{r}) \frac{1}{m(B_{r}(x))} \int_{B_{r}(x)} | f(x)-f(y) | \ \mathrm{d} y=0$ a.e. Since $\{ x: \theta(f)(x)\ne 0 \} \subset \cup_{\lambda>0} \{ x: \theta(f)(x)>\lambda \}$, it suffices to show each of the latter is of measure 0.
2. To show that, recall that continuous funcs are dense in $L^{1}$, i.e. $\exists \epsilon>0, \exists g \in C(\mathbb{R}^{n})$, s.t. $||f-g||_{1}<\epsilon$ and $\theta(g)=0$ by lemma. Note that $\theta(f)=|\theta(f)-\theta(g)| \le |\theta(f-g)| \le 2M_{f-g}$.  Consider that $\theta(f)(x) > \lambda$ implies $M_{f-g} > \frac{\lambda}{2}$. Then $\forall \epsilon>0$, by maximum thm, $m(\{\dots\}) \le c_{n} \frac{||f-g||_{1}}{\lambda/2}<\frac{c_{n}\epsilon}{\lambda/2}$. Send $\epsilon$ to 0.
3. $$\begin{aligned}
|f(x)-f(y)| &\le |f(x)-g(x)+g(x)-g(y)+g(y)-f(y)| \\ 
&\le |f(x)-g(x)|+|g(x)-g(y)|+|g(y)-f(y)| \\
|T_{f}(x)| &\le M_{f-g}(x)+|f(x)-g(x)| \\
\forall \lambda>0, & \{ T_{f}>\lambda \} \subset \{M_{f-g}>\frac{\lambda}{2}\}\cup \{|f(x)-g(x)|>\frac{\lambda}{2}\}
\end{aligned}$$
The latter is zero given Chebyshev's inequality ([[Real Analysis#^cd31a5]]).

Rmk. For n=1 and continuous, $\frac{\ \mathrm{d}}{\ \mathrm{d} x} \int_{a}^{x} f(y) \ \mathrm{d}y = f(x)$. We get the fundamental thm of calculus.

## 3.5 Func of bounded variation
This session works on $m$.

> [!important] Thm. (3.5.1)
> $F: \mathbb{R} \to \mathbb{R}$, $F \nearrow$, then $F$ is 1) continuous a.e. and 2) differentiable a.e. with 3) $F: [a,b] \to \mathbb{R}, \int_{a}^{b} f'(x) \ \mathrm{d}m(x) \le f(b)-f(a)$. 

^aa2507

Proof.
1. $D:=$ the set of discontinuous points. Claim D is countable. $x \in D \iff F(x+)>F(x-)$. Let $I_{x}:= (F(x-), F(x+))$, then $card(D)=card(\{I_{x}\})$. Claim: $I_{x}$'s are disjoint. Since $\forall x_{1},x_{2} \in D, x_{1}<x_{2}, \exists y \in (x_{1}, x_{2})$, $F(x_{1}+):=\inf \{ F(x):x_{1}<x \} \le F(y) \le \sup \{ F(x) : x < x_{2} \} =: F(x_{2}-)$. Since they're disjoint, we can always pick a non-overlaping rational number in each $I_{x}$, thus $card(\{I_{x}\})\le card(\mathbb{Q})$.
2. Two methods: abstract measure theory or some variants of Vitali covering lemma; #NotCovered 
3. For convenience, define $f(x>b):=f(b)$. Let $g(x):=f'(x+):=\lim_{n \to \infty} g_{n}(x)$, where $g_{n}(x):=\frac{ f(x+ \frac{1}{n} )-f(x) }{\frac{1}{n}} \in L^{+}$, then $g=f'$ a.e. Apply Fatou's lemma, $$\begin{aligned} \int_{[a,b]} f' \ \mathrm{d}m&=\int_{[a,b]} \lim g_{n} \le \liminf \int_{[a,b]}g_{n} \\ &= \liminf \left( n \int_{\left[b,b+ \frac{1}{n}\right]} f - n \int_{\left[a,a+ \frac{1}{n}\right]} f \right) \\ &=\liminf \left( f(b)- n \int_{\left[a,a+ \frac{1}{n}\right]} f \right) \le f(b)-f(a) \end{aligned}$$

E.g. (**Cantor func**) $F \nearrow$, continuous on $[0,1]$, diff. a.e. and $F'=0$ a.e.

> [!note] Def.
> - (**Total variation func**) $T_{f}(x)=\sup_{n, \{x_{i}\}} \{ \sum_{j=1}^{n} |f(x_{j})-f(x_{j-1})| : n \in \mathbb{N}, -\infty < x_{0} < \dots < x_{n}=x \}$;
> - (**Bounded variation**) If $T_{f}(\infty)=\lim_{x \to \infty} T_{f}(x)<\infty$;
> - (**Total variation on $[a,b]$**) $T_{f}([a,b]), Var_{f}([a,b])$;
> - The collection of those functions is denoted as $BV(\mathbb{R})$ and $BV([a,b])$.

Rmk. $T_{f} \nearrow$, since if $a<b$, we can assume that a is always one of the subdivision points without affecting the values. Thus $T_{f}([a,b])=T_{f}(b)-T_{f}(a)$.

E.g. $f(x)= x \sin \frac{1}{x}  \mathcal{X}_{\{x \ne 0\}} \notin BV([0,1])$.

Ex. $\mathbb{Q}=\{q_{n}: n \in \mathbb{N}\}, f:=\sum_{k=1}^{\infty} 2^{-k} \mathcal{X}_{[q_{k},\infty)}$ is an increasing func with set of discontinuities $\mathbb{Q}$.

> Prop. $f: X \to \mathbb{C} \in BV([a,b]), \int_{[a,b]} |f'| \le T_{f}(a,b)$.

Proof. #NotCovered 

> [!important] Thm.
> $f \in BV(\mathbb{R})$ iff f is the difference between two bounded increasing functions.

Proof. (=>) 
1. Claim: the **Jordan decomposition** $f=\frac{1}{2} ( T_{f}+f) + \frac{1}{2}(T_{f}-f)$ gives a valid decomposition. The motivation is that $T_{f} \nearrow$ and $\forall a \in \mathbb{R}, a+|a|\ge 0$. 
2. By def. $T_{f}(\infty)<\infty$, thus $|T_{f} \pm f| < \infty$, bounded. WTS $\forall  x<y$, $(T_{f} \pm f)(y)>(T_{f} \pm f)(x)$.
3. By def. $\forall \epsilon>0, \exists -\infty<x_{0}< \dots x_{n}=x$, s.t. $T_{f}(x)-\epsilon<\sum_{j=1}^{n} |f(x_{j})-f(x_{j-1})|$. OTAH, $\sum_{j=1}^{n} |f(x_{j})-f(x_{j-1})| + |f(y)-f(x)| \le T_{f}(y)$. In summary, $$\begin{aligned} (T_{f} \pm f)(y) &\ge \sum_{j=1}^{n} |f(x_{j})-f(x_{j-1})| + |f(y)-f(x)| \pm f(y) \\ &\ge T_{f}(x) -\epsilon + |f(y)-f(x)| \pm f(y)  \\ &=(T_{f} \pm f)(x) -\epsilon + |f(y)-f(x)| \pm( f(y)- f(x)) \\&\ge (T_{f} \pm f)(x) -\epsilon\end{aligned}$$

> Cor. $f \in BV(\mathbb{R})$, then $f$ is differentiable a.e.

> [!note] Def. (**Absolutely continuous**)
> $f:[a,b] \to \mathbb{R}$ is called absolutely continuous if $\forall \epsilon>0, \exists \delta>0$, s.t. $\forall$ finite disjoint collection of intervals $(a_{1}, b_{1}) \dots (a_{n}, b_{n})$, $\sum_{j=1}^{n} (b_{j}-a_{j})<\delta \to \sum_{j=1}^{n} |f(b_{j})-f(a_{j})|<\epsilon$. The collection of these func is denoted as $AC([a,b])$.

Rmk.
1. $AC([a,b]) \subset \mathcal{C}([a,b])$: trivial.
2. $AC([a,b]) \subset BV([a,b])$; #TODO 

> [!important] Thm.
> $f \in AC([a,b]), f'=0$ a.e. then $f$ is constant.

Proof. #TODO 

> [!note] Def. (**Vitali cover**)
> A collection of intervals $J$ is a Vitali cover for $E \subset \mathbb{R}$ if $\forall \epsilon>0, x \in E, \exists I \in J$ s.t. $m(I)<\epsilon, x\in I$.

> Lemma. (another **Vitali covering lemma**)
> Outermeasure $m^{*}, E \subset \mathbb{R}, m^{*}(E)<\infty$. Let J be a Vitali cover of E, then $\forall \epsilon>0, \exists$ disjoint $I_{1}, \dots I_{N} \in J, s.t. m^{*}(E \setminus \cup_{j=1}^{N} I_{j}) < \epsilon$.

Proof. #TODO 

> Lemma. $f \in L^{1}([a,b]), \forall \epsilon>0, \exists \delta>0, \forall E, m(E)<\delta \to \int_{E} |f| \ \mathrm{d}m<\epsilon$.

Proof. #TODO 

> [!important] Thm. (3.5.2)
> $F: [a,b] \to \mathbb{C}$, TFAE:
> 1. F absolutely continuous;
> 2. $\exists f \in L^{1}([a,b], \mathcal{L},m), \forall x, F(x)-F(a)=\int_{[a,x]} f$;
> 3. F is differentiable a.e. on $[a,b], F' \in L^{1}(\ \mathrm{d} m)$, and $\forall x, F(x)-F(a)=\int_{[a,x]} F'$.

^60422f

Proof. #TODO 

> Prop. $F:[a,b] \to \mathbb{R}, F'=f, f \in L^{1}([a,b])$, then $F(b)-F(a)=\int_{[a,b]} f$.

Proof.  As a generalization of thm3.5.1 ([[Real Analysis#^aa2507]]). [proof](https://math.stackexchange.com/questions/68364/integral-of-the-derivative-of-a-function-of-bounded-variation), [proof2](https://math.stackexchange.com/questions/678120/the-total-variation-and-the-integral-of-the-derivative), [proof3](https://math.stackexchange.com/questions/126577/total-variation-and-integral)  #NotCovered 

Ex. $x^{a} \sin(x^{-b}) \mathcal{X}_{\{0\}}$ is differentiable everywhere by definition. It is in $BV([-1,1])$ iff $a > b$. The case of $a>b$ can be shown by showing absolute continuity using thm3.5.2 ([[Real Analysis#^60422f]]), while the other case can be shown by giving counter example similar to $x_{n}^{-b}=n \pi + \frac{\pi}{2}$.

Ex. $F: \mathbb{R} \to \mathbb{C}$, then $\exists M \in \mathbb{R} s.t. \forall x,y \in \mathbb{R}, |F(x)-F(y)| \le M|x-y|$ (Lipschitz continuous) iff $\exists M \in \mathbb{R} s.t. |F'| \le M$ a.e. and F is absolutely continuous.

# Ch6 $L^{p}$ space
## 6.1 Basic theory

> [!note] Def.
> For $0<p<\infty, f: X \to \mathbb{C}$:
> - $L^{p}$ **norm**: $||f||_{p}:=(\int_{X} |f|^{p} \ \mathrm{d} \mu)^{\frac{1}{p}}$;
> - $||f||_{\infty}=\inf \{ M: M \ge 0, \mu(\{ x \in X: |f(x)| \ge M \})=0 \}$;
> - $L^{p}$ **space**: $L^{p}(X):=\{ f: ||f||_{p}<\infty \}$;
> - **Distribution function**: $\lambda_{f}(\alpha):=\mu(\{ x \in X: |f(x)| > \alpha \})$, $\lambda_{f}: (0, \infty) \to [0, \infty]$;
> - $||f||_{p, \infty}:=(\sup_{\alpha>0} \alpha^{p} \lambda_{f}(\alpha))^{\frac{1}{p}}$;
> - **Weak $L^{p}$ space**: $L^{p, \infty}(X):=\{ f: ||f||_{p, \infty}<\infty \}$;

Rmk.
1. $||f||_{\infty}$ can also be denoted as $ess\ sup |f(x)|$, since $|f(x)| \le ||f||_{\infty}$ a.e. $\le \sup f$.
2. $\lambda_{f} \searrow$ and right continuous (use continuity from below).
3. Just like we did in $L^{1}$, we take two function with null set difference as the same element.
4. $0<p<\infty, ||f||_{p} < ||f||_{\infty}$.

> Prop. $p<\infty, f \in L^{p} \cap L^{\infty}$ and $\forall q>p, f \in L^{q}$, then $\lim_{q \to \infty} ||f||_{q} = ||f||_{\infty}$.

Proof.
1. WTS $\liminf_{q} ||f||_{q} \ge ||f||_{\infty}$ and $\limsup_{q} ||f||_{q} \le ||f||_{\infty}$.
2. Assume $||f||_{\infty}>0$. WTS $\forall \epsilon>0, \liminf_{q} ||f||_{q} \ge ||f||_{\infty} - \epsilon$. Define $S_{\epsilon} := \{ x : |f(x)| > ||f||_{\infty}-\epsilon \}$. Then $\mu(S_{\epsilon})>0$ by def.
3. $\forall q>0, ||f||_{q} > (\int_{S_{\epsilon}} |f(x)|^{q})^{\frac{1}{q}} = (||f||_{\infty}-\epsilon) \mu(S_{\epsilon})^{\frac{1}{q}}$. Given that $+\infty> ||f||_{p} > (||f||_{\infty}-\epsilon) \mu(S_{\epsilon})^{\frac{1}{p}}$, we know $\mu(S_{\epsilon})<\infty$. Therefore $\liminf_{q} ||f||_{q} \ge ||f||_{\infty} - \epsilon$.
4. WTS $\limsup_{q} ||f||_{q} \le ||f||_{\infty}$. $$\left(\int |f|^{q} \right)^{\frac{1}{q}} = \left(\int |f|^{q-p} |f|^{p} \right)^{\frac{1}{q}} \le \left(\int ||f||_\infty^{q-p} |f|^{p} \right)^{\frac{1}{q}}=||f||_{\infty}^{\frac{(q-p)}{q}} ||f||_{p}^{\frac{p}{q}}$$Take limsup on each side.

> [!important] Thm.
> $||f||_{p}^{p} = p \int_{0}^{\infty} \alpha^{p-1} \lambda_{f}(\alpha) \ \mathrm{d}m(\alpha)$.
> 

Proof. #TODO 

> [!important] Thm. (**Chebyshev**)
> $f  \in L^{p}, \alpha>0$, then $\lambda_{f} (\alpha) \le \frac{ ||f||_{p}^{p} }{ \alpha^{p} }$.

Proof. #TODO 

> Cor. $||f||_{p, \infty} \le ||f||_{p}$, i.e. $L^{p} \subset L^{p, \infty}$.

Proof. #TODO 

> Lemma. $0 < a \le b, 0 < \theta < 1$, then $a^{\theta} b^{1-\theta} \le \theta a + (1-\theta)b$, with equality iff $a=b$.

Proof. Divide both side by b and then take $t=\frac{a}{b}$. High school stuff.

> [!important] Thm. (Holder's inequality)
> $1 \le p \le \infty$, find $p'$ s.t. $\frac{1}{p} + \frac{1}{p'}=1$, then $||fg||_{1} \le ||f||_{p} ||g||_{p'}$, with equality iff $\exists \alpha, \beta, s.t. (\alpha,\beta) \ne (0,0)$ and $\alpha |f(x)|^{p}=\beta |g(x)|^{p'}$ a.e.

Proof. WLOG, $||f||_{p} \le ||g||_{p'}$.
1. Case1: $p=1, p'=\infty$ or $p=\infty, p'=1$. Trivially $\int |fg| \le \left(\int |f|\right)\cdot ess \sup |g(x)|$.
2. Case2: $1<p<\infty$.
3. Subcase1: $||f||_{p}=0$. Since $f=0$ a.e. LHS is 0.
4. Subcase2: $||g||_{p'}=\infty$. Then RHS is infinity.
5. Subcase3: By rescaling, WLOG, $||f||_{p}=||g||_{p'}=1$, WTS $||fg||_{1} \le 1$. For every x, apply the above lemma by taking $a=|f(x)|^{p}, b=|g(x)|^{p'}, \theta=\frac{1}{p}$, we get $|f(x)g(x)| \le \frac{1}{p} |f(x)|^{p} + \frac{1}{p'} |g(x)|^{p'}$, therefore $\int |fg| \le \frac{1}{p} + \frac{1}{p'}=1$.
6. For the case of equality, it is iff a=b

> [!important] Thm. (Minkowski's inequality)
> $1 \le p \le \infty, ||f+g||_{p} \le ||f||_{p} + ||g||_{p}$

Proof.
1. If $p=\infty$ or $p=1$, derivable fom $|(f+g)(x)| \le |f(x)| + |g(x)|$.
2. If $||f+g||_{p}=0$, LHS=0.
3. Now $1 < p < \infty, ||f+g||_{p} \ne 0$. Try to have a multiplicative form to apply Holders's. Note that $\frac{1}{p} + \frac{1}{p'}=1 \implies 1+ \frac{p}{p'}=p \implies (p-1)p'=p$ and  $|f+g|^{p}=|f+g| \cdot |f+g|^{p-1} \le|f| \cdot |f+g|^{p-1} + |g| \cdot |f+g|^{p-1}$.
4. $$\begin{aligned}||f+g||_{p}^{p} &= \int |f+g|^{p} \le \int | f\cdot |f+g|^{p-1} |  + \int | g \cdot |f+g|^{p-1} | \\ & = || f \cdot |f+g|^{p-1} ||_{1} + || g\cdot |f+g|^{p-1} ||_{1}  \\&\le (||f||_{p} + ||g||_{p})\cdot ||(f+g)^{p-1}||_{p'} \\ &= (||f||_{p} + ||g||_{p})\cdot (\int |f+g|^{(p-1)p'})^{\frac{1}{p'}}\\ &= (||f||_{p} + ||g||_{p})\cdot ( ||f+g||^{p}_{p})^{\frac{1}{p'}} \end{aligned}$$

> [!important] Thm. (Critical point of Minkowski)
> - $||f+g||_{1}=||f||_{1}+||g||_{1} \iff |(f+g)(x)|=|f(x)|+|g(x)|$ a.e.
> - $1 < p < \infty, ||f+g||_{p}=||f||_{p}+||g||_{p} \iff \exists C \ge 0, f(x)=C \cdot g(x)$ a.e.

Proof. 
1. The case of $p=1$ is obvious. 
2. The case of $p=\infty$ #NotCovered 
3. The case of $1<p<\infty$. In the proof, the first inequality becomes equal iff $|(f+g)(x)|=|f(x)|+|g(x)|$ a.e. The second inequality (Holder's) becomes equal iff $\exists \alpha, \beta, s.t. (\alpha,\beta) \ne (0,0)$ and $\alpha |f(x)|^{p}=\beta ( |(f+g)(x)|^{p-1} )^{p'}=\beta |(f+g)(x)|^{p}$ a.e. These two hold iff $\exists C \ge 0, f(x)=C \cdot g(x)$ a.e.

> [!important] Thm. (Riesz-Fischer)
> $1 \le p \le \infty$, then $(L^{p}, || \cdot||_{p})$ is Banach. 
> 

Proof. #TODO 

> Prop. Suppose $1 \le p < \infty$. $||f_{n}-f||_{p} \to 0$ implies $f_{n} \overset{\mu}{\to} f$. Conversely, $||f_{n} \overset{\mu}{\to} f$ and $\forall n,|f_{n}|< g \in L^{p}$ implies $||f_{n}-f||_{p} \to 0$.

Proof.
1. Recall definition of convergence in measure ([[Real Analysis#^deb71b]]) and the fact that it induces an a.e. convergence subseq ([[Real Analysis#^4529a6]]). Let $H_{\epsilon,n}:=\{x: | f_{n}(x)-f(x)| > \epsilon  \}$. $f_{n} \overset{\mu}{\to} f$ iff $\forall \epsilon>0, \mu(H_{\epsilon, n}) \to 0$ as $n \to \infty$.
2. (Lp convergence implies convergence in measure) $$\begin{aligned} &||f_{n}-f||_{p} \iff \int |f_{n}-f|^{p} \to 0 \\ & \implies  \forall  \epsilon>0, \int_{H_{\epsilon, n}} |f_{n}-f|^{p} \to 0 \\ & \implies \forall  \epsilon>0,   \int_{H_{\epsilon, n}} \epsilon^{p} \to 0 \\& \iff  \forall  \epsilon>0,  \epsilon^{p} \cdot \mu(H_{\epsilon,n}) \iff  f_{n} \overset{\mu}{\to} f \end{aligned}$$
3. (convergence in measure implies Lp convergence under dominance) Convergence in measure induces an a.e. convergence subseq. WTS $\lim \int |f_{n}-f|^{p}=0$. Try to satisfy the conditions of DCT for $h_{n}:= |f_{n}-f|^{p}$. $\int |h_{n}|=\int (|f|+|g|)^{p} \le || (|f|+|g|) ||_{p}^{p}$, which, by Minkowski, no more than $(||f||_{p}+||g||_{p})^{p}<\infty$.
4. Suppose the consequent false given antecedent, then $\exists  \epsilon>0, \exists \{ f_{n_{i}} \}$ s.t. $||f_{n_{i}}-f||_{p} \ge \epsilon$. OTAH, since subsequence preserves sequence convergence, $f_{n_{i}} \overset{\mu}{\to} f$. Use the above argument to achieve contradiction.

## 6.2 Dual of $L^{p}$
> [!note] Def. (Linear functional, dual)
> Let X be a vector space over $\mathbb{C}$,
> - A **linear functional** is $T:X \to \mathbb{C}$. 
> - A **bounded linear function** is when $\exists C \in \mathbb{R}, \forall x\in X, |Tx| \le C ||x||$.
> - The **dual space** $X^{*}$ is the collection of bounded linear functional on X.
> - **Isometric isomorphism**: normed vector space $(X, || \cdot||_{X}), (Y, ||\cdot||_{Y}), \exists T$ surjective s.t. $||x||_{X}=||Tx||_{Y}$.

Rmk. #NotCovered 
1. (Isometric isomorphism) For $1<p<\infty, (L^{p})^{*} \overset{\sim}{=} L^{p'}$.
2. $L^{2}$ is the only Hilbert space, $(L^{2})^ * \overset{\sim}{=} L^{2}$.
3. If $\mu$ is $\sigma$-finite, then $(L^{1})^{*}=L^{\infty}, L^{1} \subset (L^{\infty})^{*}$.

> [!important] Thm.
> $1 \le p < \infty,  f\in L^{p}$, then $||f||_{p}= \sup \{ |\int_{X} fg \ \mathrm{d} \mu| : g \in L^{p'} \}$. By normalization, we get $\sup \{ |\int_{X} fg \ \mathrm{d} \mu| : g \in L^{p'}, ||g||_{p'}=1 \}$. Moreover, if $\mu$ is semi-finite, then $||f||_{\infty} = \sup \{ |\int_{X} fg \ \mathrm{d} \mu| : g \in L^{1}, ||g||_{1}=1 \}$.

Proof. Define RHS as $\Phi(f)$. #TODO 

> [!important] Thm. 
> $S:=\{ f: f=\sum_{j=1}^{n} a_{j}\mathcal{X}_{E_{j}}, \mu(E_{j})<\infty \}$, $\mu$ is $\sigma$-finite,
> 1. If $0<p \le \infty$, then S is dense in $L^{p}$.
> 2. If $1 \le p \le \infty$, then $||f||_{p}=\sup \{ |\int_{X} fg \ \mathrm{d} \mu| : g \in S, ||g||_{p'}=1 \}$

Proof.
1. #NotCovered 
2. #TODO 

> [!note] Def. (Continuous func with compact support)
> - $C_{c}(X):=\{ f: X \to \mathbb{C} | f\text{ continuous}, supp\ f\text{ is compact} \}$, where $supp f:=\{x\in X | f(x) \ne 0 \}$.
> - $C_{c}^\infty(X):=\{ f \in C_{c}(X) | f \in C^{\infty} \}$.

> Prop. $C_{c}(\mathbb{R}^{n})$ is dense in $L^{p}(\mathbb{R}^{n})$ when $1 \le p <\infty$, but false when $p=\infty$.

Proof. #NotCovered 

> [!important] Thm. (Continuity of $L^{p}$ norm)
> $f \in L^{p}(\mathbb{R}), \lim_{t \to \infty} ( \int |f(x+t)-f(x)|^{p} \ \mathrm{d}m(x) )^{\frac{1}{p}}=0$.

Proof. #TODO 

