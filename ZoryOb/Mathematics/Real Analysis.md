Course MATH 540@UIUC

# Reference
- nabla: https://ppasupat.github.io/a9online/wtf-is/nabla.html

# Guide
> Took the class with him back in 2018. I would say his exams are pretty similar to the comps, for example: [https://math.illinois.edu/system/files/2021-02/MATH 540 - Jan 2021.pdf](https://math.illinois.edu/system/files/2021-02/MATH%20540%20-%20Jan%202021.pdf) . The homework from folland's book is kind of easy compare to the exams. I mean, this is a comprehensive exam class for the Math PhD people, so you shouldn't expect it to be any less, and real analysis is known to be hard for many people.

# Textbook
Gerald B. Folland, Real Analysis

# CH0
## Notation

# CH1 Measure theory
## 1.2 $\sigma$-algebra/field
Nota. (X) The universal set.
Def. (**Algebra** of sets of X) A non-empty collection $\mathcal{A}$ of subsets of X, satisfying:
1. $E_{1}, E_{2} \in \mathcal{A} \to E_{1} \cup E_{2} \in \mathcal{A}$.
2. $E\in \mathcal{A} \to E^{C} \in \mathcal{A}$.
Rmk. (a) Algebra is closed under finite intersection; (b) $\emptyset, X \in \mathcal{A}$.

Def. (**$\sigma$-algebra** of sets of X) A non-empty collection $\mathcal{A}$ of subsets of X, satisfying:
1. $E_{j} \in \mathcal{A} \to \bigcup_{j=1}^{\infty} E_{j} \in \mathcal{A}$.
2. $E\in \mathcal{A} \to E^{C} \in \mathcal{A}$.
E.g. $\mathcal{A}=\{ E\in X:\text{E is countable or all-but-countable} \}$.

Prop. $\mathcal{A}$ is a $\sigma$-algebra iff (a) $\mathcal{A}$ is a algebra; (b)$$E_{j} \text{ mutually disjoint}, E_{j}\in \mathcal{A} \to \bigcup_{j=1}^{\infty} E_{j} \in \mathcal{A}$$Proof. $\cup E_{j}=\cup_{j} [E_{j} \setminus (\cup_{k<j} E_{k})] \in \mathcal{A}$.

