# Properties of LS

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that the first component of $$X$$ is a constant equal to one. Let $$\beta \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

We assume that our model satisfies the following conditions:

1. $$E[X U]=0$$
2. $$E\left[X X^{\prime}\right]<\infty$$
3. There is no perfect collinearity in $$X$$

Denote the marginal distribution of $$(Y,X)$$ by $$P$$. And let $$\left(Y_1, X_1\right), \ldots,\left(Y_n, X_n\right)$$ be an i.i.d. sample of random vectors with distribution $$P$$.

And the properties we will discuss next are:

* Bias
* Gauss-Markov Theorem
* Consistency
* Asymptotic Normality

## Bias

### Unbiasedness

Under the first assumption, $$E[U \mid X]=0$$ (i.e., $$E[Y \mid X]=X^{\prime} \beta$$) it follows that $$E[\hat{\beta}]=\beta$$







### Biasedness from Omitted Variable

If $$\mathbb{E}[\hat{\beta}] \neq \beta$$, then $$\hat{\beta}$$ is biased, $$\text{bias}(\hat{\beta}) = \mathbb{E}[\hat{\beta}] - \beta$$, this may because of the omitted variable (some related variable).

* If $$\operatorname{bias}(\hat{\beta}) > 0$$: $$\hat{\beta}$$ is overestimated.
* If $$\operatorname{bias}(\hat{\beta}) < 0$$: $$\hat{\beta}$$ is underestimated.

For example, in a regression about factors that affects wage:&#x20;

$$
\text { wage }=\beta_0+\beta_1 \text { edu}+u
$$

We regressed wage on the education level (edu). However, there are other factors that may not be independent of the education level that also affects wage, like ability, motivation, .etc. So in this example, we have $$\operatorname{Cov}(e d u, u) \neq 0$$, therefore, this will lead to the biased estimation of $$\beta_1$$.

To calculate the omitted variable bias, we can use the following steps:

1. Build a long regression: $$Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+e$$, where $$\mathbb{E}\left[X_1 e\right]=0, \mathbb{E}\left[X_2 e\right]=0$$
2. Build a short regression: $$Y=X_1^{\prime} \gamma_1+u$$, where $$\mathbb{E}\left[X_1 u\right]=0$$
3. By the formula of OLS, we have that:

$$
\begin{aligned} \gamma_1& =\mathbb{E}\left[X_1X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1Y\right] \\ & =\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1\left(X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+e\right)\right] \\ & =\beta_1+\left[\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 X_2^{\prime}\right] \beta_2\right]+\left[\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 e\right]\right] \end{aligned}
$$

As $$\mathbb{E}\left[X_1 e\right]=0$$, and denote $$\Gamma_{12}$$ as $$\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 X_2^{\prime}\right]$$, we can have that:

$$
\gamma_1 =\beta_1+\Gamma_{12} \beta_2
$$

Note that:

*

## Gauss-Markov Theorem



## Consistency



## Asymptotic Normality

