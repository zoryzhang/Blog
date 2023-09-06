---
link: https://zoryzhang.notion.site/Linear-algebra-f72508632ac44d17b16ad8a2940fa662
notionID: f7250863-2ac4-4d17-b16a-d8a2940fa662
---

Course MATH 416 Honor@UIUC
# Textbook
- [Linear Algebra via Exterior Products](https://github.com/winitzki/linear-algebra-book) (2020)
- [Linear Algebra Done Right](https://linear.axler.net/) (2023)
- [Linear Algebra Done Wrong](https://sites.google.com/a/brown.edu/sergei-treil-homepage/linear-algebra-done-wrong) (2021)
- [Linear Algebra (Stephen H. Friedberg, Arnold J. Insel etc.)](https://www.pearson.com/en-us/subject-catalog/p/linear-algebra/P200000006185/9780137515424) (2021) [main]

# Reminder
1. Carefully look at "dependent" or "independent".

# Ch1 Vector Spaces
Def. (**Vector space** V on field F) A non-empty set with vector addition and scalar multiplication, with the following axioms:
1. Additive commutativity;
2. Additive and scalar multiplicative associativity;
3. Additive identity and scalar multiplicative identity;
4. Additive inverse;
5. Vector and scalar additive distributivity.

Rmk. This definition gives rise to a few special vector space, e.g. $\mathbb{R}^{n}$ and $\mathcal{P^{n}}$, which will compose others by standard procedure introduced later.

Prop. Cancellation rule. By playing inverse (rule 4).

Cor. $\exists ! \underline {0}$.

Cor. $\exists ! \underline {-x}$.

Cor. 
a) $0 \cdot \underline {x} = \underline {0}$; 
b) $(-\lambda) \cdot \underline {x} = - (\lambda \underline {x}) = \lambda \cdot \underline {-x}$; 
c) $\lambda \cdot \underline {0}=\underline {0}$.

Def. (**Subspace** W of vector space V) A non-empty subset of V, such that:
1. $\underline {0} \in W$;
2. Closed under vector addition and scalar multiplication.

Prop. Subspace is closed under arbitrary intersection.

Def. (**Span**) For a set $S \subset V$, $span(S):=\bigcap_{S \subset \text{subspace } W \subset V} W$.

Prop. $span(S)$ is the set of linear combination of elements in $S$.

Def. (**Linear dependent**) n distinct $s_{i}$, exists $\lambda_{1}\dots \lambda_{n}$ are not all zero, such that $\sum \lambda_{i} s_{i}=0$.

Thm. $S$ are linear independent set of vectors, $v \in V \setminus S$, then $S \cup \{v\}$ are linear dep. iff $v \in span(S)$.

Def. (**Basis**) Minimal (defined in a subset sence, not size sence) spanning set.

Cor. $span(S)=V$, then it's basis iff it's linear indep.

Thm. (**Replacement thm**) V has a basis $s_{1}, \dots, s_{n}$ of size n, let $\{ x_{1}, \dots, x_{i} \}$ of size i be linear indep. and $i \le n$, then $\{ x_{1}, \dots, x_{i}, s_{i+1}, \dots, s_{n} \}$ (some of si is replaced by xi) is a basis.

Cor. card(linear indep) <= card(basis) <= card(spanning set)

Cor. Basis has the same cardinality.

Cor. If $|S|=\dim V$, then TFAE: a) spanning; b) linear indep; c) basis.

Cor. $W \subset V, \dim W \le \dim V$, then $\dim W = \dim V$ iff $W=V$.

# Ch2. Linear Transformations and Matrices


# Ch3. Elementary Matrix Operations and Systems of Linear Equations




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