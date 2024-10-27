# Matrix Preparation

In this chapter, we will list some important concepts and properties of linear algebra we need for regression analysis and give proof for each of them.

## Trace and Eigenvalues

We assume all matrices are conformable (e.g. their dimensions are suitable for defined operations).

- $\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B)$

- $\text{tr}(AC) = \text{tr}(CA)$

  **Proof**: Since trace is only defined on square matrices, without loss of generality, suppose $A, C\in\mathbb{R}^{n\times n}$. Then we have

  
  $$
  \text{tr}(AC) = \sum_{i=1}^n(AC)_{ii} = \sum_{i=1}^n\sum_{k=1}^nA_{ik}C_{ki} = \sum_{k=1}^n\sum_{i=1}^nC_{ki}A_{ik} = \sum_{k=1}^n(CA)_{kk} = \text{tr}(CA)
  $$
  

- If $A$ is an $n\times n$ matrix with eigenvalues $\lambda_i$ where $(i = 1, 2, \dots, n)$, then

  
  $$
  \text{tr}(A)=\sum_{i=1}^n\lambda_i \text{ and } \det(A)=\prod_{i = 1}^n\lambda_i
  $$
  

  **Proof**: We prove this by [characteristic polynomial](https://en.wikipedia.org/wiki/Characteristic_polynomial#:~:text=In%20linear%20algebra%2C%20the%20characteristic,the%20matrix%20among%20its%20coefficients.). By expanding the 

## Rank

## Positive-Semidefinite Matrices

## Positive-Definite Matrices

## Idempotent Matrices

## Vector Differentiation
