# Matrix Preparation

In this chapter, we will list some important concepts and properties of linear algebra we need for regression analysis and give proof for each of them.

## Trace and Eigenvalues

We assume all matrices are conformable (e.g. their dimensions are suitable for defined operations).

- $\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B)$

  **Proof**: $\text{tr}(A+B) = \sum_{i=1}^n A_{ii} + B_{ii} = \sum_{i = 1}^n A_{ii} + \sum_{i = 1^n} B_{ii} = \text{tr}(A) + \text{tr}(B)$.

- $\text{tr}(AC) = \text{tr}(CA)$

  **Proof**: Since trace is only defined on square matrices, without loss of generality, suppose $A, C\in\mathbb{R}^{n\times n}$. Then we have

  
  $$
  \text{tr}(AC) = \sum_{i=1}^n(AC)_{ii} = \sum_{i=1}^n\sum_{k=1}^nA_{ik}C_{ki} = \sum_{k=1}^n\sum_{i=1}^nC_{ki}A_{ik} = \sum_{k=1}^n(CA)_{kk} = \text{tr}(CA)
  $$
  

- If $A$ is an $n\times n$ matrix with eigenvalues $\lambda_i$ where $(i = 1, 2, \dots, n)$, then

  
  $$
  \text{tr}(A)=\sum_{i=1}^n\lambda_i \text{ and } \det(A)=\prod_{i = 1}^n\lambda_i
  $$
  

  **Proof**: We prove this by [characteristic polynomial](https://en.wikipedia.org/wiki/Characteristic_polynomial#:~:text=In%20linear%20algebra%2C%20the%20characteristic,the%20matrix%20among%20its%20coefficients.). By expanding the characteristic polynomial by definition, we could get

  
  $$
  \begin{aligned}
  \det(A - t I_n) = p(t) & = (-1)^n(t - \lambda_1)(t-\lambda_2)\cdots(t-\lambda_n)\\
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

- *(Principal axis theorem)* If $A$ is an $n\times n$ symmetric matrix, then there exists an orthogonal matrix $T=(t_1, t_2, t_3, \dots, t_n)$ such that $T'AT=\Lambda$, where $\Lambda = \text{diag}(\lambda_1, \lambda_2, \dots, \lambda_n)$. Here the $\lambda_i$ are the eigenvalues of $A$, and $At_i=\lambda_i t_i$. The eigenvectors $t_i$ form an orthogonal basis for $\mathbb{R}^n$. The factorization $A = T\Lambda T'$ is known as the spectral decomposition of $A$.

In next three results, we assume that $A$ is symmetric.

- $\text{tr}(A^s) = \sum_{i=1}^n\lambda_i^s$.
- If $A$ is nonsingular, the eigenvalues of $A^{-1}$ are $\lambda^{-1}_i$ for $i = 1, \dots, n$, and hence $\text{tr}(A^{-1})=\sum_{i=1}^n\lambda_i^{-1}$.
- The eigenvalues of $(I_n + cA)$ are $1 + c\lambda_i$ for $i = 1, \dots, n$.

## Rank

## Positive-Semidefinite Matrices

## Positive-Definite Matrices

## Idempotent Matrices

## Vector Differentiation

