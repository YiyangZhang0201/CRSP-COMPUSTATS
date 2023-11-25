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

Recall the Conditional Expectation Function (CEF): $$\mathbb{E}[Y \mid X=x]=m(x)$$, which is the best estimator of $$Y$$.
