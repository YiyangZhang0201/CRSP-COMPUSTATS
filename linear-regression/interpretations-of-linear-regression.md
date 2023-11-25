# Interpretations of Linear Regression

There are three ways to interpret Linear Regression:

1. Linear Conditional Expectation
2. Best Linear Approximation
3. Causal Model

Now, we talk about each way in detail.

## Linear Conditional Expectation

Suppose that:

$$
E[Y \mid X]=X^{\prime} \beta
$$

and define: $$U=Y-E[Y \mid X]$$

Recall the Conditional Expectation Function (CEF): $$\mathbb{E}[Y \mid X=x]=m(x)$$, which is the best estimator of $$Y$$.

For $$\mathbb{E}[Y \mid X]$$, we have $$\mathbb{E}[Y \mid X] = \mathbb{E}\left[Y \mid X_1, X_2, \ldots, X_k\right] = m(X_1, X_2, \ldots, X_k)$$.But in practice, the form of this function $$m(\cdot)$$ is unknown to us.

This Linear Conditional Expectation has several implications:

1.  $$\mathbb{E}(U)=0$$. &#x20;

    $$\mathbb{E}[U]=\mathbb{E}_{X}[\mathbb{E}[U \mid X]]$$

    &#x20;         $$=\mathbb{E}_{X}[\mathbb{E}[Y - X^{\prime}\beta \mid X]] =\mathbb{E}_X[\mathbb{E}[Y| X]-X^{\prime} \beta]=\mathbb{E}_X[X^{\prime} \beta - X^{\prime} \beta] = 0$$
2.  $$\mathbb{E}[X U]=0$$

    $$\mathbb{E}[X U]=\mathbb{E}\left[X \cdot\left(Y-X^{\prime} \beta\right)\right]=\mathbb{E}[X Y]-\mathbb{E}\left[X X^{\prime} \beta\right]$$

    &#x20;             $$=\mathbb{E}[\mathbb{E}[X Y \mid X]]-\mathbb{E}\left[XX^{\prime} \beta\right]$$

    take $$E[Y \mid X]=X^{\prime} \beta$$ into it we have:

    &#x20;             $$= \mathbb{E}[X \mathbb{E}[Y \mid X]]-\mathbb{E}\left[XX^{\prime} \beta\right]=0$$
3. $$\operatorname{Cov}(X, U)=0$$

For $$\beta$$ we got by this define method, it does not necessarily have a Causal Effect. Since one $$X_i$$ change, others might also change.

Therefore, we also **cannot** interpret $$\beta_j$$ as the **ceteris paribus** (i.e., holding $$X_{-j}$$ and $$U$$ constant) effect of a one unit change in $$X_i$$ on $$Y$$. We need more information to check if we can do that.



## "Best" Linear Approximation

In general, the conditional expectation is probably NOT linear. We are just using a linear function to approximate this.
