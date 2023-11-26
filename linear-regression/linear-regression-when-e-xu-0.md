# Linear Regression When E\[XU]=0

## Assumptions for Linear Regression when E\[XU]=0

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
2.  $$E\left[X X^{\prime}\right]<\infty$$**, this 2 ensures that** $$E\left[X X^{\prime}\right]$$ **exists.**

    This matrix $$E\left[X X^{\prime}\right]$$ is called **Design Matrix**.
3.  **There is NO PERFECT COLLINEARITY in** $$X$$ or **the matrix** $$E\left[X X^{\prime}\right]$$ **is in fact invertible.**

    Since $$E\left[X X^{\prime}\right]$$ is positive semi-definite, invertibility of $$E\left[X X^{\prime}\right]$$ is equivalent to $$E\left[X X^{\prime}\right]$$ being positive definite. **This ensures there is a unique solution to** $$\beta$$ **when solving for it.** So, this is also called the **identification condition** for $$\beta$$**.**

We can talk more detail about Invertibility:

**Definition:**

There is perfect collinearity or multicollinearity in $$X$$ if there exists nonzero $$c \in \mathbf{R}^{k+1}$$ such that $$P\{c^{\prime} X=0\}=1$$, (Here we treat X as a random variable.), i.e., if we can express one component of $$X$$ as a linear combination of the others.

**Lemma:**

Let $$X$$ be such that $$E\left[X X^{\prime}\right]<\infty$$. Then $$E\left[X X^{\prime}\right]$$ is invertible iff there is no perfect collinearity in $$X$$.

**Proof**:

If there is perfect collinearity, such that $$\exist c \neq0$$ that

$$
c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c=\mathbb{E}\left[c^{\prime} X X^{\prime} c\right]=\mathbb{E}\left[\left(c^{\prime} X\right)^2\right]=0 \text { with } P=1
$$

In order for $$E\left[X X^{\prime}\right]$$ to be positive definite, $$c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c$$ can take value 0, but it cannot have this with P=1. So, $$c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c$$ is not positive definite, therefore it is not invertible. This is a contradiction.

Note that, based on the calculation rule of the matrix, $$(A B)^{\prime}=B^{\prime} A^{\prime}$$, we have $$(X^{\prime} Z)^{\prime}=Z^{\prime} X$$, therefore,&#x20;

$$
\begin{aligned} Z^{\prime} \mathbb{E}\left[X X^{\prime}\right] Z & =\mathbb{E}\left[Z^{\prime} X X^{\prime} Z\right]=\mathbb{E}\left[Z^{\prime} X\left(Z^{\prime} X\right)^{\prime}\right] \\ & =\mathbb{E}\left[\left(Z^{\prime} X\right)^2\right] \geqslant 0 \end{aligned}
$$

So, $$E\left[X X^{\prime}\right]$$ is always semi-positive definite, we need $$E\left[X X^{\prime}\right]>0$$ with $$P>0$$ to be positive definite.

## Solving for Beta

* $$E[U X]=0$$ implies that $$E\left[X\left(Y-X^{\prime} \beta\right)\right]=0$$:&#x20;





## Estimating Beta using OLS







## Matrix Notation

Define

$$
\begin{aligned} \mathbb{Y} & =\left(Y_1, \ldots, Y_n\right)^{\prime} \\ \mathbb{X} & =\left(X_1, \ldots, X_n\right)^{\prime} \\ \hat{\mathbb{Y}} & =\left(\hat{Y}_1, \ldots, \hat{Y}_n\right)^{\prime} \\ & =\mathbb{X} \hat{\beta} \\ \mathbb{U} & =\left(U_1, \ldots, \mathbb{U}_n\right)^{\prime} \\ \hat{\mathbb{U}} & =\left(\hat{U}_1, \ldots, \hat{U}_n\right)^{\prime} \\ & =\mathbb{Y}-\hat{\mathbb{Y}} \\ & =\mathbb{Y}-\mathbb{X} \hat{\beta} . \end{aligned}
$$

In this notation,

$$
\hat{\beta}=\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{Y}
$$

and may be equivalently described as the solution to

$$
\min _{b \in \mathbf{R}^{k+1}}|\mathbb{Y}-\mathbb{X} b|^2 .
$$

Hence, $$\mathbb{X} \hat{\beta}$$ is the vector in the column space of $$\mathbb{X}$$ that is the closest (in terms of Euclidean distance) to $$\mathbb{Y}$$.

$$
\mathbb{X} \hat{\beta}=\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{Y}
$$

is the orthogonal projection of $$Y$$ onto the $$((k+1)$$-dimensional) column space of $$\mathbb{X}$$.

The matrix

$$
\mathbb{P}=\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}
$$

is known as the **Projection Matrix**. It projects a vector in $$\mathbf{R}^n$$ (such as $$\mathbb{Y}$$ ) onto the column space of $$\mathbb{X}$$.

Note that $$\mathbb{P}^2=\mathbb{P}$$, which reflects the fact that projecting something that already lies in the column space of $$\mathbb{X}$$ onto the column space of $$\mathbb{X}$$ does nothing.

The matrix $\mathbb{P}$ is also symmetric. The matrix

$$
\mathbb{M}=\mathbb{I}-\mathbb{P}
$$

is also a projection matrix. It projects a vector onto the $$((n-k-1)$$-dimensional) vector space orthogonal to the column space of $$\mathbb{X}$$. Hence, $$\mathbb{M X}=0$$. Note that $$\mathbb{M Y}=\hat{\mathbb{U}}$$. For this reason, $$\mathbb{M}$$ is sometimes called the **"residual maker" matrix**.

**Proof**:

