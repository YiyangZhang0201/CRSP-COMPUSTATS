# Endogeneity

**In this section , we are going to focus on Linear Regression When** $$E[XU] \neq 0$$**.**&#x20;

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X \in \mathbf{R}^{k+1}$$. Assume further that $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$ and let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

**Not that now, we do not assume** $$E[X U]=0$$**.** Any $$X_j$$ such that $$E\left[X_j U\right]=0$$ is said to be exogenous; Any $$X_j$$ such that $$E\left[X_j U\right] \neq 0$$ is said to be endogenous. Normalizing $$\beta_0$$ if necessary, we view $$X_0$$ as exogenous.

Here is an example:

Recall the Cobb-Douglas production function, a fundamental concept in macroeconomics.

$$
Y=A K^\alpha L^\beta
$$

where we have:

* $$Y$$: Output, or total production of goods and services in an economy.
* $$A$$: Total factor productivity
* $$K$$: Capital input
* $$L$$: Labor input
* $$α$$ and $$β$$: These are the output elasticities of capital and labor, respectively.

We can reform this production function into:

$$
\ln (Y)=\log A+\alpha \log K+\beta \log L .
$$

To do the regression on this function, we can further reform it as

$$
y=\beta_0+\beta_1 K+\beta_2 L+u
$$

Here, we can easily know that this model is endogenous since there are more macro-economy factors that correlated with Capital and Labor but not included in our model, therefore,&#x20;

$$
\mathbb{E}(K u) \neq 0 \quad E(L u) \neq 0 \text {, }
$$

Note that, this is a structure model, which is based on economic theory and are designed to capture the underlying mechanisms and relationships between different variables. It focus on the causal relationship. However, if we treat it as a projection model, the parameters $$\beta$$, $$\beta_1$$, and $$\beta_2$$ are going to be slightly different from this structure model. Since in a projection model, we will assume $$\mathbb{E}(K u) = 0 \quad\& \quad E(L u) = 0$$.

**Now we raise a question, what will happen to the OLS estimator in this setting** $$E[X U]\neq0$$**?**

The Projection Model will have the following inconsistency problem.

$$
\begin{aligned} \hat{\beta} & =\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i Y_i \\ & =\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n} \sum_{i=1}^n X_i Y_i \\ & \stackrel{P}{\longrightarrow}\left(\mathbb{E}\left[X_i X_i^{\prime}\right]\right)^{-1} \mathbb{E}\left[X_i Y_i^{\prime}\right] \\ & =\left(\mathbb{E}\left[X_i X_i^{\prime}\right]\right)^{-1} \mathbb{E}\left[X_i\left(X_i^{\prime} \beta+u_i\right)\right] \\ & =\beta+\left(\mathbb{E}\left[X_i X_i^{\prime}\right]\right)^{-1} \mathbb{E}\left[X_i u_i\right] \\ & \neq \beta \quad \text { if } \mathbb{E}\left[X_i u_i\right] \neq 0 . \end{aligned}
$$

Therefore, $$p \lim _{n \rightarrow \infty} \hat{\beta} \neq \beta$$, the OLS estimator is inconsistent and biased.
