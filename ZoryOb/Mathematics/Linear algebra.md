---
link: https://zoryzhang.notion.site/Linear-algebra-f72508632ac44d17b16ad8a2940fa662
notionID: f7250863-2ac4-4d17-b16a-d8a2940fa662
---
>  The note of UIUC course MATH 416 Honor Abstruct Linear Algebra in Fall 2023, by Zory Zhang. In case of any broken math renderring in Github preview, please open this markdown file using your own markdown editor. PDF version (maybe not up-to-date) can be found [here](linear%20algebra.pdf).

# Textbook
- [Linear Algebra via Exterior Products](https://github.com/winitzki/linear-algebra-book) (2020)
- [Linear Algebra Done Right](https://linear.axler.net/) (2023)
- [Linear Algebra Done Wrong](https://sites.google.com/a/brown.edu/sergei-treil-homepage/linear-algebra-done-wrong) (2021)
- [Linear Algebra (Stephen H. Friedberg, Arnold J. Insel etc.)](https://www.pearson.com/en-us/subject-catalog/p/linear-algebra/P200000006185/9780137515424) (2021) [main]

# Reminder
1. Carefully look at "dependent" or "independent".

# Notation
1.  $\epsilon_{n}$ is the standard basis of $F^{n}$.

# Ch1 Vector Spaces
## 1.2 Vector Space
> [!note] Def. (**Vector space** V on field F) 
> A non-empty set with vector addition and scalar multiplication, with the following axioms:
> 1. Additive commutativity;
> 2. Additive and scalar multiplicative associativity;
> 3. Additive identity and scalar multiplicative identity;
> 4. Additive inverse;
> 5. Vector and scalar additive distributivity.

Rmk. This definition gives rise to a few special vector space, e.g. $\mathbb{R}^{n}$ and $\mathcal{P^{n}}$, which will compose others by standard procedure introduced later.

Thm. (1.1 Cancellation law for vector addition) By playing inverse (rule 4).

Cor. 
a) $\exists ! \underline {0}$;
b) $\exists ! \underline {-x}$;
c) $0 \cdot \underline {x} = \underline {0}$; 
d) $(-\lambda) \cdot \underline {x} = - (\lambda \underline {x}) = \lambda \cdot \underline {-x}$; 
e) $\lambda \cdot \underline {0}=\underline {0}$.

## 1.3 Subspaces
> [!note] Def. (**Subspace** W of vector space V) 
> A non-empty subset of V, such that:
> 1. $\underline {0} \in W$;
> 2. Closed under vector addition and scalar multiplication.

Thm. (1.4) Subspace is closed under arbitrary intersection.

## 1.4 Linear combination
> [!note] Def. (**Span**) 
> For a set $S \subset V$, $span(S):=\bigcap_{S \subset \text{subspace } W \subset V} W$.

Rmk. If $S_{1} \subset S_{2}$, then $span(S_{1}) \subset span(S_{2})$.

Prop. $span(S)$ is the set of linear combination of elements in $S$.
## 1.5 Linear independence
> [!note] Def. (**Linear dependent**) 
> $n$ distinct $s_{i}$, there exists $\lambda_{1}\dots \lambda_{n}$ that are not all zero, such that $\sum \lambda_{i} s_{i}=0$.

Thm. $S$ are linear independent set of vectors, $v \in V \setminus S$, then $S \cup \{v\}$ are linear dep. iff $v \in span(S)$.

## 1.6 Bases and dimention
> [!note] Def. (**Basis**) 
> Minimal (defined in the subset inclusion sence, not in size sence) spanning set.

Cor. $span(S)=V$, then it's basis iff it's linear indep.

Thm. (**Replacement thm**) V has a basis $s_{1}, \dots, s_{n}$ of size n, let $\{ x_{1}, \dots, x_{i} \}$ of size i be linear indep. and $i \le n$, then $\{ x_{1}, \dots, x_{i}, s_{i+1}, \dots, s_{n} \}$ (some of si is replaced by xi) is a basis.

Cor. card(linear indep) <= card(basis) <= card(spanning set)

Cor. Basis has the same cardinality.

Cor. If $|S|=\dim V$, then TFAE: a) spanning; b) linear indep; c) basis.

Thm. (1.11) $W \subset V, \dim W \le \dim V$, then $\dim W = \dim V$ iff $W=V$.

Cor. $\dim V < \infty, W \subset V$, then W posseses a compliment.

> [!note] Def. (**Quotient space**) 
> Given subspace W, define $x \sim y$ if $x-y \in W$, $[x]:=\{ y: x \sim y \}=:\{ x+w| w \in W \}=:x+W$, and $\{ [x] \}:=V_{/W}$ is a vector space called quotient space, by the intuitive definition of addition and scalar multiplication: $[v]=[\sum \lambda_{i} s_{i}]:=\sum \lambda_{i} s_{i}$ and $\lambda[x]:=[\lambda x]$, e.g. $-[x]=[-x]$.

Prop. $\dim (V_{/W})=\dim V - \dim W$.

Thm. Given subspace W, there's a bijection between $\{H:subspace\ H, W \subset H\}$ and $\{ \bar H \in V_{/W}: subspace\ H\}$, where the $\bar H:=H_{/W}=\{[x]\in V_{/W}:x\in H\}$.

Rmk. This together with the usage of flags give another proof for Cor 1.11.

> [!note] Def. (**Direct sum**) 
> $W_{1} \oplus W_{2}$ if $W_{1}+W_{2}=V$ and $W_{1} \cap W_{2}=\emptyset$.

Cor. $\dim (W_{1}+W_{2})=\dim W_{1} + \dim W_{2} - \dim(W_{1} \cap W_{2})$, by showing $\dim \bar V = \dim \bar W_{1} + \dim \bar W_{2}$.

## 1.7 Maximal linear independent subset
> [!note] Def. (**Chain / nest / tower**) 
> A collection of elements that are totally ordered.

Thm. (**Hausdorff maximal principle / the axiom of choice**) Every partially ordered set has a maximal linearly / totally ordered subset. It's the same as the next thm.

Thm. (**Zorn's lemma**) For a partially ordered set $(X, \le)$, for any $C \subset X$ be totally ordered. Suppose $\exists x_{c} \in X, s.t., \forall x \in C, x \le x_{c}$ (every chain has a top), then $\exists x_{m}, s.t. , \forall y \in X, x_{m} \le y \to x_{m}=y$ (maximum exists).

> [!note] Def. (**Maximal linear independent set**) 
> Again, maximal with respect to set inclusion.

Lemma. A set is a maximal linear independent set iff it's a basis.

Thm. For any linearly independent subset S of a vector space V, there's a basis that contains S.

Proof. Construct X to be the collection of independent sets containing S. For any chain C in X, we need to find a top of it in X. This can be done by taking union of sets in C, which means it's a top and therefore containing S. Also, it's independent, since for any $u_{i}$ for $i=1 \dots n$, we can find a set in C such that it contains all these vectors, therefore they're linearly independent.

Cor. Every vector space has basis.

Thm. Subspace $W \subset V$, then $\exists W', s.t. V=W \oplus W'$.

# Ch2. Linear Transformations and Matrices

## 2.1 Rank-nullity
> [!note] Def. (**Linear map**) 
> $T:V \to W$.

Rmk. 
1. $T(0)=0$.
2. $Ker(T) \subset V, Ran(T) \subset W$ are subspaces, called **null space / kernel** and **range / image**, and their dimention is called **nullity** and **rank**.
3. (2.4) $T$ is 1-1 iff $Ker(T)=\{0\}$.

> [!important] Thm. (**Dimension thm**) 
> For linear $T:V \to W$, and V is finite-dimensional, then $nullity(T)+rank(T)=\dim(V)$.

Thm. T is isomorphic iff $\exists T^{-1}, s.t., T \circ T^{-1}=id_{V}. T^{-1} \circ T=id_{W}, T^{-1}\ linear$.

Thm. (2.19) $T:V \to W$, $\dim V=n<\infty$, then T is isomorphism iff $\dim W=n$.

Cor. Subspace $V' \subset V$, then $T|_{V'}:V' \to T(V')$ is still isomorphic.

Thm. $T:V \to W$ induces linear $\bar T: V_{/KerT}\to R(T)$ by letting $\bar T:=[x] \mapsto T(x)$.

Cor. $\dim V < \infty, \dim KerT + \dim R(T)=\dim V$.

Cor. If $V=R(T)+Ker(T)$, then it's direct sum. 

Ex. If $T \circ T=T$, then the above is true, and further more, $T=\pi_{R(T)}$.

Ex. Consider subspace $W' \subset W$, then $T^{-1}(W') \subset V$ is a subspace, and another induced linear quotient map $\bar T: V_{/ T^{-1}(W') }\to W_{/W'}$ can be given by $\bar T: [x] \to [T(x)]$. When T is onto, it's bijective.

## 2.2 Matrix and map

Lemma. For linear map $T:F^{n} \to F$, there's a unique tuple $(a_{i})$, such that $T(x)=\sum_{i=1}^{n} a_{i}x_{i}$. Constructively, $a_{i}=T(e_{i})$.

> [!important] Thm. 
> For linear map $T:F^{n} \to F^{m}$, there's a unique $m \times n$ matrix $A=(a_{ji})$ such that $T(x)=(T_{1}(x), T_{2}(x), \dots)$ and $T_{j}(x)=\sum_{j=1}^{n} a_{ji} x_{i}$. We use $L_{A}$ to refer to T. Further more, $T(e_{i})=(a_{1i}, a_{2i}, \dots)$ is the i-th column of A.

Rmk. We define matrix as a compact representation of a linear transformation between euclidean spaces. Matrix A is defined to be $[L_{A}]_{\epsilon_{n}}^{\epsilon_{m}}$.

> [!important] Thm. (2.20) 
> $T: V \to W$, V and W respectively possess ordered bases $\beta=(\beta_{1}, \beta_{2}, \dots, \beta_{n})$ and $\alpha=(\alpha_{1}, \alpha_{2}, \dots, \alpha_{m})$, then $T(\beta_{i})=\sum_{j=1}^{m}a_{ji} \alpha_{j}$. Further more, given $\beta,\alpha$, there's an isomorphism between T and $[T]_{\beta}^{\alpha}=(a_{ji})$. This can be done since $\phi_{\beta}: V \to F^{n}, \phi_{\alpha}: W \to F^{n}$, we have $L_{A} \phi_{\beta} = \phi_{\alpha} T$.

Ex. Given a complete flag $\mathcal{F}$: $\{0\} = V_{0} \subset V_{1} \subset \dots \subset V_{n}=V$ in V so that $\dim(V_{i} / V_{i-1})=1, \forall i$. We say T is **upper triangular** w.r.t. $\mathcal{F}$ if $T(V_{i}) \subset V_{i}, \forall i$. In this case, let $\beta$ be any ordered basis that can generate the flag, then matrix $[T]_{\beta}$ will also be **upper triangular** in matrix sense. At the same time, the induced quotient map $\bar T_{i} : V_{i} / V_{i-1} \to V_{i} / V_{i-1}, \bar T_{i}:[x]\mapsto [T(x)]$ is given by multiplication by a unique $\lambda_{i} \in F$. In this case, T is invertible iff $\forall i, \lambda_{i} \ne 0$, or $a_{ii} \ne 0$ for $[T]_{\beta}$. If invertible, $T^{-1}$ and $[T^{-1}]_{\beta}$ also upper triangular w.r.t. $\mathcal{F}$.

> [!important] Thm. (2.11) 
> $[S \circ T]_{\beta}^{\beta''} = [S]_{\beta'}^{\beta''} [T]_{\beta}^{\beta'}$.

> [!note] Def. (**Nilpotent**) 
> For a non-zero matrix A, it's called nilpotent if  $\exists n \in \mathbb{N}, s.t., A^{n}=0$.

> Prop. Multiplicative property of A: non-communative, no cancellation, and there exist nilpotent matrix.

> Prop. 
> If $T:V \to W, \dim V=\dim W=n$, T.F.A.E:
> 1. T is an isomorphism;
> 2. $\exists \beta$ as a basis of V, s.t. $T(\beta)$ is a basis of W.
> 3. $\forall \beta$ as a basis of V, $T(\beta)$ is a basis of W.

Proof. (1->3) We know $card(T(\beta)) \le n$, and since T is onto, $T(\beta)$ spans W.

>[!Important] Thm. (2.22 **Change of basis**)
>Say $\dim V=n$,
> 1. $A=[Id_{V}]_{\beta}^{\alpha} \in M_{n \times n}$ is invertible;
> 2. Fix $\beta / \alpha$, then any invertible A is $[Id_{V}]_{\beta}^{\alpha}$ for some unique $\alpha / \beta$.

Proof.
1. The inverse is $[Id_{V}]_{\alpha}^{\beta}$;
2. Say fix $\beta=(s_{1}, \dots, s_{n})$, for invertible $A=[A_{1}, \dots, A_{n}]$, find unique $\alpha=(t_{1}, \dots, t_{n})$. Let $\phi_{\beta}, \phi_{\alpha}: F^{n} \to V$ be the translation isomorphism. Since $\{ A_{j} \}$ is a basis of $F^{n}$, $\phi_{\beta}(\{ A_{j} \})$ is a basis of $F^{n}$. Let $t_{i}=\phi_{\beta}(A_{i})=\phi_{\beta}( L_{A}(e_{i}) )=\sum_{j} a_{ji} s_{j}$. Then we can write $Id(t_{i})=\sum_{j} a_{ji} s_{j}$, which means $[Id]_{\alpha}^{\beta}=A$, and so $[Id]_{\beta}^{\alpha}=A^{-1}$. 
3. So if we apply the above construction with $A^{-1}$ in place of $A$ to construct $\alpha'=\{ \phi_{\beta}(A_{i}^{-1}) \}$, then $[Id]_{\beta}^{\alpha'}=A$. This gives the existence of $\alpha$ in original statement.
4. If $[Id]_{\beta}^{\alpha}=[Id]_{\beta}^{\gamma}$, then $[Id]_{\alpha}^{\beta}=[Id]_{\gamma}^{\beta}$, and then $\alpha=\gamma$, which shows the uniqueness.

Rmk. $V \overset{T}{\to} W, \dim V=n, \dim W=m$, then $B:=[T]_{\beta'}^{\alpha'} = [Id_W]_{\alpha}^{\alpha'} [T]_{\beta}^{\alpha} [Id_V]_{\beta'}^{\beta}=:QAP$. This inspires an equivalence relation on $M_{m \times n}$, i.e., $A \sim B$ iff $B=[L_{A}]_{\beta'}^{\alpha'}$ for some ordered bases $\beta'$ of $V$ and $\alpha'$ for $W$.

> Prop. 
> If $rk (A)=r$, then there're invertible matrices P, Q s.t.
> $$
> PAQ
> =\begin{bmatrix}  I_{r} & 0 \\ 0 & 0 \end{bmatrix}
> \in M_{m \times n}$$
That means there's only $\min(n,m)$ many equivalence classes. Also, that means $rk A \le \min(n,m)$. This result will be justified later.

Proof. 
1. By replacement thm, we can pick $\alpha$ so that $R(L_{A})=span(t_{1}, \dots, t_{r})$. For $i \le r$, since $t_{i} \in R(L_{A})$, we can find $s_{i}$ s.t. $L_{A}(s_{i})=t_{i}$.
2. Claim $\{s_{i}\}_{i=1}^{r}$ are independent. Since $\bar L_{A}: F^{n} / ker(T) \to R(L_{A})$ is isomorphism and $R(L_{A})=span(t_{1}, \dots, t_{r})$, we have $\{[s_{i}]\}$ forming a basis in $F^{n} / ker(T)$.
3. Now let $W=span(s_{1}, \dots, s_{r})$. Claim $W \cap ker(L_{A})=0$, otherwise contradicts with the independence.
4. By rank-nullity, $F^{n}=W \oplus ker(L_{A})$. Merge them into one basis $\beta$ we seek.

## 2.3 Duality
> [!note] Def. (**Dual space**) 
> $V^{*}:=\mathcal{L}(V,F)$.

Rmk. 
1. $(F^{n})^{*} \cong F^{n}$. 
2. Further more, when $\dim V=n$ and a basis is given, $V^{*}:=\mathcal{L}(V, F) \cong \mathcal{L}(F^{n}, F)=:(F^{n})^{*} \cong F^{n}$.
3. Which means although the "all linear functionals" looks scary, the cardinality doesn't increase.

> [!note] Def. (**Dual basis**) 
> $s_{i}^{*}: V \to F$ defined by $s_{i}^{*}(s_{j})=\mathbb{1}(i=j)$. Then $\beta^{*}:=\{ s_{i}^{*} \}$ is a basis of $V^{*}$.

E.g. $e_{i}^{*}(e_{j})=\mathbb{1}(i=j)=:\delta_{ij}$. Then $e_{i}^{*}$ is the functional that essentially picks the i-th coordinate.

> [!note] Def. (**Dual map**) 
> $T^{*}: W^{*} \to V^{*}, T^{*}: \phi \mapsto \phi \circ T$. 

Rmk. $V(=span(\beta)) \overset{T}{\to} W(=span(\alpha)) \overset{\phi \in W^{*}}{\to} F$.

> [!Important] Thm. (Transpose)
  $A^{T}=[T^{*}]_{\alpha^{*}}^{\beta^{*}}$.

Proof. 
1. It suffices to show $T^{*}(t_{i}^{*})=\sum_{i} (A^{T})_{ji} s_{j}^{*}=\sum_{i} a_{ij} s_{j}^{*}$.
2. $T^{*}(t_{i}^{*})(s_{k})=t_{i}^{*} \circ T(s_{k})=t_{i}^{*}(\sum_{j} a_{jk}t_{j})=a_{ik}$.
3. $\sum_{i} a_{ij}s^{*}_{j}(s_{k})=a_{ik}$.

> Lemma. $rk T=rk L_{A}$. 

Proof. Since $R(T)=R(T \circ \varphi_{\beta})=R(\varphi_{\alpha}\circ L_{A})=R(L_{A})$.

> [!important] Thm.
> $rk A=rk A^{T}$.

Proof.
1. It suffices to show that $rk T=rk T^{*}$.
2. $ker T^{*}=\{ \varphi \in W^{*}: \varphi \circ T=0 \}$. Write $\varphi=\sum_{i} a_{i}t_{i}^{*}$.
3. $\varphi \circ T=0$ iff $\varphi(R(T))=0$, pick basis so that $R(T)=span(t_{1} \dots t_{r})$, then iff $a_{1} \dots a_{r}=0$ iff $ker T^{*}=span(t_{r+1} \dots t_{m})$. Then $rk T^{*}=rk T$.

> [!important] Thm. (Double dual)
> There's a canonical isomorphism between $V$ and $V^{**}$ that doesn't depends on choice of bases, given by $hat:V \to \mathcal{L}(V^{*}, F)$ and $hat: x \mapsto \hat x$, where $\hat x: V^{*} \to F$, $\hat x: \varphi \mapsto \varphi(x)$.

Proof.
1. $\hat x$ is linear;
2. $hat$ is linear;
3. $hat$ is bijective. The case of infinite dimension is #NotCovered . Otherwise, $\dim V^{**}=\dim V$, we need only 1-1 or onto. We show 1-1 here. Whenever $\hat x=0$, i.e. $\forall \varphi \in \mathcal{L}(V, F), \varphi(x)=0$. Suppose $\exists x_{0} \ne 0$ follows the above condition. When it's non-zero, one thing we can tell by replacement thm is that we can pick a basis in V as $\beta:=(x_{0}, \dots)$, then we got $x_{0}^{*}(x_{0})=1 \ne 0, x_{0}^{*} \in \mathcal{L}(V, F)$, contradicts.

Cor. If $\dim V<\infty$, then for any basis $\gamma$ of V*, there's a basis $\beta$ of V, s.t. $\beta^{*}=\gamma$.

Proof. It's nice to be able to regard linear transformation as elements of vector space. For $\gamma:=(\varphi_{1}, \dots)$, we can generate $\gamma^{*}:=(\varphi_{1}^{*}, \dots)$, and find unique $\beta:=(x_{1}, \dots), s.t. \hat x_{i}=\varphi_{i}^{*}$. It's what suggested by the notation since $\varphi_{i}(x_{j})=:\hat x_{j}(\varphi_{i})=\varphi_{j}^{*}(\varphi_{i}):=\delta_{ji}=\delta_{ij}$.

# Ch3. Elementary Matrix Operations and Systems of Linear Equations

> [!note] Def. (**System of linear equations**) 
> $A x=b$, where $x$ is the variable vector.

Prop. Given an invertible matrix P, then $A x=b$ iff $PAx=Pb$.

Rmk. Based on results from Ch2, we know the system of linear equations has a solution if $b \in R(L_{A})$. If so, i.e., $\exists s, s.t. As=b$, then the solution space as a preimage of b is $s + Ker L_{A}$.

> [!note] Def. (**Elementary operations on row**) 
> $A \in M_{m \times n}$,
> 1. Interchanging two rows;
> 2. Multiplying each element in a row by a non-zero number;
> 3. Adding a scalar $\lambda$ multiple of j-th row to i-row ($E=I_{m}+\lambda e_{ij}$, A'=EA).

Prop. Inverse and transpose of elementary matrix are still elementary.

Lemma. If $P, Q$ are invertible, then $rk(PAQ)=rk(A)$.

Proof. We can express PAQ into $[Id]_{\epsilon}^{\alpha} [L_{A}]_{\epsilon}^{\epsilon'} [Id]_{\beta}^{\epsilon'}$, where $\alpha, \beta$ can be given by thm2.22. Then $PAQ=[L_{A}]_{\beta}^{\alpha}$, and then $rk (PAQ)=rk(A)$.

> [!important] Thm. 
> There're invertible matrix P, Q that are product of elementary matrices, s.t. $PAQ=\begin{pmatrix} I_{r}& 0  \\ 0 & 0 \end{pmatrix}$.

Proof. Constructive induction. Transform A into $\begin{pmatrix} 1 & 0  \\ 0 & B \end{pmatrix}$, then $R(A)=span(e_{1}) \oplus R(B)$, and doing row and column transformations on B won't affect the first row and column, thus induction works. 

> Cor. Every invertible matrix in $M_{n \times n}$ is a product of elementary matrices.

Proof. $PAQ=I_{n}$, then $A=Q^{-1} I_{n} P^{-1}$ is a product of them.

> Cor. $rk A=rk A^{T}$. 

Proof. Since transposing $PAQ=\begin{pmatrix} I_{r}& 0  \\ 0 & 0 \end{pmatrix}$ gives $Q^{T} A^{T} P^{T}=\begin{pmatrix} I_{r}& 0  \\ 0 & 0 \end{pmatrix}$.

> Cor. $rk(AB) \le rk(A), rk(B)$. 

Proof. The first is trivial, and second is because $rk(AB)=rk(B^{T}A^{T}) \le rk(B^{T}) = rk(B)$.


---

# Eigenvalue

## Eigenvalue, eigenvector and movement
For a matrix $A_{n \times n}$, consider all $(\vec u,\lambda)$ pair such that: $A \vec u=\lambda \vec u$
We call them **eigenvalues** and **eigenvectors** of matrix A.
There're totally n pairs of $(\vec u_i, \lambda_i)$ for diagonalizable linear transformation, and the eigenvectors form a basis(some $\lambda_i$ might be the same).

If we regard matrix/transformation W as a space movement in Euclidean space, we need to apply it on certain vector to examine its feature. What if we try to apply it multiple times?
$$
\begin{aligned}
\vec v&=\sum_i \alpha_i \vec  u_i
\\
W^k \vec v
&=\sum_i \alpha_i  W^k \vec  u_i
=\sum_i \alpha_i  \lambda_i^k \vec  u_i
\end{aligned}
$$
We find out that the largest eigenvalue corresponding eigenvector will eventually dominate as k getting larger and larger. That's why we would like to conclude:
- first principle eigenvalue(largest) indicates the movement speed
- first principle eigenvector indicates the movement direction

e.g. 
When A is the adjacency matrix, $(A \vec v)_i = \frac 1 {deg_i }\sum_{j \in N(i)} v_j$
When $L=I-D^{-1}A$ , the Laplacian matrix, $(L \vec v)_i = \frac 1 {deg_i} \sum_{j \in N(i)} (v_i - v_j)$

## How to find them?
When the transformation A is normal operator, which means orthogonal diagonalizable, then:
$$
\begin{gather}
A=P \Lambda P^{-1}
\end{gather}
$$
where $\Lambda$ stretchs (eigenvalues), $P$ rotates (orthonormal eigenvectors).
Further more, when A is symmetric real matrix(e.g. adjacency and Laplacian matrix), then it is hermitian/self-adjoint, which means all eigenvalues are real.

## THM
Symmetric real matrix M
$M := \sum_{i}\lambda_{i} v_{i} v_{i}^T$, #TODO 
(upd) dim V=K
We may use the same eigenvectors in $M^k$, such that $M^k := \sum_{i}\lambda_{i}^k v_{i} v_{i}^T$
claim: $M^{-1} := \sum_{i} \frac{1}{\lambda_{i}} v_{i} v_{i}^{T} , M^{-1} M=I$
proof: substitute

thm2: $tr(M)=\sum_{i} \lambda_{i}$
https://courses.cs.washington.edu/courses/cse521/16sp/521-lecture-8.pdf

## Variational Characterization of Eigenvalues
$$
\begin{gather}
\text{symmetric real}\ M_{n \times n},\text{ eigenvalue}\ \lambda_1 \le \lambda_2 ... \le\lambda_n
\\
\text{Rayleigh quotient }R_M(\boldsymbol x)=\frac{\boldsymbol x^T M \boldsymbol x}{\boldsymbol x^T \boldsymbol x}
\\
\lambda_k = \min_{\forall V,\dim V=k} \max_{\boldsymbol x \in V-\{\boldsymbol 0\}} R_M(\boldsymbol x)
\end{gather}
$$
proof:
https://blog.csdn.net/a358463121/article/details/100166818


证明$V$里面一定存在向量使得Rayleigh quotient时，只需要取$\lambda_1,\lambda_2, ...,\lambda k$对应的$v1, v_2, ..., v_k$组成的空间$V$即可。
https://zhuanlan.zhihu.com/p/80817719


# Hilbert space
conjucture symmetric

## Reference
Basic knowledge in Spectral Theory.