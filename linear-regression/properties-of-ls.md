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

1. Build a long regression:
2. Build a short regression:&#x20;

## Gauss-Markov Theorem



## Consistency



## Asymptotic Normality

