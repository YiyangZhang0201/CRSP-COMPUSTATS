# Linear Regression When E\[XU]=0

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$ and let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

We will make following three assumptions for this model.

1. $$E[X U]=0$$**: The justification of 1 varies depending on which of the three preceding interpretations we invoke.** This expectation refers to the covariance between the regressor $$X$$ and the error term $$U$$ being zero.
   1.  **For Linear Conditional Expectation:** In this interpretation, the regression is viewed as modeling the conditional expectation of $$Y$$ given $$X$$. That is, $$E[Y \mid X]=\beta_0+\beta_1 X$$.

       Here, $$U$$ represents the deviation of $$Y$$ from its conditional expectation given $$X$$. Since $$U$$ is defined as $$Y-E[Y \mid X]$$, it inherently means that $$E[U \mid X]= 0$$ . Consequently, this implies that $$E[X U]=0$$, because the error term $$U$$ has no systematic relationship with $$X$$ when considering the conditional expectation.
   2.  **For Best Linear Approximation:** In the best linear approximation, the regression equation is considered the best linear approximation to the true relationship between $$Y$$ and $$X$$, regardless of the true underlying relationship.&#x20;

       The error term $$U$$ in this context captures all factors that affect $$Y$$ but are not captured by $$X$$. For the linear approximation to be the 'best', it requires that these omitted factors (captured in $$U$$ ) are uncorrelated with $$X$$. **If** $$X$$ **were correlated with** $$U$$**, there would be systematic information in** $$X$$ **that could improve the approximation, contradicting the premise that the model is the 'best' linear approximation.** Hence, $$E[X U]=0$$ is necessary to ensure that the linear model is indeed the best approximation under the given circumstances.
   3.  **For Causal Model:** the regression is understood as modeling a causal relationship between $$X$$ and $$Y$$. Here, $$\beta_1$$ is interpreted as the causal effect of $$X$$ on $$Y$$.

       For $$\beta_1$$ to represent the causal effect of $$X$$ on $$Y$$, it is crucial that all other factors influencing $$Y$$ are either controlled for or are not correlated with $$X$$. The error term $$U$$ includes all these other factors. **If** $$U$$ **were correlated with** $$X$$**, it would mean that there are omitted variables that both affect** $$Y$$ **and are related to** $$X$$**, which would bias the estimation of the causal effect.** Therefore, ensuring $$E[X U]=0$$ is essential for a valid causal interpretation, as it implies that there are no omitted confounders that are correlated with $$X$$.
2. $$E\left[X X^{\prime}\right]<\infty$$**, this 2 ensures that** $$E\left[X X^{\prime}\right]$$ **exists.**
3.  **There is NO PERFECT COLLINEARITY in** $$X$$ or **the matrix** $$E\left[X X^{\prime}\right]$$ **is in fact invertible.**

    Since $$E\left[X X^{\prime}\right]$$ is positive semi-definite, invertibility of $$E\left[X X^{\prime}\right]$$ is equivalent to $$E\left[X X^{\prime}\right]$$ being positive definite. **This ensures there is a unique solution to** $$\beta$$ **when solving for it.**

We can talk more detail about Invertibility:

**Definition:**

There is perfect collinearity or multicollinearity in $$X$$ if there exists nonzero $$c \in \mathbf{R}^{k+1}$$ such that $$P\{c^{\prime} X=0\}=1$$, (Here we treat X as a random variable.), i.e., if we can express one component of $$X$$ as a linear combination of the others.

**Lemma:**

Let $$X$$ be such that $$E\left[X X^{\prime}\right]<\infty$$. Then $$E\left[X X^{\prime}\right]$$ is invertible iff there is no perfect collinearity in $$X$$.

**Proof**:

