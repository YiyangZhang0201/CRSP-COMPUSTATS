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

### Consistency of TSLS



### Asymptotic Normality of TSLS



