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

If we measure the $$\beta$$ in whole without using the sub-vector estimation, we can also have that $$\hat{\beta}$$ is inconsistnet and biased.

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

As by endogeneity, $$\mathbb{E}\left[X_1 U^*\right] \neq 0$$, so we CANNOT get $$\hat{\beta}\stackrel{P}{\longrightarrow} \beta$$, means estimatior of $$\beta$$ using OLS is inconsistent and biased.

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

Note that, $$\hat{X}_1=X_1 \cdot V$$ is also a possible form, e.g. where $$V=\left(\begin{array}{l}0.1 \\ 0.6 \\ 0.8\\.\\ .\\.\end{array}\right)\neq \mathbb{I}$$, then the errors still exist.

We focus on the summation form. Assume (a) $$E[V]=0$$, (b) $$\operatorname{Cov}\left[X_1, V\right]=0$$, and (c) $$\operatorname{Cov}[U, V]=0$$. We may therefore rewrite this model as:

$$
Y=\beta_0^*+\hat{X}_1^{\prime} \beta_1^*+U^* \text { with }\left\{\begin{array}{l} \beta_0^*=\beta_0 \\ \beta_1^*=\beta_1 \\ U^*=-V^{\prime} \beta_1+U \end{array}\right.
$$

As $$\beta_1^*$$ is the only thing we are interested in. Now we use the projection formula from sub-vector $$\beta$$ estimation:

$$
\begin{aligned} p\lim _{n \rightarrow \infty} \hat{\beta}_1^*& =\frac{\operatorname{Cov}\left(\hat{X}_1, Y\right)}{\operatorname{Var}\left(\hat{X}_1\right)} \\ & =\frac{\operatorname{Cov}\left(\hat{X}_1, \hat{\beta}_0^*+\hat{X}_1 \beta_1^*+U^*\right)}{\operatorname{Var}\left(\hat{X}_1\right)} \\ & =\frac{\operatorname{Cov}\left(\hat{X}_1, \beta_0^*\right)+\beta_1^* \operatorname{Cov}\left(\hat{X}_1, \hat{X}_1\right)+\operatorname{Cov}\left(\hat{X}_1, U^*\right)}{\operatorname{Var}\left(\hat{X}_1\right)} \\ & =\beta_1^*+\frac{\operatorname{Cov}\left(X_1+V, U-V^{\prime} \beta_1\right)}{\operatorname{Var}\left(\hat{X}_1\right)} \\ & =\beta_1^*+\frac{\operatorname{Cov}\left(X_1, U\right)+\operatorname{Cov}\left(U ,V\right)-\operatorname{Cov}\left(X_1, V^{\prime}\beta_1\right)-\operatorname{Cov}\left(V,V^{\prime}\beta_1\right)}{\operatorname{Var}\left(\hat{X}_1\right)} \\ \end{aligned}
$$

As we assume $$\mathbb{E}[X_1U] = 0$$, $$\operatorname{Cov}\left[X_1, V\right]=0$$, and $$\operatorname{Cov}[U, V]=0$$, and $$\beta_1^* = \beta_1$$,&#x20;

$$
p \lim _{n \rightarrow \infty} \hat{\beta}_1^*= \beta_1^* \left(1 - \frac{\operatorname{Var}(V)}{\operatorname{Var}(\hat{X}_1)}\right)
$$

As $$\hat{X}=X_1+V$$, and $$\operatorname{Cov}\left[X_1, V\right]=0$$, we have that&#x20;

$$
\begin{aligned} \operatorname{Var}\left(\hat{X}_1\right) & =\operatorname{Var}\left(X_1+V\right) \\ & =\operatorname{Var}\left(X_1\right)+\operatorname{Var}(V)+2 \operatorname{Cov}\left(X_1, V\right) \\ & =\operatorname{Var}\left(X_1\right)+\operatorname{Var}(V) \end{aligned}
$$

Therefore,&#x20;

$$
p \lim _{n \rightarrow \infty} \hat{\beta}_1^*= \beta_1^* \left(1 - \frac{\operatorname{Var}(V)}{\operatorname{Var}(\hat{X}_1)}\right) = \beta_1^* \left( \frac{\operatorname{Var}(X_1)}{\operatorname{Var}(\hat{X}_1)}\right) < \beta_1^*=\beta_1
$$

Similarly, in the sample form, we have:

$$
\begin{aligned} & \hat{\beta}_1^*=\frac{\widehat{\operatorname{Cov}}\left(x_i^*, y_i\right)}{\widehat{\operatorname{Var}}\left(x_i^*\right)}=\frac{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)\left(y_i-\bar{y}_i\right)}{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2} \\ & =\frac{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)\left(\beta_1^*\left(x_i^*-\bar{x}_i^*\right)+\left(u_i-\bar{u}_i\right)\right)}{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2} \\ & =\beta_1^* \frac{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2}{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2}+\frac{\sum_{i=1}^n\left(x_{i}^*-\bar{x}_i^*\right)\left(u_i-\bar{u}_i\right)}{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2} \\ & =\beta_1^*-\beta_1^* \frac{\sum_{i=1}^n\left(v_i-\bar{v}_i\right)\left(v_i-\bar{v}_i\right)}{\sum_{i=1}^n\left(x_i^*-\bar{x}_i^*\right)^2} \\ & =\beta_1^*\left(1-\frac{\operatorname{Var}\left(v_i\right)}{\operatorname{Var}\left(x_i^*\right)}\right) \\ &=\beta_1\left(1-\frac{\operatorname{Var}\left(v_i\right)}{\operatorname{Var}\left(x_i^*\right)}\right) \end{aligned}
$$

**This means that, under measurement error, the OLS is going to underestimate the coefficient. This bias is called Attenuation Bias. The OLS estimator under measurement error is both inconsistent and biased.**

Note that the part $$\frac{\operatorname{Var}\left(V\right)}{\operatorname{Var}\left(\hat{X}_1\right)}$$is called the noise-to-signal ratio. The estimated $$\hat{\beta_1}^*$$is close to 0 if the measurement error $$V$$'s variance is too big.

## Simultaneity

Simultaneity in the context of econometrics and statistical modeling refers to a situation where a cause-and-effect relationship between two variables is bidirectional, meaning each variable simultaneously affects and is affected by the other. This will lead to endogeneity.

Classical example: supply and demand. Let $$Q^s$$ be quantity supplied and $$Q^d$$ be quantity demanded. As a function of (non-market clearing) price $$\tilde{P}$$, assume

$$
\begin{aligned} & Q^d=\beta_0^d+\beta_1^d \tilde{P}+U^d \\ & Q^s=\beta_0^s+\beta_1^s \tilde{P}+U^s \end{aligned}
$$

* **Price Affects Quantity**: In both equations, price ($$P$$) is an explanatory variable affecting $$Q^d$$ and $$Q^s$$.
* **Quantity Affects Price**: At the same time, in a market, the equilibrium price is determined by the interaction of $$Q^d$$ and $$Q^s$$. This creates a simultaneity problem since the price is both influencing and being influenced by the quantities.

Note that, $$U^d$$ and $$U^s$$ denotes for the other factors that affect demand and supply sides. The other relationship between the price and quantity may be included in them. This will lead to the endogeneity of the equilibrium price $$\tilde{P}$$.

Also we assume where $$E\left[U^s\right]=E\left[U^d\right]=E\left[U^s U^d\right]=0$$. We observe $$(Q, P)$$, where $$Q$$ and $$P$$ are such that the market clears, i.e., $$Q^s=Q^d$$. This implies the equilibrium price $$\tilde{P}$$ is:

$$
\beta_0^d+\beta_1^d \tilde{P}+U^d=\beta_0^s+\beta_1^s \tilde{P}+U^s
$$

$$
\tilde{P}=\frac{\beta_0^d+U^d-\left(\beta_0^s+U^s\right)}{\beta_1^s-\beta_1^d}
$$

Here we can get that,&#x20;

$$
\operatorname{Cov}\left(\tilde{P}, U^d\right)=\operatorname{Cov}\left(\frac{U^d}{\beta_1^s-\beta_1^d}, U^d\right)=\frac{\operatorname{Var}\left(U^d\right)}{\beta_1^s -\beta_1^d} \neq 0
$$

and similarly,&#x20;

$$
\operatorname{Cov}\left(\tilde{P}, U^s\right)=\operatorname{Cov}\left(-\frac{U^s}{\beta_1^s-\beta_1^d}, U^s\right)=-\frac{\operatorname{Var}\left(U^s\right)}{\beta_1^s -\beta_1^d} \neq 0
$$

These lead to the endogeneity of equilibrium price $$\tilde{P}$$.
