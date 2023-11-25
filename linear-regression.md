# Linear Regression

## Introduction to Linear Regression

Let $$(Y, X, U)$$be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $X$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that the first component of $$X$$ is a constant equal to one, i.e.,$$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$.  Let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that:&#x20;

$$
Y=X^{\prime} \beta+U
$$

We can have that:

* $$X_1, \ldots, X_k$$ are column vectors, store data for specific variable $$k$$
* Shape of $$Y$$, $$X^{\prime}$$, $$\beta$$ and $$U$$:&#x20;
  * $$Y$$: $$n \times 1$$
  * $$X^{\prime}$$: $$n \times (k+1)$$
  * $$\beta$$: $$(k+1) \times 1$$
  * $$U$$: $$n \times 1$$
* &#x20;$$\beta_0$$ is an intercept parameter and the remaining $$\beta_j$$ are slope parameters.

Here, we got the basic structure of the Linear Regression.

## Interpretations of Linear Regression

There are three ways to interpret Linear Regression:

1. Linear Conditional Expectation
2. Best Linear Approximation
3. Causal Model

Now, we talk about each way in detail.

### Linear Conditional Expectation

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



### "Best" Linear Approximation

In general, the conditional expectation is probably NOT linear. We are just using a linear function to approximate this.

