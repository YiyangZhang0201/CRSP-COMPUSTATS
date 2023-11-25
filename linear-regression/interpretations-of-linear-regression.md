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

* We are only holding $$X_j, j \neq i$$ constant, but we didn't hold $$U$$ constant in this structure.
* As $$U=Y-\mathbb{E}[Y \mid X]$$, we have $$Y=\mathbb{E}[Y \mid X]+U = m(X) + U$$
* So, $$\frac{\partial Y}{\partial X_i}=\frac{\partial m(X)}{\partial X_i}+\frac{\partial U}{\partial X_i}$$
* $$\frac{\partial m(X)}{\partial X_i} = \beta_i$$ only if $$m(X)$$ is a linear function, e.g. $$m(X)=\beta_0+\beta_1 X_1+\cdots+\beta_k X_k$$

## "Best" Linear Approximation

In general, the conditional expectation is probably NOT linear. We are just using a linear function to approximate this.

Suppose that: $$E\left[Y^2\right]<\infty$$ and $$E\left[X X^{\prime}\right]<\infty$$ (or, $$E\left[X_j^2\right]<\infty$$ for $$\left.1 \leq j \leq k\right)$$

Under these assumptions, one may consider what is the **"best" linear approximation** (i.e., function of the form $$X^{\prime} b$$ for some choice of $$b \in \mathbf{R}^{k+1}$$, $$b$$ as the best linear predictor for $$\beta$$) to the conditional expectation.&#x20;

To this end, consider the minimization problem for approximation/prediction error:

$$
\min _{b \in \mathbf{R}^{k+1}} E\left[\left(E[Y \mid X]-X^{\prime} b\right)^2\right]
$$

Minimize over $$b$$ and denote $$\beta$$ as the solution to this minimization problem. Then,

* $$\beta$$ is called the best linear predictor, and it is the linear projection coefficient.
* $$b$$ is the generic coefficient vector.

But we still **cannot** interpret $$\beta_j$$ as the ceteris paribus (i.e., holding $$X_{-j}$$ and $$U$$ constant) effect of a one unit change in $$X_j$$ on $$Y$$. Because we still do not know the information about the error term. Partial derivative only hold for other $$X_i$$s.

### Best Linear Predictor (BLP)

Best linear predictor (BLP) can also be defined as:

$$
\beta \in \underset{b \in \mathbf{R}^{k+1}}{\operatorname{argmin}} E\left[\left(Y-X^{\prime} b\right)^2\right]
$$

This $$\beta$$ is also a convenient way of summarizing the “best” linear predictor of $$Y$$ given $$X$$.

**Proof:**

$$\mathbb{E}\left[\left(Y-X^{\prime} b\right)^2\right] =\mathbb{E}\left[\left(Y-\mathbb{E}[Y \mid X]+\mathbb{E}[Y \mid X]-X^{\prime} b\right)^2\right]$$

$$= \mathbb{E}\left[ (Y - \mathbb{E}[Y|X])^2 \right] + \mathbb{E}\left[ (\mathbb{E}[Y \mid X] - X^{\prime} b)^2 \right]+2 \mathbb{E}\left[(Y-\mathbb{E}[Y \mid X])\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)\right]$$

As for $$\mathbb{E}\left[(Y-\mathbb{E}[Y \mid X])\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)\right]$$, we have that it is equal to,

$$\mathbb{E}\left[\mathbb{E}\left[(Y-\mathbb{E}[Y \mid X])\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right) \mid X\right]\right)$$, and $$\mathbb{E}[Y \mid X]-X^{\prime} b$$ only depend on $$X$$, we have:

$$\mathbb{E}\left[(Y-\mathbb{E}[Y \mid X])\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)\right] = \mathbb{E}[(\mathbb{E}[Y \mid X]-X^{\prime} b)(\mathbb{E}[Y-\mathbb{E}[Y \mid X]\mid X])]$$

$$=\mathbb{E}\left[\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)(\mathbb{E}[\mathbb{E}[Y \mid X] -\mathbb{E}[Y \mid X]])\right] = 0$$

So, we got:

$$\mathbb{E}\left[\left(Y-X^{\prime} b\right)^2\right]=\mathbb{E}\left[(Y-\mathbb{E}[Y \mid X])^2\right]+\mathbb{E}\left[\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)^2\right]$$

However, only the part $$\mathbb{E}\left[\left(\mathbb{E}[Y \mid X]-X^{\prime} b\right)^2\right]$$ is depended on $$b$$, so optimize the whole function over $$b$$ is same to optimize over this part. Therefore, this BLP definition is same with the previous one.

### Summary: Two in One

Two interpretations from equivalent optimization problems:

$$
\beta \in \underset{b \in \mathbf{R}^{k+1}}{\operatorname{argmin}} E\left[\left(E[Y \mid X]-X^{\prime} b\right)^2\right] \text { and } \beta \in \underset{b \in \mathbb{R}^{k+1}}{\operatorname{argmin}} E\left[\left(Y-X^{\prime} b\right)^2\right]
$$

Note $$E\left[\left(Y-X^{\prime} b\right)^2\right]$$ is a convex (as a function of $$b$$ ) and this has the following implications.

* We can take the derivative on it and use FOC to solve $$b$$ and get $$\beta$$
* However, in order to do this, we need to make more assumptions. And I will introduce them in detail later in the estimation of $$\beta$$

## Casual Model

In order to analysis the Casual Effect using the model, suppose that: $$Y=g(X, U)$$, where $$X$$ are the observed determinants of $$Y$$ and $$U$$ are the unobserved determinants of $$Y$$.

Such a relationship is a model of how $$Y$$ is determined and may come from physics, economics, etc. The effect of $$X_j$$ on $$Y$$ holding $$X_{-j}$$ and $$U$$ constant (i.e., ceteris paribus) is determined by this function $$g$$.

If $$g$$ is differentiable. then it is given by

$$
D_{x_j} g(X, U) \text {. }
$$

If we assume further that $$g$$ is linear, such that,

$$
g(X, U)=X^{\prime} \beta+U,
$$

then the ceteris paribus effect of $$X_j$$ on $$Y$$ is simply $$\beta_j$$. We may normalize $$U$$ so that $$E[U]=0$$, we can achieve this by replacing $$U$$ with $$U-E[U]$$ and $$\beta_0$$ with $$\beta_0+E[U]$$ if $$E[U]=0$$ is not the original case.

On the other hand, $$E[U \mid X], E\left[U \mid X_j\right]$$ and $$E\left[U X_j\right]$$ for $$1 \leq j \leq k$$ may or may not equal zero. This aspect is crucial in causal inference as it relates to the independence or correlation of the unobserved determinants with the observed variables. So, $$\beta_j$$ might be biased for the ceteris paribus effect. To get the ceteris paribus effect, we need more assumptions.

### Potential Outcomes

Potential outcomes are an easy way to think about causal relationships.

Illustration: randomized controlled experiment where individuals are randomly assigned to a treatment (a drug) that is intended to improve their health status.

Notation: Let $$Y$$ denote the observed health status and $$X \in \{0,1\}$$ denote whether the individual takes the drug or not.

The **causal relationship** between $$X$$ and $$Y$$ can be described using the so-called **potential outcomes**:

* $$Y(0)$$ potential outcome in the absence of treatment
* $$Y(1)$$ potential outcome in the presence of treatment

Under health status, we have two health status variables: $$(Y(0), Y(1))$$, where

* $$Y(0)$$ is the value of the outcome that would have been observed if (possibly counter-to-fact) $$X$$ were 0.
* $$Y(1)$$ is the value of the outcome that would have been observed if (possibly counter-to-fact) $$X$$ were 1.

### Treatment Effects

* The difference $$Y(1)-Y(0)$$ is called the **treatment effect (TE)**.
* The quantity $$E[Y(1)-Y(0)]$$ is usually referred to as the **average treatment effect (ATE)**.

Using this notation, we may rewrite the observed outcome as:





