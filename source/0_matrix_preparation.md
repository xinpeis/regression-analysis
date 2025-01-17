# Matrix Preparation

In this chapter, we will list some important concepts and properties of linear algebra we need for regression analysis and give proof for each of them.

## Trace and Eigenvalues

**Definition**: The trace of a square matrix $A$, denoted by $\text{tr}(A)$, is the sum of the elements on its main diagonal. It is only defined for a square matrix $(n\times n)$.

**Definition**: Consider an $n\times n$ matrix $A$ and a nonzero vector $v\in \mathbb{R}^n$. If multiplying $A$ with $v$ (denoted by $Av$) simply scales $v$ by a factor of $\lambda$, where $\lambda$ is a scalar, then $v$ is called an eigenvector of $A$, and $\lambda$ is the corresponding eigenvalue. This relation can be expressed as $Av = \lambda v$.

We assume all matrices are conformable (e.g. their dimensions are suitable for defined operations).

- $\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B)$

  **Proof**: $\text{tr}(A+B) = \sum_{i=1}^n A_{ii} + B_{ii} = \sum_{i = 1}^n A_{ii} + \sum_{i = 1^n} B_{ii} = \text{tr}(A) + \text{tr}(B)$.

- $\text{tr}(AC) = \text{tr}(CA)$

  **Proof**: Since trace is only defined on square matrices, without loss of generality, suppose $A, C\in\mathbb{R}^{n\times n}$. Then we have

  
  $$
  \text{tr}(AC) = \sum_{i=1}^n(AC)_{ii} = \sum_{i=1}^n\sum_{k=1}^nA_{ik}C_{ki} = \sum_{k=1}^n\sum_{i=1}^nC_{ki}A_{ik} = \sum_{k=1}^n(CA)_{kk} = \text{tr}(CA)
  $$
  
- If $A$ is an $n\times n$ matrix with eigenvalues $\lambda_i$ where $(i = 1, 2, \dots, n)$, then $\text{tr}(A)=\sum_{i=1}^n\lambda_i \text{ and } \det(A)=\prod_{i = 1}^n\lambda_i$.

  **Proof**: We prove this by [characteristic polynomial](https://en.wikipedia.org/wiki/Characteristic_polynomial#:~:text=In%20linear%20algebra%2C%20the%20characteristic,the%20matrix%20among%20its%20coefficients.). By expanding the characteristic polynomial by definition, we could get
  
  $$
  \begin{aligned}
  p(t) = \det(A - t I_n) & = (-1)^n(t - \lambda_1)(t-\lambda_2)\cdots(t-\lambda_n)\\
  & = (-1)(t - \lambda_1)(-1)(t - \lambda_2)\cdots(-1)(t - \lambda_n) \\
  & = (\lambda_1 - t)(\lambda_2 - t)\cdots(\lambda_n - t)
  \end{aligned}
  $$
  
  
  Then we could set $t = 0$ because it is just a variable, then we could get $\det(A)=\prod_i\lambda_i$.
  
  For trace of $A$, we write the characteristic polynomial in its vanilla format as
  
  
  $$
  p(t) = \det(A - tI_n) = (A_{11} - t)(A_{22} - t)\cdots(A_{nn} - t) + \cdots
  $$

  
  Then based on the [Vieta's formulas](https://en.wikipedia.org/wiki/Vieta%27s_formulas), the sum of the roots of the polynomial is the opposite of coefficient of its second highest terms. In our case, we consider the coefficient of $t^{n-1}$ terms and we ignore other terms. Notice that the after expanding the polynomial, each $\lambda_i$ will multiply $-t$ for $n - 1$ times, so we could find that the coefficient of $t^{n - 1}$ is $\sum_i-A_{ii}$, which is the $-\text{tr}(A)$. Since the roots of the $p(t)$ are eigenvalues $\lambda_1,\dots,\lambda_n$, we could conclude that $\sum_{i}\lambda_i=\text{tr}(A)$.
  
- *(Principal axis theorem)* If $A$ is an $n\times n$ symmetric matrix, then there exists an orthogonal matrix $T=(t_1, t_2, \dots, t_n)$ such that $T'AT=\Lambda$, where $\Lambda = \text{diag}(\lambda_1, \lambda_2, \dots, \lambda_n)$. Here the $\lambda_i$ are the eigenvalues of $A$, and $At_i=\lambda_i t_i$. The eigenvectors $t_i$ form an orthogonal basis for $\mathbb{R}^n$. The factorization $A = T\Lambda T'$ is known as the spectral decomposition of $A$.

  **Proof**: 


In next three results, we assume that $A$ is symmetric.

- $\text{tr}(A^s) = \sum_{i=1}^n\lambda_i^s$.
- If $A$ is nonsingular, the eigenvalues of $A^{-1}$ are $\lambda^{-1}_i$ for $i = 1, \dots, n$, and hence $\text{tr}(A^{-1})=\sum_{i=1}^n\lambda_i^{-1}$.
- The eigenvalues of $(I_n + cA)$ are $1 + c\lambda_i$ for $i = 1, \dots, n$.

## Rank

**Definition**: The rank of a matrix $A$ is the dimension of the vector space generated (or spanned) by its columns. This corresponds to the maximal number of linearly independent columns of $A$.

- If $A$ and $B$ are conformable matrices, then $\text{rank}(AB)\leq\min(\text{rank}(A), \text{rank}(B))$.
- If $A$ is any matrix, and $P$ and $Q$ are any conformable nonsingular matrices, then $\text{rank}(PAQ) = \text{rank}(A)$.
- Let $A$ be any $m\times n$ matrix such that $r=\text{rank}(A)$ and $s = \text{nullity}(A)$, [the dimension of $\mathcal{N}(A)$, the null space or kernel of $A$, i.e., the dimension fo $\{x:Ax=0\}$]. Then $r + s = n$.
- $\text{rank}(A) = \text{rank}(A') = \text{rank}(A'A) = \text{rank}(AA')$.
- If $\mathcal{C}(A)$ is the column space of $A$ (the space spanned by the columns of $A$), then $\mathcal{C}(A'A)=\mathcal{C}(A')$.
- If $A$ is symmetric, then $\text{rank}(A)$ is equal to the number of nonzero eigenvalues.
- Any $n\times n$ symmetric matrix $A$ has a set of $n$ orthonormal eigenvectors, and $\mathcal{C}(A)$ is the space spanned by those eigenvectors corresponding to nonzero eigenvalues.

## Positive-Semidefinite Matrices

**Definition**: A symmetric matrix $A$ is said to be positive-semidefinite (p.s.d) if and only if  $x'Ax\geq 0$ for all $x$.

- The eigenvalues of a p.s.d. matrix are nonnegative.
- If $A$ is p.s.d., then $\text{tr}(A)\geq 0$.
- $A$ is p.s.d. of rank $r$ if and only if there exists an $n\times n$ matrix $R$ of rank $r$ such that $A = RR'$.
- If $A$ is an $n\times n$ p.s.d. matrix of rank $r$, then there exists an $n\times r$ matrix $S$ of rank $r$ such that $S'AS = I_r$.
- If $A$ is p.s.d., then $X'AX = 0 \implies AX = 0$.

## Positive-Definite Matrices

**Definition**: A symmetric matrix $A$ is said to be positive-definite (p.d.) if  $x'Ax > 0$ for all $x$, $x\neq 0$.

- The eigenvalues of a p.d. matrix $A$ are all positive; thus $A$ is also nonsingular.
- $A$ is p.d. if and only if there exists a nonsingular $R$ such that $A = RR'$.
- If $A$ is p.d., then so if $A^{-1}$.
- If $A$ is p.d., then $\text{rank}(CAC')=\text{rank}(C)$.
- If $A$ is an $n\times n$ p.d. matrix and $C$ is $p\times n$ of rank $p$, then $CAC'$ is p.d.
- If $X$ is $n\times p$ of rank $p$, then $X'X$ is p.d.
- $A$ is p.d. if and only if all the leading minor determinants of $A$ [including $\det(A)$ itself] are positive.
- The diagonal elements of a p.d. matrix are all positive.
- If $A$ is an $n\times n$ p.d. matrix and $B$ is an $n\times n$ symmetric matrix, then $A - tB$ is p.d. for $|t|$ sufficiently small.
- *(Cholesky decomposition)* If $A$ is p.d., there exists a unique upper triangular matrix $R$ with positive diagonal elements such that $A=RR'$.
- If $L$ is positive definite, then for any $b$, $\max_{h:h\neq 0}\{\frac{(h'b)^2}{h'Lh}\}=b'L^{-1}b$.
- *(Square root of a positive-definite matrix)* If $A$ is p.d., there exists a p.d. square root $A^{1/2}$ such that $(A^{1/2})^2 = A$.

## Idempotent Matrices

**Definition**: A matrix $P$ is idempotent if $P^2 = P$.

**Definition**: A symmetric idempotent matrix is called a *projection matrix*.

- If $P$ is symmetric, then $P$ is idempotent of rank $r$ if and only if it has $r$ eigenvalues equal to unity and $n - r$ eigenvalues equal to zero.
- If $P$ is a projection matrix, then $\text{tr}(P)=\text{rank}(P)$.
- If $P$ is idempotent, so is $I - P$.
- Projection matrices are positive definite.
- If $P_1, P_2$ are projection matrices and $P_1 - P_2$ is p.s.d., then
  - $P_1P_2 = P_2P_1 = P_2$,
  - $P_1 - P_2$ is a projection matrix.

## Vector Differentiation

