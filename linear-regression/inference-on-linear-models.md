# Inference on Linear Models

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X \in \mathbf{R}^{k+1}$$.&#x20;

We already assume that&#x20;

1. $$E[X U]=0$$
2. $$E\left[X X^{\prime}\right]<\infty$$&#x20;
3. No perfect collinearity in $$X$$
4. $$\operatorname{Var}[X U]<\infty$$

Under these assumptions, we establish the asymptotic normality of the OLS estimator $$\hat{\beta}$$,

$$
\sqrt{n}(\hat{\beta}-\beta) \stackrel{d}{\rightarrow} N(0, \mathbb{V})
$$

with

$$
\mathbb{V}=\left(E\left[X X^{\prime}\right]\right)^{-1} E\left[X X^{\prime} U^2\right]\left(E\left[X X^{\prime}\right]\right)^{-1}
$$

We also described a consistent estimator $$\hat{\mathbb{V}}_n$$ of the limiting variance $$\mathbb{V}$$. **We develop methods for inference under the assumption that** $$E\left[X X^{\prime} U^2\right]$$ **is non-singular.**

