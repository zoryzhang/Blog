>  The note of UIUC course MATH 540 Real Analysis in Fall 2023, by Zory Zhang. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (maybe not up-to-date) can be found [here](real%20analysis.pdf).

# Reference
- nabla: https://ppasupat.github.io/a9online/wtf-is/nabla.html

# Guide
> Took the class with him back in 2018. I would say his exams are pretty similar to the comps, for example: [https://math.illinois.edu/system/files/2021-02/MATH 540 - Jan 2021.pdf](https://math.illinois.edu/system/files/2021-02/MATH%20540%20-%20Jan%202021.pdf) . The homework from folland's book is kind of easy compare to the exams. I mean, this is a comprehensive exam class for the Math PhD people, so you shouldn't expect it to be any less, and real analysis is known to be hard for many people.

# Textbook
Gerald B. Folland, Real Analysis
[Sol1](https://people.umass.edu/bban/Solutions.html), [Sol2](https://www.math.wustl.edu/~sawyer/m5051f09/hwindex.html)

# Ch0 Preliminaries

## High level techniques
1. When we want to show an inequality related to measure, it's usually easier to enlarge it, since the subadditivity is giving you more terms during enlarging. Otherwise, you need to organize your terms and take a pair of it to apply subadditivity. Also, during enlarging, you can directly drop unnecessary terms in intersection, due to monotonicity.

## Reminder
- Do algebra with $\mu(E)$ carefully, since it can be infinity.

## Notation
- X: (in plain text) the universal set.
- $\mathcal{E}$: (mathcal in tex) a collection of subsets.
- $A, E$: (in tex) a set.
- $\mathcal{P}(X)$: the power set $\{E:E\subset X\}$.
- $\cup A_{j}$ can be finite, countable, or arbitrary union(same for other symbols like summation/intersection) and should be clear in context. Arbitrary union usually will be stressed by using $\cup_{\alpha}^{\infty} A_{\alpha}$.
- ":=" means this is definition, or can be done by definition.
## Set theory
Nota. $A \subset B$: A can be equal to B.

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

# Ch1 Measure theory
## 1.2 Basic algebra structure
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

> Lemma. (1.1) $\mathcal{E\subset M(F) \implies M(E) \subset M(F)}$.

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
> We ask for $\mathcal{B}_{\mathbb{R}^{n}} = \bigotimes_{j=1}^{n} \mathcal{B}_{\mathbb{R}}$. This definition enables it by: let $\{X_{\alpha}\}_{\alpha \in A}$ be an indexed collection of nonempty sets, $X:=\prod_{\alpha \in A} X_{\alpha}$, $\pi_{\alpha}: X \to X_{\alpha}$ the coordinate maps, and $\mathcal{M}_{\alpha}$ is a $\sigma$-algebra on $X_{\alpha}$, then define $\bigotimes \mathcal{A_{\alpha}}:=\{ \pi_{\alpha}^{-1}(E_{\alpha}):E_{\alpha} \in \mathcal{M}_{\alpha}, \alpha \in A \}$.

#NotCovered Prop 1.1-1.6

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
> 
> [!note] Def. (**$\sigma$-finite measure**) $X=\bigcup E_{j}, s.t., \forall j, \mu(E_{j})<\infty$.
> 
> [!note] Def. (**Semifinite measure**) $\forall E\in \mathcal{M}, \mu(E)=\infty \to (\exists F \subset E, 0<\mu(F)<\infty)$ .
> 
> [!note] Def. (**Null set and "almost everywhere (a.e.)"**) E is a null set if $\mu(E)=0$. Proposition A is true almost everywhere if it is true on all but null set.

E.g. Given $f: X \to [0,\infty]$, we can define a measure by $\mu(E)=\sum_{x \in E} f(x)$.
1. It's semifinite iff $f(x)<\infty$.
2. It's $\sigma$-finite iff it's semifinite and $\{x:f(x)>0\}$ is countable.
3. It's called **counting measure** if for some $x_{0}\in X$, $f(x)=\mathbb{1}(x=x_{0})$.
4. It's called **point mass or Dirac measure** if $f(x)=1$.

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
> [!note] Def. (**Continuity of general measure**) $\mu$ is continuous if $\forall \{A_{n}\}, A_{n} \to A, n \to  \infty \longrightarrow \lim_{n \to  \infty} \mu(A_{n}) = \mu(\lim_{n \to  \infty} A_n):=\mu(A)$. Notice the closeness under union&intersection gives that $A:=\limsup_{n}A_{n} \in \mathcal{F}$.

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
> $$
\begin{aligned}
\mu^{*}(E\cap B_{n})
&=\mu^{*}(E\cap B_{n}\cap A_{n})+\mu^{*}(E\cap B_{n}\cap A_{n}^{c}) \\
\text{given disjoint}, &=\mu^{*}(E\cap A_{n})+\mu^{*}(E\cap B_{n-1}) \\
\text{by induction}, &= \sum_{i=1}^{n} \mu^{*}(E\cap A_{i})
\end{aligned}
$$
> The above result can be extended to infinite sum since only one side is needed given subadditivity.

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
1. The collection $\mathcal{M}_\mu$ of $\mu^{*}$-measurable in Caratheodory's thm is the largest (in fact strictly larger than $\mathcal{B_\mathbb{R}}$, denoted as $\mathcal{E}$) gives the domain of the completion of $\mu_{F}$ (Ex22a), which is called the **Lebesgue-Stieltjes measure** associated to F.
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

> Prop. (1.20) If $E \in \mathcal{E}, \mu(E)<\infty$, then $\forall \epsilon>0, \exists A$ that is a finite union of open intervals such that $\mu(E \bigtriangleup A) < \epsilon$.

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
Motiv. $f^{-1}(E)=\{ x \in X:f(x) \in E \}$ preserves unions, intersections, and complements. $f^{-1}(\mathcal{B})$ and $\mathcal{M}=\{ E \in \mathcal{B} : f^{-1}(E) \in \mathcal{A} \}$ are $\sigma$-algebra.

> [!note] Def. (**Measurable function**) 
> Measurable space $(X, \mathcal{A}), (Y, \mathcal{B})$, we say $f:X \to Y$ is $(\mathcal{A,B})$-measurable if $\mathcal{f^{-1}(\mathcal{B}) \subset A}$, or equivalently, $\mathcal{M} \supset \mathcal{B}$.

Rmk. 
1. Random variables are special cases of measurable function.
2. Composition of measurable mappings are measurable.
3. For $E \in \mathcal{A}$, the indicator function $\mathbb{1}_{E}$ or $\mathcal{X}_{E}$ is $\mathcal{A}$-measurable.

> Prop. (2.1) $f:X \to Y$ is $(\mathcal{A,B})$-measurable iff $\mathcal{M} \supset \mathcal{B_{0}}$, where $\mathcal{M}( B_{0})=\mathcal{B}$.

Proof. $\mathcal{M}$ is a $\sigma$-algebra, and $\mathcal{M \supset B_{0}} \implies \mathcal{M \supset \mathcal{M}( B_{0})=B}$.

> Cor. Let X, Y be metric or topological spaces, then every continuous $f:X \to Y$ is $(\mathcal{B}_{X},  \mathcal{B}_{Y} )$-measuable.

Proof. Recall that $f:X \to Y$ is continuous on X iff for any open set U in Y, $f^{-1}(U)$ is open in X. By prop 2.1, it follows.

> [!important] Thm. (2.3)
> Based on prop 1.2 and 2.1, T.F.A.E:
> 1. $f:X \to \mathbb{R}$ is $\mathcal{A}$-measuable.
> 2. $\{(a, \infty): \forall a \in \mathbb{R}\} \subset \mathcal{M}$.
> 3. $\{[a, \infty): \forall a \in \mathbb{R}\} \subset \mathcal{M}$.
> 4. $\{(-\infty, a): \forall a \in \mathbb{R}\} \subset \mathcal{M}$.
> 5. $\{(-\infty, a]: \forall a \in \mathbb{R}\} \subset \mathcal{M}$.
> 6. If $f: X \to \bar{ \mathbb{R}}$, change the above as including infinity.

> [!note] Def. (**Measurable on subset of X**)
> $f$ is measurable on $E \in \mathcal{M}$, if $f|_{E}$ is $\mathcal{M}_{E}$-measurable, i.e. $\forall B \in \mathcal{B}_{ \mathbb{R}}, f^{-1}(B) \cap E \in \mathcal{M}$.

> [!important] Prop. (2.4)
> Let $(X, \mathcal{M})$ and $(Y_{\alpha}, \mathcal{N}_{\alpha})$ be measurable spaces, and $Y:=\prod_{\alpha} Y_{\alpha}, \mathcal{N}:=\otimes \mathcal{N}_{\alpha}$, and $\pi_\alpha$ the coordinate maps. Then $f:X \to Y$ is measurable iff $f_{\alpha}:=\pi_{\alpha} \circ f$ is $(\mathcal{M, N_\alpha})$-measurable for all $\alpha$.

Cor. $f: X \to \mathbb{C}$ is measurable iff $Re f, Im f$ are measurable.

> [!important] Thm. (2.6)
> If $f, g: X \to \mathbb{C}$ are $\mathcal{A}$-measurable, then $f+g, fg$ are $\mathcal{A}$-measurable.

Proof. Work on level sets. Consider $fg=\frac{1}{2}((f+g)^{2} -f^{2} -g^{2})$.

> [!note] Def. 
> $\mathcal{B}_{\bar{\mathbb{R}}}=\{ E \subset \bar{\mathbb{R}} : E \cap \mathbb{R} \subset \mathcal{B}_{\mathbb{R}} \}$. 

> [!important] Prop. 2.7
> In $\bar{\mathbb{R}}$, $\liminf, \limsup$ exist. Let $\{f_{j}\}$ be a sequence of $\mathcal{A}$-measurable function, then $g_{1}=\sup f_{j}, g_{2}=\inf f_{j}, g_{3}=\limsup f_{j}, g_{4}=\liminf g_{j}$ are measurable. Thus, if $f,g$ are measurable, then $\max(f,g), \min(f,g)$ are measurable.

Proof. $\limsup_{j} = \inf_{k} \sup_{j>k}$.

Rmk. We prefer to work on $\bar{\mathbb{R}}$ from now on since the limsup and liminf always exists.

> [!note] Def. (Decomposition of real-valued func)
> $f^{+}:=\max (f(x),0),f^{-}:=\max (-f(x),0)$, then $f=f^{+}-f^{-}, |f|=f^{+}+f^{-}$. By Prop. 2.7, if f is measurable, so are $f^{+}, f^{-}$.

> [!note] Def. (Polar decomposition of complex-valued func)
> $f=(sgn f) |f|$, where $sgn z=\frac{z}{|z|}\mathbb{1}(z \ne 0)$. If f is measurable, so are $|f|, sgn (f)$.

Proof. 

> [!note] Def. (**Simple function**)
> A finite linear combination of $\mathbb{1}_{E}$ of sets in A as the E, i.e. $$f=\sum_{j=1}^{m} a_{j} \mathbb{1}_{E_{j}}, E_{j}\in \mathcal{A}$$

> [!important] Thm. (Standard representation)
> Any simply function can be written so that disjoint $\cup E_{j}=X$.

Proof. Simply function takes finite many values, say $z_{1}, z_{2}, \dots z_{n}$. Let $E_{j}:=f^{-1}(\{z_{j}\})$, which is disjoint. Let $E_{0}=X \setminus (\cup E_{j})$ and $a_{0}=0$, then $f(x)=\sum_{j=1}^{n} z_{j} \mathbb{1}_{E_{j}}(x)$ gives the existence of standard representation.

> [!important] Thm.
> If $f$ is $\mathcal{A}$-measurable, $f:X\to [0,\infty]$, then $\exists simple\ \{ \phi_{j} \}$ s.t. $\phi_{j} \nearrow$, $\forall x, \phi_{j}(x) \to f(x)$, and $\phi_{j} \to  f$ uniformly on any set on which f is bounded. 

Proof. 
1. Consider n as a parameter to control a partition over the codomain. For any n, define Dyatic intervals $I_{k,n}:=[k 2^{-n}, (k+1)2^{-n})$ for $k=0 \dots 2^{2n}$, and also let $F_{n}:=[2^{n}, \infty]$. Then $[0,\infty]=(\cup_{k} I_{k,n})\cup F_{n}$.
2. Define an approximation from below of $f$ on each intervals, i.e. $E_{k,n}:=f^{-1}(I_{k,n}), \phi_{n}(E_{k,n}):=k2^{-n}$. The same for $F_{n}$. Then in summary, $$\phi_{n}=\sum_{k=1}^{2^{2n}-1} k2^{-n} \mathcal{X}_{E_{k,n}}+2^{n} \mathcal{X}_{F_{n}} $$
3. Claim $\phi_{n} \le f$.
4. Claim $\phi_{n} \le \phi_{n+1}$.
5. Claim $\forall x \in [0,\infty] \setminus F_{n}, 0 \le f(x)-\phi_{n}(x) \le 2^{-n}$.
6. Claim $\forall x, \phi_{n}(x) \to f(x)$.
7. Claim $\forall A \subset X, s.t. f(A)\subset [0, \infty), \sup_{x \in A} |f-\phi_{n}| \to 0$.

## 2.2 Integration of non-negative func.
> [!note] Def. 
> 1. $L^{+}:=\{ \text{all } \mathcal{A}-\text{measurable } f: X \to [0,\infty] \}$;
> 2. For a simple func $\phi(x)=\sum_{j=1}^{n} a_{j} \mathbb{1}_{E_{j}}(x)$ with standard representation, define $\int_{X} \phi \ \mathrm{d} \mu:=\sum_{j=1}^{n} a_{j}\mu(E_{j})$; (Here $0 \cdot \infty=0$)
> 3. $\int_{A} \phi := \int_{X} \phi \mathcal{X}_{A} \ \mathrm{d} \mu$;
> 4. $\int_{X} f \ \mathrm{d} \mu:=\sup \{ \int_{X} \phi \ \mathrm{d} \mu \}$.

> [!important] Prop.
> For simple functions $\phi, \varphi$:
> 1. If $c>0$, then $\int c \phi \ \mathrm{d} \mu=c \int \phi \ \mathrm{d}\mu$;
> 2. $\int (\phi + \varphi) = \int \phi + \int \varphi$;
> 3. If $\varphi \le \phi$, then $\int \varphi \le \int \phi$;
> 4. $v: A \mapsto \int_{A} \phi \ \mathrm{d} \mu$ is a measure on $\mathcal{A}$.

Proof.
2. In standard form, $\phi=\sum_{j=1}^{n} a_{j} \mathbb{1}_{E_{j}},\varphi=\sum_{k=1}^{m} b_{k} \mathbb{1}_{F_{k}}$. Since $E_{j}=\cup_{k} (E_{j} \cap F_{k})$, we can have $\phi=\sum_{j=1}^{n} a_{j} \sum_{k} \mathbb{1}_{E_{j} \cap F_{k}}$, and similarly for $\varphi$. Then $$\begin{aligned}\int (\phi+\varphi)=\int (\sum_{j,k} (a_{j}+b_{k}) \mathcal{X}_{E_{j} \cap F_{k}})\\=\sum_{j,k} (a_{j}+b_{k}) \mu(E_{j} \cap F_{k})=\int \phi+\int \varphi\end{aligned}$$.
4. For disjoint $\{A_{k}\}$, $$\begin{aligned}v(\cup_{k=1}^{\infty} A_{k})=\int_{\cup A_{k}} \phi=\sum_{j=1}^{n} a_{j} \mu(\cup A_{k})=\sum_{j=1}^{n} a_{j} \sum_{k=1}^{\infty}\mu(A_{k})\\=\sum_{k=1}^{\infty} (\sum_{j=1}^{n} a_{j} \mu(A_{k}))=\sum_{k=1}^{\infty} \int_{A_{k}} \phi =\sum_{k=1}^{\infty}v(A_{k})\end{aligned}$$.

> [!important] Thm. Monotone convergence thm (MCT)
> If $f_{j} \in L^{+}, \{ f_{j}\} \nearrow$ and $\forall x, f_{n}(x) \to f(x)$, then $\int f=\lim_{n \to \infty} \int f_{n}$.

Proof. 

