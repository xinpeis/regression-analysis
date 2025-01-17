# Multivariate Normal Distribution

## Moment Generating Function

**Definition**: Let $X$ and $t$ be $n\times 1$ random vector and vector of constants, respectively. Then the *characteristic function* of $X$ is


$$
\phi_X(t)=\mathbb{E}(e^{it'X}).
$$


The *moment generating function (M.G.F.)* of $X$ is


$$
M_X(t) = \mathbb{E}(e^{t'X}).
$$


**Property 1.1**: Let $X$ and $Y$ be $n\times 1$ random vectors. $X$ and $Y$ are independent if and only if 


$$
\phi_{X + Y}(t) = \phi_X(t)\phi_Y(t)
$$


if and only if 


$$
M_{X + Y}(t) = M_X(t)M_Y(t).
$$


**Property 1.2**: Let $X$ and $Y$ be random vectors. $X$ and $Y$ are independent if and only if


$$
\phi_{X, Y}(t_1, t_2) = \phi_X(t_1)\phi_Y(t_2)
$$


if and only if 


$$
M_{X, Y}(t_1, t_2) = M_X(t_1)M_Y(t_2).
$$


*Note*: $\phi_{X, Y}(t_1, t_2) = \mathbb{E}(e^{i(t_1'X + t_2'Y)})$, and $M_{X, Y}(t_1, t_2) = \mathbb{E}(e^{t_1'X + t_2'Y})$.

**Fact**: If $X\sim\chi_r^2$, the M.G.F. of $X$ is


$$
M_X(t) = \frac{1}{(1 - 2t)^{r/2}}, t<\frac{1}{2}.
$$


**Example**: Let $Q_1\sim \chi_{r_1}^2$ and $Q_2\sim \chi_{r_2}^2$ where $(r_1 > r_2)$. If $Q = Q_1 - Q_2$ is independent of $Q_2$, show that $Q \sim \chi_{r_1-r_2}^2$.

**Solution**: Since $Q$ is independent of $Q_2$ and $Q_1 = Q + Q2$, we have


$$
M_{Q_1}(t) = M_Q(t)M_{Q_2}(t)\implies \frac{1}{(1 - 2t)^{r_1/2}} = M_Q(t)\frac{1}{(1 - 2t)^{r_2/2}}.
$$


Then we could derive that $M_Q(t) = \frac{1}{(1 - 2t)^{(r_1 - r_2)/2}}$, which is the M.G.F. of $\chi_{r_1 - r_2}^2$. Therefore, $Q\sim \chi_{r_1-r_2}^2$ by definition of M.G.F.

## Multivariate Normal Distributions

**Definition 2.1**: Let $Y$ be an $n\times 1$ random vector. We say $Y\sim \mathcal{N}_n(\mu, \Sigma)$ if $Y$ has the density


$$
f(y) = f(y_1, y_2, \dots, y_n) = k^{-1}\exp\Bigg\{-\frac{1}{2}(y - \mu)'\Sigma^{-1}(y - \mu)\Bigg\}
$$


where $k = (2\pi)^{n/2}\det(\Sigma)^{1/2}$, $\mu \in\mathbb{R}^n$, and $\Sigma\in\mathbb{R}^{n\times n}$ is positive definite.

*Special case*: A standard normal distribution $Y\sim\mathcal{N}_n(0, I_n)$ is a multivariate normal distribution with $\mu = 0$ and $\Sigma = I_n$.

**Theorem 2.1**: If $Y\sim\mathcal{N}_n(\mu, \Sigma)$, then $\mathbb{E}(Y) = \mu$ and $\text{var}(Y) = \Sigma$.

**Proof**: 

