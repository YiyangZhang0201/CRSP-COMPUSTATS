# Endogeneity

**The endogeneity means that there is correlation between regressor** $$X$$ **and error term** $$U$$**. Means** $$Corr(X,U) \neq 0$$**, this leads to the assumption** $$E[X U]=0$$**.**



There are three scenarios that can leads to endogeneity:

1. Omitted Variable
2. Measurement Error
3. Simultaneity

Now, we are going to talk about these scenarios in detail.

## Omitted Variable

Suppose $$k=2$$, so

$$
Y=\beta_0+\beta_1 X_1+\beta_2 X_2+U
$$

We are interpreting this regression as a casual model and are willing to assume that $$E[X U]=0$$ (i.e., $$E[U]=E\left[X_1 U\right]=E\left[X_2 U\right]=0$$ ), but $$X_2$$ is unobserved. An example of a situation like this is when $$Y$$ is wages, $$X_1$$ is education, and $$X_2$$ is ability.

Given unobserved ability, we may rewrite this model as:

$$
Y=\beta_0^*+\beta_1^* X_1+U^* \text { with } \begin{cases}\beta_0^* & =\beta_0+\beta_2 E\left[X_2\right] \\ \beta_1^* & =\beta_1 \\ U^* & =\beta_2\left(X_2-E\left[X_2\right]\right)+U\end{cases}
$$

Proof:

$$
\begin{aligned} Y & =\beta_0+\beta_1 X_1+\beta_2 X_2+U \\ & =\beta_0+\beta_1 X_1+\beta_2 \mathbb{E}\left[X_2\right]+\underbrace{\beta_2\left(X_2-\mathbb{E}\left[X_2\right]\right)+U}_{U^*} \\ & =\underbrace{\left(\beta_0+\beta_2 \mathbb{E}\left[X_2\right]\right)}_{\beta_0^*}+\underbrace{\beta_1}_{\beta_1^*} X_1+U^* \\ & =\beta_0^*+\beta_1^* X_1+U^* \end{aligned}
$$

Now, if we still use OLS to estimate the $$\beta_1$$ using $$\beta_1^*$$,&#x20;

$$
\hat{\beta}^*=\left(\begin{array}{c} \hat{\beta}_0^* \\ \hat{\beta}_1^* \end{array}\right)
$$

As we are estimating the $$\beta_1^*$$, we can use the method in estimating the sub-vector of beta to get the  $$\hat{\beta_1^*}$$. This is the projection coefficient of $$Y$$ on $$X_1$$ only. By sub-vector of beta estimating formula:

$$
\begin{aligned} \hat{\beta_1^*}& \stackrel{P}{\longrightarrow}\frac{\operatorname{Cov}\left(Y, X_1\right)}{\operatorname{Var}\left(X_1\right)} \\ & =\frac{\operatorname{Cov}\left(\beta_0^*+\beta_1^* X_1+U^*, X_1\right)}{\operatorname{Var}\left(X_1\right)}\\ & =\frac{\operatorname{Cov}\left(\beta_0^*, X_1\right)+\beta_1^* \operatorname{Cov}\left(X_1, X_1\right)+\operatorname{Cov}\left(U^*, X_1\right)}{\operatorname{Var}\left(X_1\right)} \\ & =\frac{0+\beta_1^* \operatorname{Var}\left(X_1\right)+\operatorname{Cov}\left(U^*, X_1\right)}{\operatorname{Var}\left(X_1\right)} \\ & =\beta_1^*+\frac{\operatorname{Cov}\left(U_1^*, X_1\right)}{\operatorname{Var}\left(X_1\right)} \end{aligned}
$$

We can have that:&#x20;

* $$\operatorname{Var}\left(X_1\right) \neq 0$$: This is because $$X_1$$ is a random variable.
* $$\operatorname{Cov}\left(U^*, X_1\right) = \mathbb{E}[X_1U^*] -\mathbb{E}[X_1]\mathbb{E}[U^*] = \mathbb{E}[X_1U^{*}]$$: This is because $$\mathbb{E}[U^{*}]=0$$ and by endogeneity $$\mathbb{E}\left[X_1 U^*\right] \neq 0$$, so we have that $$\operatorname{Cov}\left(U^*, X_1\right)\neq 0$$

Therefore, we have that&#x20;

$$
\hat{\beta}_1^* \neq \beta_1^* = \beta_1
$$

If we measure the $$\beta$$ in whole without using the sub-vector estimation, we can also have that $$\hat{\beta}$$ is inconsistnet.

$$
\hat{\beta}=\left(\begin{array}{c} \hat{\beta_0^*} \\ \hat{\beta}_1^* \end{array}\right) \stackrel{P}{\longrightarrow} \beta+\mathbb{E}\left[X X^{\prime}\right]^{-1} \mathbb{E}\left[X^{\prime} U^*\right]
$$

where we have $$\beta=\left(\begin{array}{l}\beta_0^* \\ \beta_1^*\end{array}\right) \quad X=\left(\begin{array}{l}1 \\ X_1\end{array}\right)$$, and&#x20;

$$
\mathbb{E}\left[X^{\prime} U^*\right]=\mathbb{E}\left[\left(\begin{array}{l}
1 \\
X_1
\end{array}\right) \cdot U^*\right]=\left[\begin{array}{l}
\mathbb{E}\left[U^*\right] \\
\mathbb{E}\left[X_1 U^*\right]
\end{array}\right]
$$

As by endogeneity, $$\mathbb{E}\left[X_1 U^*\right] \neq 0$$, so we CANNOT get $$\hat{\beta}\stackrel{P}{\longrightarrow} \beta$$, means estimatior of $$\beta$$ using OLS is inconsistent.

## Measurement Error

Measurement Error often happens in the survey method, which will also lead to endogenous.

The measurement error often because the misleading information provided by the people taking the survey:

1. Bad memory about the past situations.
2. Intentionally misreport.

Now we formally define this problem:

Partition $$X$$ into $$X_0$$ and $$X_1$$, where $$X_0=1$$ and $$X_1$$ takes values in $$\mathbf{R}^k$$. Partition $$\beta$$ analogously.

$$
Y=\beta_0+X_1^{\prime} \beta_1+U
$$

We are interpreting this regression as a causal model and are willing to assume that $$E[X U]=0$$, but $$X_1$$ is not observed. Instead, $$\hat{X}_1$$ is observed, where

$$
\hat{X}_1=X_1+V
$$

Here, we have that:

* $$\hat{X}_1$$ is observed value, e.g. the result we got from the survey.
* $$X_1$$ is not observed, which denotes the real value of the results.
* $$V$$ is the error because of the measurement error. This is the difference between the observed value and the real value.

Assume (a) $$E[V]=0$$, (b) $$\operatorname{Cov}\left[X_1, V\right]=0$$, and (c) $$\operatorname{Cov}[U, V]=0$$. We may therefore rewrite this model as:

$$
Y=\beta_0^*+\hat{X}_1^{\prime} \beta_1^*+U^* \text { with }\left\{\begin{array}{l} \beta_0^*=\beta_0 \\ \beta_1^*=\beta_1 \\ U^*=-V^{\prime} \beta_1+U \end{array}\right.
$$

































## Simultaneity





