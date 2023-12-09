# TSLS Estimator

## Two-Stage Least Squares

The Two-Stage Least Squares (TSLS) is used when the number of instrument variables is greater than the number of explanatory variables. Means to use it in the following condition:

$$
\text { Over-identified case: } l>k
$$

The expressions we derived for $$\beta$$ in this case, like

$$
\beta=E\left[\Pi^{\prime} E\left[Z X^{\prime}\right]\right]^{-1} \Pi^{\prime} E[Z Y]
$$

all involved the matrix $$\Pi$$, where

$$
B L P(X \mid Z)=\Pi^{\prime} Z
$$

An estimate of $$\Pi$$ can be obtained by OLS. Since $$\Pi=E\left[Z Z^{\prime}\right]^{-1} E\left[Z X^{\prime}\right]$$, a natural estimator of $$\Pi$$ is

$$
\hat{\Pi}=\left(\frac{1}{n} \sum_i Z_i Z_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_i Z_i X_i^{\prime}\right) .
$$

Let $$X_i=\hat{\Pi}^{\prime} Z_i+\hat{V}_i$$, with above estimator of $$\Pi$$, a natural estimator of $$\beta$$ is simply:&#x20;

$$
\hat{\beta}=\left[\hat{\Pi} \frac{1}{n} \sum_{i=1}^n Z_i X_i^{\prime}\right]^{-1}\left[\hat{\Pi} \frac{1}{n} \sum_{i=1}^n Z_i Y_i\right]
$$

Proof:

$$
\begin{aligned} \hat{\beta}&=\left[\hat{\Pi} \frac{1}{n} \sum_{i=1}^n Z_i X_i^{\prime}\right]^{-1}\left[\hat{\Pi}\frac{1}{n} \sum_{i=1}^n Z_i Y_i\right] \\ & =\left[\hat{\Pi} \frac{1}{n} \sum_{i=1}^n Z_i X_i^{\prime}\right]^{-1}\left[\hat{\Pi} \frac{1}{n} \sum_{i=1}^n Z_i\left(X_i^{\prime} \beta+U\right)\right] \\ & \stackrel{p}{\rightarrow} \mathbb{E}\left[Z X^{\prime}\right]^{-1}\left(\mathbb{E}\left[Z X^{\prime} \beta\right]+\mathbb{E}[Z U]\right) \\ & =\beta+\mathbb{E}\left[Z X^{\prime}\right]^{-1} \mathbb{E}[Z U] \quad\text{ by Instrument Exogeneity: } \mathbb{E}[Z U]=0\\ & =\beta \\\end{aligned}
$$

Note that $$\hat{\beta}_n$$ satisfies

$$
\frac{1}{n} \sum_i \hat{\Pi}^{\prime} Z_i\left(Y_i-X_i^{\prime} \hat{\beta}\right)=0 .
$$

In particular, $$\hat{U}_i=Y_i-X_i^{\prime} \hat{\beta}$$ satisfies

$$
\frac{1}{n} \sum_i \hat{\Pi}^{\prime} Z_i \hat{U}_i=0
$$

**This implies that** $$\hat{U}_i$$ **is orthogonal to all of the instruments equal to an exogenous regressors, but may not be orthogonal to the other regressors.**

It is termed the TSLS estimator because it may be obtained in the following way:&#x20;

1. Regress (each component of) $$X_i$$ on $$Z_i$$ to obtain $$\hat{X}_i=\hat{\Pi}^{\prime} Z_i$$&#x20;
2. Regress $$Y_i$$ on $$\hat{X}_i$$ to obtain $$\hat{\beta}$$. However, in order to obtain proper standard errors, it is recommended to compute the estimator in one step

### Matrix Notation

This estimator may be expressed more compactly using matrix notation. Define

$$
\begin{aligned} \mathbb{Z} & =\left(Z_1, \ldots, Z_n\right)^{\prime} \\ \mathbb{X} & =\left(X_1, \ldots, X_n\right)^{\prime} \\ \mathbb{Y} & =\left(Y_1, \ldots, Y_n\right)^{\prime} \\ \hat{\mathbb{X}} & =\left(\hat{X}_1, \ldots, \hat{X}_n\right)^{\prime} \\ & =\mathbb{P}_Z \mathbb{X}, \end{aligned}
$$

where

$$
\mathbb{P}_Z=\mathbb{Z}\left(\mathbb{Z}^{\prime} \mathbb{Z}\right)^{-1} \mathbb{Z}^{\prime}
$$

is the projection matrix onto the column space of $$\mathbb{Z}$$. In this notation, we have

$$
\begin{aligned} \hat{\beta} & =\left(\hat{\mathbb{X}}^{\prime} \mathbb{X}\right)^{-1}\left(\hat{\mathbb{X}}^{\prime} \mathbb{Y}\right) \\ & =\left(\hat{\mathbb{X}}^{\prime} \hat{\mathbb{X}}\right)^{-1}\left(\hat{\mathbb{X}}^{\prime} \mathbb{Y}\right) \\ & =\left(\mathbb{X}^{\prime} \mathbb{P}_Z \mathbb{X}\right)^{-1}\left(\mathbb{X}^{\prime} \mathbb{P}_Z \mathbb{Y}\right) \end{aligned}
$$

## Properties of Two-Stage Least Squares

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that the first component of $$X$$ is constant and equal to one, i.e., $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$. Let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

Estimation in OLS is inconsistent and biased if $$E[XU]\neq0$$

We assume:

1. &#x20;$$E[Z U]=0$$: Exclusion Condition: variable need to be valid IV
2. $$E\left[Z X^{\prime}\right]<\infty$$: Regularity condition
3. $$E\left[Z Z^{\prime}\right]<\infty$$: Regularity condition
4. There is no perfect collinearity in $$Z$$
5. The rank of $$E\left[Z X^{\prime}\right]$$ is $$k+1$$: Relevance Condition

Let $$\left(Y_1, X_1, Z_1\right), \ldots,\left(Y_n, X_n, Z_n\right)$$ be an i.i.d. sequence of random variables with distribution $$P$$.

Under these assumptions the TSLS estimator is consistent for $$\beta$$, and under the additional requirement that $$\operatorname{Var}[Z U]<\infty$$, it is asymptotically normal with limiting variance

$$
\mathbb{V}=\left[E\left(\Pi^{\prime} Z Z^{\prime} \Pi\right)\right]^{-1} \Pi^{\prime} \operatorname{Var}[Z U] \Pi\left[E\left(\Pi^{\prime} Z Z^{\prime} \Pi\right)\right]^{-1}
$$

### Consistency of TSLS

The nature estimator of $$\beta$$ under TSLS $$\hat{\beta}$$ satisfies&#x20;

$$
\hat{\beta}=\left[\hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i X_i^{\prime}\right)\right]^{-1} \hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Y_i\right) \stackrel{P}{\rightarrow} \beta \text { as } n \rightarrow \infty .
$$

**Proof:**

As $$\hat{\Pi}=\left(\frac{1}{n} \sum_i Z_i Z_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_i Z_i X_i^{\prime}\right)$$ $$\stackrel{P}{\longrightarrow}$$ $$\Pi=E\left[Z Z^{\prime}\right]^{-1} E\left[Z X^{\prime}\right]$$, and $$\frac{1}{n} \sum_{1 \leqslant i \leqslant n} Z_i X_i^{\prime} \stackrel{P}{\longrightarrow} \mathbb{E}\left[Z_i X_i^{\prime}\right]$$, then by Slutsky Theorem and Continuous Mapping Theorem (CMP) (for function $$f(X)=X^{-1}$$), we can have that, for the left part:

$$
\left(\hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum Z_i X_i^{\prime}\right)\right)^{-1} \stackrel{P}{\longrightarrow}\left(\Pi^{\prime} \mathbb{E}\left[Z_i X_i^{\prime}\right]\right)^{-1}
$$

For the right part, similarly, we can get that:

$$
\begin{aligned} & \frac{1}{n} \sum_{1 \leqslant i \leqslant n} Z_i Y_i=\frac{1}{n} \sum_{1 \leqslant i \leqslant n} Z_i\left(X_i^{\prime} \beta+U\right) \\ & =\frac{1}{n} \sum_{1 \leqslant i \leqslant n} Z_i X_{i}^{\prime} \beta+\frac{1}{n} \sum_{1 \leqslant i \leqslant n} Z_i U_i \\ & \stackrel{P}{\longrightarrow}\mathbb{E}\left[Z_i X_{i}^{\prime}\right] \beta+\mathbb{E}[Z_i U_i] \\ & =\mathbb{E}\left[Z_i X_{i}^{\prime}\right] \beta+0=\mathbb{E}\left[Z_i X_{i}^{\prime}\right] \beta \\ \end{aligned}
$$

Therefore,&#x20;

$$
\hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Y_i\right) \stackrel{P}{\rightarrow}\Pi^{\prime} \mathbb{E}\left[Z_i X_i^{\prime}\right]\beta
$$

Therefore, we can have finished the proof that&#x20;

$$
\hat{\beta}=\left[\hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i X_i^{\prime}\right)\right]^{-1} \hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Y_i\right) \stackrel{P}{\rightarrow} \beta \text { as } n \rightarrow \infty .
$$

### Asymptotic Normality of TSLS

Assume that $$\operatorname{Var}[Z U]=E\left[Z Z^{\prime} U^2\right]<\infty$$. Then, as $$n \rightarrow \infty$$,

$$
\sqrt{n}(\hat{\beta}-\beta) \stackrel{d}{\rightarrow} N(0, \mathbb{V})
$$

Based on the estimator of $$\hat{\beta}$$, we can have that:

$$
\hat{\beta}-\beta=\left[\hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i X_i^{\prime}\right)\right]^{-1} \hat{\Pi}_n^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i U_i\right)
$$

By CLT:&#x20;

$$
\sqrt{n} \frac{1}{n} \sum_{i=1}^n Z_i U_i \stackrel{d}{\longrightarrow} N\left(0, \operatorname{Var}\left(Z_i U_i\right)\right) .
$$

Then, take this inside, we can have that, based on the Slustky Theorem:

$$
\begin{aligned} \sqrt{n}\left(\hat{\beta}-\beta\right)&=\left[\hat{\Pi}^{\prime} \frac{1}{n} \sum_{i=1}^n Z_i X_i^{\prime}\right]^{-1} \hat{\Pi}^{\prime}\left(\sqrt{n} \frac{1}{n} \sum_{i=1}^n Z_i U_i\right)\\ &\stackrel{d}{\rightarrow}\underbrace{\left(\left[\hat{\Pi}^{\prime} \frac{1}{n} \sum_{i=1}^n Z_i X_i^{\prime}\right]^{-1} \hat{\Pi}^{\prime}\right)}_A \underbrace{N\left(0, \operatorname{Var}\left(Z_i U_i\right)\right)}_W \end{aligned}
$$

Since $$A$$ is scaler, we can have that:

$$
\begin{aligned} \operatorname{Var}(A \cdot W) & =\mathbb{E}\left[(A W-\mathbb{E}[A W])(A W-\mathbb{E}[A W])^{\prime}\right] \\ & =\mathbb{E}[A(W-\mathbb{E}[W])(W-\mathbb{E}[W])^{\prime} A^{\prime}] \\ & =A \mathbb{E}[(W-\mathbb{E}[W])(W-\mathbb{E}[W])^{\prime}] A^{\prime} \\ & =A \operatorname{Var}(W) A^{\prime} \end{aligned}
$$

Now we can have that $$\mathbb{V}$$ is

$$
\mathbb{V}= {\left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i X_i^{\prime}\right) \right]^{-1} \hat{\Pi}^{\prime}Var\left(W\right)\hat{\Pi} \left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i X_i^{\prime}\right) \right]^{-1} }
$$

As we have $$X=\Pi^{\prime} Z+e$$ $$\Rightarrow$$ $$X^{\prime}=Z^{\prime} \Pi+e$$

Therefore, we can have that,&#x20;

$$
E\left[Z_i X_i\right] =E\left[Z_i Z_i^{\prime}\right] \Pi +\mathbb{E}\left[Z_i E_i\right] =E\left[Z_i Z_i^{\prime}\right] \Pi
$$

Now, we can get that:

$$
\mathbb{V}= {\left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime}\right) \hat{\Pi}\right]^{-1} \hat{\Pi}^{\prime}Var\left(W\right)\hat{\Pi} \left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime}\right) \hat{\Pi}\right]^{-1} }
$$

#### Estimation of V:

A natural estimator of $$\mathbb{V}$$ is given by

$$
\hat{\mathbb{V}}_n= {\left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime}\right) \hat{\Pi}\right]^{-1} \hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime} \hat{U}_i^2\right) \hat{\Pi} } {\left[\hat{\Pi}^{\prime}\left(\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime}\right) \hat{\Pi}\right]^{-1} }
$$

where $$\hat{U}_i=Y_i-X_i^{\prime} \hat{\beta}$$.

The primary difficulty in establishing the consistency of this estimator lies in showing that

$$
\frac{1}{n} \sum_{1 \leq i \leq n} Z_i Z_i^{\prime} \hat{U}_i^2 \stackrel{P}{\rightarrow} \operatorname{Var}[Z U]
$$

as $$n \rightarrow \infty$$. The complication lies in the fact that we do not observe $$U_i$$ and therefore have to use $$\hat{U}_i$$.

$$
\operatorname{Var}(Z U)=E\left[Z U \cdot U Z^{\prime}\right] \text { since } E[Z U]=0
$$



However, please note that $$\hat{U}_i=Y_i-X_i^{\prime} \hat{\beta} \neq Y_i-\hat{X}_i^{\prime} \hat{\beta}$$, where $$\hat{X_i}$$  **is the regressor in the second stage of regression.** So the standard errors from two repeated applications of OLS will be incorrect. **And Stata is using** $$\hat{X_i}^{\prime}$$ **as default. So, to do the Two-Step Regression correctly, you need to use command `ivregress`.**

