# Properties of LS

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that the first component of $$X$$ is a constant equal to one. Let $$\beta \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

We assume that our model satisfies the following conditions:

1. $$E[X U]=0$$
2. $$E\left[X X^{\prime}\right]<\infty$$
3. There is no perfect collinearity in $$X$$

Denote the marginal distribution of $$(Y,X)$$ by $$P$$. And let $$\left(Y_1, X_1\right), \ldots,\left(Y_n, X_n\right)$$ be an i.i.d. sample of random vectors with distribution $$P$$.

And the properties we will discuss next are:

* Bias
* Gauss-Markov Theorem
* Consistency
* Asymptotic Normality

## Bias

### Unbiasedness

Under the first assumption, $$E[U \mid X]=0$$ (i.e., $$E[Y \mid X]=X^{\prime} \beta$$) it follows that $$E[\hat{\beta}]=\beta$$

**Proof:**

$$E[X U]=E[E[XU \mid X]] = E[XE[U \mid X]] =0 \Rightarrow E[U \mid X] =0$$

Based on the OLS formula, we have that:&#x20;

$$
\hat{\beta}=\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1}\left(\sum_{i=1}^n X_i Y_i\right)
$$

Take $$Y_i = X_i^{\prime}\beta + u_i$$ into our formula, we can have that:

$$
\begin{aligned} \hat{\beta} & =\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i\left(X_i^{\prime} \beta+u_i\right) \\ & =\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i X_i^{\prime} \beta+\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i u_i \\ & =\beta+\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i u_i \end{aligned}
$$

As we can have that $$E[\hat{\beta}]=E[E[\hat{\beta} \mid X]]$$, we can have the following proof:

$$
\mathbb{E}\left[\hat{\beta} \mid X_1, \cdots X_n\right]=\beta+\left(\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \sum_{i=1}^n X_i \mathbb{E}[u_i \mid X_1, \cdots ,X_n]
$$

Note that:&#x20;

* If $$X_i$$s are i.i.d, then $$\mathbb{E}\left[u_i \mid X_1, \cdots, X_n\right] = \mathbb{E}[u_i \mid X_i]$$. Otherwise, this equation may not hold.
* Both our assupmtion $$E[U \mid X]=0$$ and $$\mathbb{E}\left[u_i \mid X_1, \cdots, X_n\right]$$ can be a sufficient condition for us to finish the proof.

As $$\mathbb{E}\left[u_i \mid X_1, \cdots, X_n\right] = \mathbb{E}\left[u_i \mid X_i\right]=0$$, we can have that $$\mathbb{E}\left[\hat{\beta} \mid X_1, \cdots X_n\right]=\beta$$

So we can have that:&#x20;

$$
E[\hat{\beta}]=E[E[\hat{\beta} \mid X]] = E[\beta] = \beta
$$

Now we finished the proof for unbiasedness.

### Biasedness from Omitted Variable

If $$\mathbb{E}[\hat{\beta}] \neq \beta$$, then $$\hat{\beta}$$ is biased, $$\text{bias}(\hat{\beta}) = \mathbb{E}[\hat{\beta}] - \beta$$, this may because of the omitted variable (some related variable).

* If $$\operatorname{bias}(\hat{\beta}) > 0$$: $$\hat{\beta}$$ is overestimated.
* If $$\operatorname{bias}(\hat{\beta}) < 0$$: $$\hat{\beta}$$ is underestimated.

For example, in a regression about factors that affects wage:&#x20;

$$
\text { wage }=\beta_0+\beta_1 \text { edu}+u
$$

We regressed wage on the education level (edu). However, there are other factors that may not be independent of the education level that also affects wage, like ability, motivation, .etc. So in this example, we have $$\operatorname{Cov}(e d u, u) \neq 0$$, therefore, this will lead to the biased estimation of $$\beta_1$$.

To calculate the omitted variable bias, we can use the following steps:

1. Build a long regression: $$Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+e$$, where $$\mathbb{E}\left[X_1 e\right]=0, \mathbb{E}\left[X_2 e\right]=0$$
2. Build a short regression: $$Y=X_1^{\prime} \gamma_1+u$$, where $$\mathbb{E}\left[X_1 u\right]=0$$
3. By the formula of OLS, we have that:

$$
\begin{aligned} \gamma_1& =\mathbb{E}\left[X_1X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1Y\right] \\ & =\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1\left(X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+e\right)\right] \\ & =\beta_1+\left[\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 X_2^{\prime}\right] \beta_2\right]+\left[\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 e\right]\right] \end{aligned}
$$

As $$\mathbb{E}\left[X_1 e\right]=0$$, and denote $$\Gamma_{12}$$ as $$\mathbb{E}\left[X_1 X_1^{\prime}\right]^{-1} \mathbb{E}\left[X_1 X_2^{\prime}\right]$$, we can have that:

$$
\gamma_1 =\beta_1+\Gamma_{12} \beta_2
$$

Note that:

* $$\Gamma_{12}$$ can be defined as $$X_2 = X_1^{\prime} \Gamma_{12}+e$$, which is the projection of $$X_2$$ on $$X_1$$. However,  in the real world, it is very hard to estimate because we usually cannot observe omitted variables.
* As $$X_1$$ stands for education, and $$X_2$$ stands for ability or motivation, based on the real world experience, we can easily conclude that:
  * Better ability/motivation are more likely leads to higher wage: $$\beta_2 > 0$$ is highly likely.
  * Better ability/motivation are more likely leads to higher education: $$\Gamma_{12} > 0$$ is highly likely.
* Therefore, we have that the bias we got from the omitted variable: $$\Gamma_{12} \beta_2$$ is highly likely to be greater than 0. Therefore, in our short regression, we are very likely overestimated the effect of education on wage.

## Gauss-Markov Theorem

### Homoskedastic and Heteroskedastic

Suppose $$E[U \mid X]=0$$ and that $$\operatorname{Var}[U \mid X]=\sigma^2$$.

* When $$\operatorname{Var}[U \mid X]$$ is constant (and therefore does not depend on $$X$$ ) we say that $$U$$ is homoskedastic.&#x20;
* Otherwise, we say that $$U$$ is heteroskedastic.

And there are two ways to check the homoskedastic and heteroskedastic:

1. We can do regression for $$\operatorname{Var}[U \mid X]$$ on $$X$$, if covariance for $$X$$ is significantly different with 0.
2. We can also plot the value of $$\operatorname{Var}[U \mid X]$$, and check the plot to see if there is any trend in the plot.

### Gauss-Markov Theorem

**Gauss-Markov Theorem**: under these assumptions **the OLS estimator is "best" in the sense that it has the "smallest" value of** $$\operatorname{Var}\left[\mathbb{A}^{\prime} \mathbb{Y} \mid X_1, \ldots, X_n\right]$$ among all estimators of the form

$$
\mathbb{A}^{\prime} \mathbb{Y}
$$

for some matrix $$\mathbb{A}=\mathbb{A}\left(X_1, \ldots, X_n\right)$$ satisfying

$$
E\left[\mathbb{A}^{\prime} \mathbb{Y}\mid X_1, \ldots, X_n\right]=\beta
$$

Note that $$\mathbb{A}^{\prime} \mathbb{Y}$$ is linear in $$\mathbb{Y}$$, so we might be able to get better in variance using the WLS. Gauss-Markove Theorem is just for OLS case.

Denote the variance matrix as $$B$$, we can have that the "smallest" is understood as the partial order obtained by $$B \geq \tilde{B}$$ if $$B-\tilde{B}$$ is positive semi-definite.

Taking above matrix comparison skill in to our theorem, the "best" unbiased linear estimator is obtained by finding the matrix $$\mathbb{A}_0$$ satisfying $$\mathbb{A}_0^{\prime} \mathbb{X}=\mathbb{I}_{k}$$ such that $$\mathbb{A}_0^{\prime} \mathbb{A}_0$$ is minimized in the positive definite sense, which means that for any other matrix $$\mathbb{A}$$ satisfying $$\mathbb{A}^{\prime} \mathbb{X}=\mathbb{I}_k$$ then $$\mathbb{A}^{\prime} \mathbb{A}-\mathbb{A}_0^{\prime} \mathbb{A}_0$$ is positive semi-definite.

This class of estimators includes the OLS estimator as a special case (by setting $$\mathbb{A}^{\prime}=\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}$$. The property is sometimes expressed as saying that **OLS estimator is the "best linear unbiased estimator (BLUE)"** **of** $$\beta$$ **under these assumptions.**

The Gauss-Markov theorem provides a lower bound on the variance matrix of unbiased linear estimators under the assumption of homoskedasticity. It says that no unbiased linear estimator can have a variance matrix smaller (in the positive definite sense) than $$\sigma^2\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}$$.

Now we do the following proofs:

* **The estimator is** $$\mathbb{A}^{\prime} Y$$ **for** $$\mathbb{A}=\mathbb{A}\left(X_1, \ldots, X_n\right)$$ **and satisfies** $$E\left[\mathbb{A}^{\prime} \mathbf{Y} \mid X_1, \ldots, X_n\right]=\beta$$**.**

**Proof:**

As we have $$Y=X \beta+U$$ $$\Rightarrow$$ $$\mathbb{A}^{\prime} Y=\mathbb{A}^{\prime}(X \beta+U)$$ $$\Rightarrow$$ $$\mathbb{A}^{\prime} Y=\mathbb{A}^{\prime} X \beta+\mathbb{A}^{\prime} U$$

Now we can have that, $$E\left[\mathbb{A}^{\prime} Y \mid X_1, \ldots, X_n\right]=E\left[\mathbb{A}^{\prime} X \beta+\mathbb{A}^{\prime} U \mid X_1, \ldots, X_n\right]$$

As $$\mathbb{A}=\mathbb{A}\left(X_1, \ldots, X_n\right)$$ depend on $$X_1, \ldots, X_n$$, and $$X \perp U$$, we can have that:

$$E\left[\mathbb{A}^{\prime} X \beta\mid X_1, \ldots, X_n\right]=\mathbb{A}^{\prime} X \beta$$ & $$E\left[\mathbb{A}^{\prime} U \mid X_1, \ldots, X_n\right]=0$$

So we got that $$E\left[\mathbb{A}^{\prime} Y \mid X_1, \ldots, X_n\right]=\mathbb{A}^{\prime} X \beta$$, combine this with $$\mathbb{A}^{\prime} \mathbb{X}=\mathbb{I}$$, we finished the proof that

$$
E\left[\mathbb{A}^{\prime} \mathbf{Y} \mid \boldsymbol{X}_1, \ldots, \boldsymbol{X}_n\right]=\beta
$$

* **Show** $$\mathbb{A}^{\prime} \mathbb{A}-\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}$$ **is positive semi-definite for any** $$\mathbb{A}$$ **satisfying** $$\mathbb{A}^{\prime} \mathbb{X}=\mathbb{I}$$

**Proof:**

We need to show $$\mathbb{A}^{\prime} \mathbb{A}-\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} > 0$$.

Set . Note that $$\boldsymbol{X}^{\prime} \boldsymbol{C}=\mathbf{0}$$. We calculate that

$$
\begin{aligned} \mathbb{A}^{\prime} \mathbb{A}-\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} & =\left(\mathbb{C}+\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}\right)^{\prime}\left(\mathbb{C}+\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}\right)-\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \\ & =\mathbb{C}^{\prime} \mathbb{C}+\mathbb{C}^{\prime} \mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}+\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{C} \\ & +\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}-\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \\ & =\mathbb{C}^{\prime} \mathbb{C} \\ & >0 \end{aligned}
$$

The final inequality states that the matrix $$\mathbb{C}^{\prime} \mathbb{C}$$ is positive semi-definite which is a property of quadratic form.

## Consistency

$$
\text { Under our three main assumptions, } \hat{\beta} \stackrel{P}{\rightarrow} \beta \text { as } n \rightarrow \infty \text {. }
$$

**Proof:**

Based on the OLS formula, we can have that:

$$
\hat{\beta}=\left(\frac{1}{n} \sum_{1 \leq i \leq n} X_i X_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_{1 \leq i \leq n} X_i Y_i\right)
$$

Take $$Y_i = X_i^{\prime}\beta + u_i$$ into our formula, we can have that:

$$
\begin{aligned} \hat{\beta} & =\left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n}\sum_{i=1}^n X_i\left(X_i^{\prime} \beta+u_i\right) \\ & =\left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime} \beta+\left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n}\sum_{i=1}^n X_i u_i \\ & =\beta+\left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \left(\frac{1}{n}\sum_{i=1}^n X_i u_i\right) \end{aligned}
$$

Now, we denote $$B_n = \left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \left(\frac{1}{n}\sum_{i=1}^n X_i u_i\right)$$, then we can have that, as $$X_i$$s are i.i.d. and based on the LLN:

* $$\left(\frac{1}{n}\sum_{i=1}^n X_i X_i^{\prime}\right)^{-1}$$ $$\stackrel{P}{\rightarrow}$$ $$\mathbb{E}\left[X_i X_i^{\prime}\right]$$, which is less than $$\infin$$
* $$\frac{1}{n} \sum_{i=1}^n X_i u_i$$ $$\stackrel{P}{\rightarrow}$$ $$\mathbb{E}\left[\begin{array}{lll}X_iu_i\end{array}\right]=0$$

Therefore, we can have that :

$$
\begin{aligned} p \lim _{n \rightarrow \infty} \hat{\beta} & =\beta+p\lim _{n \rightarrow \infty} B_n \\ & =\beta+\mathbb{E}\left[X_i X_i^{\prime}\right] \mathbb{E}\left[X_i u_i\right] \\ & =\beta+0=\beta \end{aligned}
$$

Now we finished our proof for consistency.

## Asymptotic Normality

We already assume that our model satisfies the three assumptions in the previous analysis:

1. $$E[X U]=0$$
2. $$E\left[X X^{\prime}\right]<\infty$$
3. There is no perfect collinearity in $$X$$

Now, we add a forth assumption, which is:

4. $$\operatorname{Var}[X U]=E\left[X X^{\prime} U^2\right]<\infty$$

Then, as $$n \rightarrow \infty$$, we have

$$
\sqrt{n}(\hat{\beta}-\beta) \stackrel{d}{\rightarrow} N(0, \mathbb{V}) \text { where } \mathbb{V}=\left(E\left[X X^{\prime}\right]\right)^{-1} E\left[X X^{\prime} U^2\right]\left(E\left[X X^{\prime}\right]\right)^{-1}
$$

As we have calculated before,&#x20;

$$
\begin{aligned} \hat{\beta} & =\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n} \sum_{i=1}^n X_i Y_i \\ & =\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n} \sum_{i=1}^n X_i\left(X_i \beta+U_i\right) \\ & =\beta+\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n} \sum_{i=1}^n X_i U_i \end{aligned}
$$

Therefore, we have

$$
\hat{\beta}-\beta=\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1} \frac{1}{n} \sum_{i=1}^n X_i U_i
$$

We have shown that:



