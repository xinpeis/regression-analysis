# Vector of Random Variables

In this chapter, we will explore the expectation and covariance for a vector of random variables. Then we derive the function of a random vector as quadratic form and discuss its mean and variance. We also cover the independence of two random vectors.

## Expectation

**Definition 1.1**: Let $Z=(Z_{ij})$. The expectation of $Z$ is $\mathbb{E}(Z)=(\mathbb{E}(Z_{ij}))$.

**Theorem 1.1**: Let $Z$ be an $m\times n$ random matrix. Let $A$, $B$, and $C$ be $l\times m$, $n\times p$, and $l\times p$ matrices of constant, respectively. Then


$$
\mathbb{E}(AZB + C) = A\mathbb{E}(Z)B + c.
$$


**Proof**: We prove this based on the [linearity of expectation](https://brilliant.org/wiki/linearity-of-expectation/#:~:text=Linearity%20of%20expectation%20is%20the,of%20whether%20they%20are%20independent.) of a random variable (e.g. $\mathbb{E}(ax + b) = a\mathbb{E}(x) + b$)). 

**Corollary**: Let $X$ be an $m\times 1$ random vector. Then $\mathbb{E}(AX + C) = A\mathbb{E}(X) + C$.

## Covariance

**Definition 1.2**: Let $X$ and $Y$ be $m\times 1$ and $n\times 1$ random vectors, respectively. Then


$$
\text{cov}(X, Y) = (\text{cov}(X_i, Y_j))
$$


**Definition 1.3**: The *variance (dispersion) matrix* of $X$ is


$$
\text{cov}(X, X) = \text{var}(X) = \begin{bmatrix}
\text{var}(X_1) & \text{cov}(X_1, X_2) & \cdots & \text{cov}(X_1, X_n) \\
\text{cov}(X_2, X_1) & \text{var}(X_2) & \cdots & \text{cov}(X_2, X_n) \\
\vdots & \vdots & \ddots & \vdots \\
\text{cov}(X_n, X_1) & \text{cov}(X_n, X_2) & \cdots & \text{var}(X_n)
\end{bmatrix}.
$$


**Theorem 1.2**: Let $\mathbb{E}(X) = a$ and $\mathbb{E}(Y) = b$. Then


$$
\text{cov}(X, Y) = \mathbb{E}[(X - a)(Y - b)'] = \mathbb{E}(XY') - ab'.
$$


**Proof**: We prove this based on *Theorem 1.1* of [expectation](#expectation) and [definition of covariance](https://en.wikipedia.org/wiki/Covariance#Definition).


$$
\begin{aligned}
\text{cov}(X, Y) & = \mathbb{E}[(X - \mathbb{E}(X))(Y - \mathbb{E}(Y))'] \\
& = \mathbb{E}[(X - a)(Y - b)'] \\
& = \mathbb{E}[XY' - aY' - Xb' + ab'] \\
& = \mathbb{E}[XY'] - a\mathbb{E}[Y'] - \mathbb{E}[X]b' + ab' \\
& = \mathbb{E}[XY'] - ab' - ab' + ab' \\
& = \mathbb{E}[XY'] - ab'
\end{aligned}
$$


**Corollary**: $\text{var}(X) = \mathbb{E}(XX') - aa'$.

**Proof**: $\text{var}(X) = \text{cov}(X, X) = \mathbb{E}(XX') - aa'$.

**Theorem 1.3**: Let $X$ and $Y$ be $n\times 1$ random vectors. Let $A$ and $B$ be $m\times n$ matrices of constants. Then


$$
\text{cov}(AX, BY) = A\text{cov}(X, Y)B'
$$


**Proof**: We prove this in a similar way as *Theorem 1.2*. Suppose $\mathbb{E}(X) = a$ and $\mathbb{E}(Y) = b$.


$$
\begin{aligned}
\text{cov}(AX, BY) & = \mathbb{E}[(AX - \mathbb{E}(AX))(BY - \mathbb{E}(BY))'] \\
& = \mathbb{E}[(AX - Aa)(BY - Bb)'] \\
& = \mathbb{E}[AX(BY)'] - Aa(Bb)' \\
& = \mathbb{E}[AXY'B'] - Aab'B' \\
& = A\mathbb{E}[XY']B' - Aab'B' \\
& = A(\mathbb{E}[XY'] - ab')B' \\
& = A\text{cov}(X, Y)B'
\end{aligned}
$$


**Corollary**: $\text{var}(AX) = A\text{var}(X)A'$.

**Proof**: $\text{var}(AX) = \text{cov}(AX, AX) = A\text{cov}(X, X)A' = A\text{var}(X)A'$.

**Theorem 1.4**: Let $X$ be an $n\times 1$ random vector. Then $\text{var}(X)$ is non-negative definite. Furthermore, if no element of $X$ is a linear combination of the remaining elements (that is, there does not exist $a\in \mathbb{R}^n$, $a\neq 0$ and $b\in\mathbb{R}$ such that $a'X = b$ for all values of $X = x$), then $\text{var}(X)$ is positive definite.

**Proof**: Based previous corollary, given any $c\in \mathbb{R}^n$, since the variance is non-negative, we have


$$
0 \leq \text{var}(c'X) = c'\text{var}(X)c
$$


Then $\text{var}(X)$ is non-negative definite.

Based on the definition of variance, the equality holds if any only if $c = 0$ or $c'X = b$ when $c \neq 0$ for some $b\in \mathbb{R}$. Since our condition rules out the second possibility, $0 = \text{var}(c'X)$ if and only if $c = 0$. Therefore, $\text{var}(X)$ is positive definite.

## Quadratic Form

**Definition**: A function $f(x_1, x_2, \dots, x_n)$ is a *quadratic form* with matrix $A\in\mathbb{R}^{n\times n}$ in variables $X = (X_1, X_2, \dots, X_n)'$ if 


$$
\begin{aligned}
f(X) & = X'AX \\
& = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}X_iX_j
\end{aligned}
$$


### Mean of Quadratic Forms

**Theorem 1.5**: Let $X$ be an $n\times 1$ random vector and $A$ be a symmetric matrix of constants. Let $\mathbb{E}(X) = \mu$ and $\text{var}(X) = \Sigma$. Then


$$
\mathbb{E}(X'AX) = \text{tr}(A\Sigma) + \mu'A\mu.
$$


**Proof**: By definition, $\Sigma$ is symmetric. Then we have


$$
\begin{aligned}
\mathbb{E}[X'AX] & = \mathbb{E}\Bigg[\sum_{i = 1}^n\sum_{j = 1}^n a_{ij} X_i X_j\Bigg] \\
& = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}\mathbb{E}[X_iX_j] \\
& = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}\big(\text{cov}(X_i, X_j) + \mathbb{E}[X_i]\mathbb{E}[X_j]\big) \\
& = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}(\Sigma_{ij} + \mu_i\mu_j) \\
& = \sum_{i = 1}^n\sum_{j = 1}^n a_{ij}\Sigma_{ji} + \sum_{i = 1}^n\sum_{j = 1}^na_{ij}\mu_i\mu_j \\
& = \text{tr}(A\Sigma) + \mu'A\mu
\end{aligned}
$$


**Corollary**: Let $b$ be an $n\times 1$ vector of constants. Then


$$
\mathbb{E}((X - b)'A(X - b)) = \text{tr}(A\Sigma) + (\mu - b)'A(\mu - b).
$$


**Proof**: Since $b$ is constant, we have $\mathbb{E}(X - b) = \mathbb{E}(X) - b = \mu - b$ and $\text{var}(X - b) = \text{var}(X) = \Sigma$. Then apply *Theorem 1.5*, we could get the result.

**Example**: Let $X_1, X_2, \dots, X_n\overset{\text{i.i.d.}}{\sim}(\mu, \sigma^2)$. Find $\mathbb{E}(Q)$ for 


$$
Q = (X_1 - X_2)^2 + (X_2 - X_3)^2 + \cdots + (X_{n - 1} - X_n)^2
$$


**Solution**: Since $X_1 - X_2 = (X_1 - \mu) - (X_2 - \mu)$, $Q$ does not depend on $\mu$. We assume $\mu = 0$. Then we expand $Q$ to get the quadratic form


$$
Q = X_1^2 + 2\sum_{i = 2}^{n - 1}X_i^2 + X_n^2 - 2\sum_{i = 1}^{n - 1}X_iX_{i + 1} = X'AX
$$


where


$$
A = \begin{bmatrix}
1 & -1 & 0 & \cdots & 0 & 0 \\
-1 & 2 & -1 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & 2 & -1 \\
0 & 0 & 0 & \cdots & -1 & 1
\end{bmatrix}
$$


Then we apply *Theorem 1.5* to get $\mathbb{E}(Q) = \text{tr}(A\Sigma) = (2n - 2)\sigma^2$.

**Example**: Let $X$ be an $n\times 1$ random vector with $\mathbb{E}(X_i)=\mu$ and $\text{var}(X) = \Sigma$, where $\sigma_{ii} = \sigma^2$ and $\sigma_{ij} = \rho\sigma^2$ with ($0\leq \rho\leq 1$) for $i\neq j$. Show that


$$
\mathbb{E}(Q) = \sigma^2(1 - \rho)(n - 1)\text{ for }Q = \sum_{i = 1}^n(X_i -\bar{X})^2.
$$


**Solution**: Since $X_i - \bar{X} = (X_i - \mu) - \frac{1}{n}\sum_{i = 1}^n(X_i - \mu)$, $Q$ does not depend on $\mu$. We assume $\mu = 0$. Then we expand $Q$ to get the quadratic form


$$
Q = \sum_{i = 1}^n X_i^2 - 2\bar{X}\sum_{i = 1}^n X_i + n\bar{X}^2 = \sum_{i = 1}^n(1 - \frac{1}{n})X_i^2 + \sum_{i < j}-\frac{2}{n}X_iX_j = X'AX,
$$


where


$$
A = \begin{bmatrix}
1 - \frac{1}{n} & -\frac{1}{n} & \cdots & -\frac{1}{n} \\
-\frac{1}{n} & 1 - \frac{1}{n} & \cdots & -\frac{1}{n} \\
\vdots & \vdots & \ddots & \vdots \\
-\frac{1}{n} & -\frac{1}{n} & \cdots & 1 - \frac{1}{n}
\end{bmatrix}
$$
 

Also we have the variance matrix $\Sigma$ as


$$
\Sigma = \sigma^2 \begin{bmatrix}
1 & \rho & \cdots & \rho \\
\rho & 1 & \cdots & \rho \\
\vdots & \vdots & \ddots & \vdots \\
\rho & \rho & \cdots & 1
\end{bmatrix}
$$


Then we apply *Theorem 1.5* to get


$$
\mathbb{E}(Q) = \text{tr}(A\Sigma) = \sigma^2(1 - \rho)\text{tr}(A) = \sigma^2(1 - \rho)(n - 1).
$$


### Variance of Quadratic Forms

**Theorem 1.6**: Let $X_1, X_2, \dots, X_n$ be independent with means $\theta_1, \theta_2, \dots, \theta_n$, common variance $\mu_2$ and common third and fourth central moments $\mu_3$ and $\mu_4$ (that is, $\mu_k = \mathbb{E}((X_i - \theta_i)^k)$ for $k\in\mathbb{N}$), respectively. Let $A$ be an $n\times n$ symmetric matrix of constants and $a$ be a column vector of the diagonal of $A$. Then


$$
\text{var}(X'AX) = (\mu_4 - 3\mu_2^2)a'a + 2\mu_2^2\text{tr}(A^2) + 4\mu_2\theta'A^2\theta + 4\mu_3\theta'Aa.
$$


**Proof**: 

**Example**: Let $Z_i\overset{\text{i.i.d.}}{\sim}\mathcal{N}(0, \mu_2)$. Then $\mu_3 = 0, \mu_4 = 3\mu_2^2$. Then


$$
\text{var}(Z'AZ) = 2\mu_2^2\text{tr}(A^2).
$$


## Independence

**Definition**: Let $X$ and $Y$ be random vectors. Then $X$ and $Y$ are independent if and only if


$$
f_{X, Y}(x, y) = f_X(x)f_Y(y) \text{ or } F_{X, Y}(x, y) = F_X(x)F_Y(y) \text { for all }x, y.
$$


**Proposition**: If $X$ and $Y$ are independent, $\text{cov}(X, Y) = 0$.

**Proof**: Given that $X$ and $Y$ are independent, we have


$$
\begin{aligned}
\mathbb{E}(XY) & = \iint_{x,y}xyf_{X,Y}(x, y)dxdy \\
& = \iint_{x, y}xyf_X(x)f_Y(y)dxdy \\
& = \int_xxf_X(x)dx \cdot \int_yyf_Y(y)dy \\
& = \mathbb{E}(X)\mathbb{E}(Y)
\end{aligned}
$$


Then by *Theorem 1.2* in [expectation](#expectation), we have $\text{cov}(X, Y) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y) = 0$.

**Example**: Let $X\sim \mathcal{U}(-1, 1)$, and let $Y = X^2$. Then 


$$
\text{cov}(X, Y) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y) = \mathbb{E}(X^3) - \mathbb{E}(X)\mathbb{E}(X^2) = 0
$$


However, it is clear that $X$ and $Y$ are not independent. Therefore, we could derive a proposition

**Proposition**: If $X$ and $Y$ are independent, $\mathbb{E}(g(X)h(Y)) = \mathbb{E}(g(X))\mathbb{E}(h(Y))$. However, the opposite direction does not always hold.

