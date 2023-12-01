# Linear Regression When E\[XU]=0

## Assumptions for Linear Regression when E\[XU]=0

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Assume further that $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$ and let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$

We will make following three assumptions for this model.

1. $$E[X U]=0$$**: The justification of 1 varies depending on which of the three preceding interpretations we invoke.** This expectation refers to the covariance between the regressor $$X$$ and the error term $$U$$ being zero.
   1.  **For Linear Conditional Expectation:** In this interpretation, the regression is viewed as modeling the conditional expectation of $$Y$$ given $$X$$. That is, $$E[Y \mid X]=\beta_0+\beta_1 X$$.

       Here, $$U$$ represents the deviation of $$Y$$ from its conditional expectation given $$X$$. Since $$U$$ is defined as $$Y-E[Y \mid X]$$, it inherently means that $$E[U \mid X]= 0$$ . Consequently, this implies that $$E[X U]=0$$, because the error term $$U$$ has no systematic relationship with $$X$$ when considering the conditional expectation.
   2.  **For Best Linear Approximation:** In the best linear approximation, the regression equation is considered the best linear approximation to the true relationship between $$Y$$ and $$X$$, regardless of the true underlying relationship.&#x20;

       The error term $$U$$ in this context captures all factors that affect $$Y$$ but are not captured by $$X$$. For the linear approximation to be the 'best', it requires that these omitted factors (captured in $$U$$ ) are uncorrelated with $$X$$. **If** $$X$$ **were correlated with** $$U$$**, there would be systematic information in** $$X$$ **that could improve the approximation, contradicting the premise that the model is the 'best' linear approximation.** Hence, $$E[X U]=0$$ is necessary to ensure that the linear model is indeed the best approximation under the given circumstances.
   3.  **For Causal Model:** the regression is understood as modeling a causal relationship between $$X$$ and $$Y$$. Here, $$\beta_1$$ is interpreted as the causal effect of $$X$$ on $$Y$$.

       For $$\beta_1$$ to represent the causal effect of $$X$$ on $$Y$$, it is crucial that all other factors influencing $$Y$$ are either controlled for or are not correlated with $$X$$. The error term $$U$$ includes all these other factors. **If** $$U$$ **were correlated with** $$X$$**, it would mean that there are omitted variables that both affect** $$Y$$ **and are related to** $$X$$**, which would bias the estimation of the causal effect.** Therefore, ensuring $$E[X U]=0$$ is essential for a valid causal interpretation, as it implies that there are no omitted confounders that are correlated with $$X$$.
2.  $$E\left[X X^{\prime}\right]<\infty$$**, this 2 ensures that** $$E\left[X X^{\prime}\right]$$ **exists.**

    This matrix $$E\left[X X^{\prime}\right]$$ is called **Design Matrix**.
3.  **There is NO PERFECT COLLINEARITY in** $$X$$ or **the matrix** $$E\left[X X^{\prime}\right]$$ **is in fact invertible.**

    Since $$E\left[X X^{\prime}\right]$$ is positive semi-definite, **invertibility of** $$E\left[X X^{\prime}\right]$$ **is equivalent to** $$E\left[X X^{\prime}\right]$$ **being positive definite.** **This ensures there is a unique solution to** $$\beta$$ **when solving for it.** So, this is also called the **identification condition** for $$\beta$$**.**

We can talk more detail about Invertibility:

**Definition:**

There is perfect collinearity or multicollinearity in $$X$$ if there exists nonzero $$c \in \mathbf{R}^{k+1}$$ such that $$P\{c^{\prime} X=0\}=1$$, (Here we treat X as a random variable.), i.e., if we can express one component of $$X$$ as a linear combination of the others.

**Lemma:**

Let $$X$$ be such that $$E\left[X X^{\prime}\right]<\infty$$. Then $$E\left[X X^{\prime}\right]$$ is invertible iff there is no perfect collinearity in $$X$$.

**Proof**:

If there is perfect collinearity, such that $$\exist c \neq0$$ that

$$
c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c=\mathbb{E}\left[c^{\prime} X X^{\prime} c\right]=\mathbb{E}\left[\left(c^{\prime} X\right)^2\right]=0 \text { with } P=1
$$

In order for $$E\left[X X^{\prime}\right]$$ to be positive definite, $$c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c$$ can take value 0, but it cannot have this with P=1. So, $$c^{\prime} \mathbb{E}\left[X X^{\prime}\right] c$$ is not positive definite, therefore it is not invertible. This is a contradiction.

Note that, based on the calculation rule of the matrix, $$(A B)^{\prime}=B^{\prime} A^{\prime}$$, we have $$(X^{\prime} Z)^{\prime}=Z^{\prime} X$$, therefore,&#x20;

$$
\begin{aligned} Z^{\prime} \mathbb{E}\left[X X^{\prime}\right] Z & =\mathbb{E}\left[Z^{\prime} X X^{\prime} Z\right]=\mathbb{E}\left[Z^{\prime} X\left(Z^{\prime} X\right)^{\prime}\right] \\ & =\mathbb{E}\left[\left(Z^{\prime} X\right)^2\right] \geqslant 0 \end{aligned}
$$

So, $$E\left[X X^{\prime}\right]$$ is always positive semi-definite, we need $$E\left[X X^{\prime}\right]>0$$ with $$P>0$$ to be **positive definite.**

## Solving for Beta

* $$E[U X]=0$$ implies that $$E\left[X\left(Y-X^{\prime} \beta\right)\right]=0$$, which is the FOC for optimization problem $$\underset{b \in \mathbb{R}^{k+1}}{\operatorname{argmin}} E\left[\left(Y-X^{\prime} b\right)^2\right]$$: $$\frac{\partial \mathbb{E}\left[\left(Y-X^{\prime} b\right)^2\right]}{\partial b}=\mathbb{E}\left[\frac{\partial\left(Y-X^{\prime} b\right)^2}{\partial b}\right]=\mathbb{E}\left[\left(Y-X^{\prime} b\right) \cdot X\right]=0$$
* As $$\beta$$ is the solution to this optimization problem. So, we have $$\mathbb{E}\left[\left(Y-X^{\prime} \beta\right) \cdot X\right]=0$$
* $$\mathbb{E}[Y X]-\mathbb{E}\left[X^{\prime} X \beta\right]=0$$ $$\Rightarrow$$ $$\mathbb{E}[X Y]=\mathbb{E}[X X^{\prime}]\beta$$
* As $$E\left[X X^{\prime}\right]<\infty$$ and $$E\left[X X^{\prime}\right]$$ is positive definite. So, it exists and is invertible. We have:

&#x20;                                                           $$\beta=\left[\mathbb{E}\left[X X^{\prime}\right]\right]^{-1} \mathbb{E}[X Y]$$           &#x20;

Note that, here the $$\beta$$ we got is the linear projection coefficient.&#x20;

* **And for** $$E[U X]=0$$**, we can have that** $$E[U] = 0$$**.**

**Proof:**

Since $$E[U X]=0$$ indicates $$X$$ is independent with $$U$$,  $$\mathbb{E}[x_j u]=0$$ for $$j = 1 , \cdots, k$$.$$\Rightarrow$$$$x_j \perp u$$

$$Cov(X, U) = \mathbb{E}[XU] - \mathbb{E}[X]\mathbb{E}[U] = 0 - \mathbb{E}[X]\mathbb{E}[U] = 0$$

As $$\mathbb{E}[X] \neq 0$$, so we have $$\mathbb{E}[U]=0$$.

* **If** $$E\left[X X^{\prime}\right]$$ **is not invertible (not positive definite), there will be more than one solution to this system of equations.** Any two solutions $$\beta$$ and $$\tilde{\beta}$$ will necessarily satisfy $$X^{\prime} \beta=X^{\prime} \tilde{\beta}$$.

## Estimating Beta using OLS

Let $$(Y, X, U)$$ be as described and let $$P$$ be the marginal distribution of $$(Y, X)$$. And let $$\left(Y_1, X_1\right), \ldots,\left(Y_n, X_n\right)$$ be an i.i.d. sequence of random vectors with distribution $$P$$.

A natural estimator of $$\beta=\left(E\left[X X^{\prime}\right]\right)^{-1} E[X Y]$$ is simply:

$$
\hat{\beta}=\left(\frac{1}{n} \sum_{1 \leq i \leq n} X_i X_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_{1 \leq i \leq n} X_i Y_i\right)=\left(\sum_{1 \leq i \leq n} X_i X_i^{\prime}\right)^{-1}\left(\sum_{1 \leq i \leq n} X_i Y_i\right)
$$

This estimator is called the **ordinary least squares (OLS) estimator** of $$\beta$$ because it can also be derived as the solution to the following minimization problem:

$$
\min _{b \in \mathbf{R}^{k+1}} \frac{1}{n} \sum_{1 \leq i \leq n}\left(Y_i-X_i^{\prime} b\right)^2
$$

Here:

* $$\hat{\beta}$$ is a random variable, since it is $$f\left(X_i, Y_i\right)$$
* By Law of Large Number: $$\frac{1}{n} \sum_{1 \leqslant i \leqslant n} X_i X_i^{\prime} \stackrel{P}{\longrightarrow} \mathbb{E}\left[X_i X_i^{\prime}\right]$$
* By Law of Large Number: $$\frac{1}{n} \sum_{1 \leqslant i \leqslant n} X_i Y_i^{\prime} \stackrel{P}{\longrightarrow} \mathbb{E}\left[X_i Y_i^{\prime}\right]$$
* Note that for more efficient estimator $$\hat{\beta}$$, its Variance is smaller.

**Proof:**

Define Objective Function:

$$
Q(b)=\frac{1}{n} \sum_{i=1}^n\left(Y_i-X_i^{\prime} b\right)^2
$$

We take the derivative of the objective function w.r.t. $$b$$ and get the FOC:

$$
\frac{\partial Q}{\partial b}=-\frac{2}{n} \sum_{i=1}^n X_i\left(Y_i-X_i^{\prime} b\right)=0
$$

Then by FOC, we have that:

$$
\begin{aligned} & -\frac{2}{n} \sum_{i=1}^n X_i\left(Y_i-X_i^{\prime} b\right)=0 \\ & \sum_{i=1}^n X_i Y_i-\sum_{i=1}^n X_i X_i^{\prime} b=0 \end{aligned}
$$

Now, we rearrange to solve for $$b$$ :

$$
\begin{aligned} & \sum_{i=1}^n X_i X_i^{\prime} b=\sum_{i=1}^n X_i Y_i \\ & \left(\sum_{i=1}^n X_i X_i^{\prime}\right) b=\sum_{i=1}^n X_i Y_i \end{aligned}
$$

Dividing by $$n$$ to align with your provided formulation:

$$
\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right) b=\frac{1}{n} \sum_{i=1}^n X_i Y_i
$$

Finally, solving for $$b$$, the result will be our $$\hat{\beta}$$:

$$
\hat{\beta} = b=\left(\frac{1}{n} \sum_{i=1}^n X_i X_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_{i=1}^n X_i Y_i\right)
$$

Now we finished the proof.

Note that we can also apply weight to the above formula to make this a **weighted least squares (WLS)** estimator.&#x20;

$$
\min _{b \in \mathbf{R}^{k+1}} \frac{1}{n} \sum_{1 \leq i \leq n}W_i \left(Y_i-X_i^{\prime} b\right)^2
$$

So, we have that OLS is a special case of WLS. In this case, $$W_i$$s are equal to $$1$$.

### Matrix Notation

Define

$$
\begin{aligned} \mathbb{Y} & =\left(Y_1, \ldots, Y_n\right)^{\prime} \\ \mathbb{X} & =\left(X_1, \ldots, X_n\right)^{\prime} \\ \hat{\mathbb{Y}} & =\left(\hat{Y}_1, \ldots, \hat{Y}_n\right)^{\prime} =\mathbb{X} \hat{\beta} \\ \mathbb{U} & =\left(U_1, \ldots, \mathbb{U}_n\right)^{\prime} \\ \hat{\mathbb{U}} & =\left(\hat{U}_1, \ldots, \hat{U}_n\right)^{\prime} \\ & =\mathbb{Y}-\hat{\mathbb{Y}}  =\mathbb{Y}-\mathbb{X} \hat{\beta} . \end{aligned}
$$

In this notation,

$$
\hat{\beta}=\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{Y}
$$

and may be equivalently described as the solution to

$$
\min _{b \in \mathbf{R}^{k+1}}|\mathbb{Y}-\mathbb{X} b|^2 .
$$

Hence, $$\mathbb{X} \hat{\beta}$$ is the vector in the column space of $$\mathbb{X}$$ that is the closest (in terms of Euclidean distance) to $$\mathbb{Y}$$.

$$
\mathbb{X} \hat{\beta}=\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{Y}
$$

is the orthogonal projection of $$Y$$ onto the $$((k+1)$$-dimensional) column space of $$\mathbb{X}$$.

The matrix

$$
\mathbb{P}=\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}
$$

is known as the **Projection Matrix**. It projects a vector in $$\mathbf{R}^n$$ (such as $$\mathbb{Y}$$ ) onto the column space of $$\mathbb{X}$$.

Note that $$\mathbb{P}^2=\mathbb{P}$$, which reflects the fact that projecting something that already lies in the column space of $$\mathbb{X}$$ onto the column space of $$\mathbb{X}$$ does nothing.

The matrix $\mathbb{P}$ is also symmetric. The matrix

$$
\mathbb{M}=\mathbb{I}-\mathbb{P}
$$

is also a projection matrix. It projects a vector onto the $$((n-k-1)$$-dimensional) vector space orthogonal to the column space of $$\mathbb{X}$$. Hence, $$\mathbb{M X}=0$$. Note that $$\mathbb{M Y}=\hat{\mathbb{U}}$$. For this reason, $$\mathbb{M}$$ is sometimes called the **"residual maker" matrix**.

**Proof**:

* $$\mathbb{P}\mathbb{X} = \mathbb{X}$$:&#x20;

$$
\mathbb{P} \mathbb{X}=\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} \mathbb{X}=\mathbb{X}\left[\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1}\left(\mathbb{X}^{\prime} \mathbb{X}\right)\right]=\mathbb{X} \mathbb{I}=\mathbb{X}
$$

* $$\mathbb{P}^2 = \mathbb{P}$$:&#x20;

$$
\mathbb{P}^2=\left(\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}\right)\left(\mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}\right)^{\prime} = \mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime}\mathbb{X}[\left(\mathbb{X}^{\prime}\mathbb{X}\right)^{-1}]^{\prime} \mathbb{X}^{\prime} = \mathbb{X}\left(\mathbb{X}^{\prime} \mathbb{X}\right)^{-1} \mathbb{X}^{\prime} = \mathbb{P}
$$

* $$\mathbb{P M}=0$$:

$$
\mathbb{P M}=\mathbb{P}(\mathbb{I}-\mathbb{P }) = \mathbb{P} - \mathbb{P}^2 = \mathbb{P}-\mathbb{P}=0
$$

## Sub-Vectors of Beta

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X$$ takes values in $$\mathbf{R}^{k+1}$$. Let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ such that

$$
Y=X^{\prime} \beta+U
$$

Partition $$X$$ into $$X_1$$ and $$X_2$$, where $$X_1$$ takes values in $$\mathbf{R}^{k_1}$$ and $$X_2$$ takes values in $$\mathbf{R}^{k_2}$$. Partition $$\beta$$ into $$\beta_1$$ and $$\beta_2$$ analogously. In this notation,

$$
Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U
$$

Our preceding results imply that:

$$
\left(\begin{array}{l} \beta_1 \\ \beta_2 \end{array}\right)=\left[E\left(\begin{array}{l} X_1 \\ X_2 \end{array}\right)\left(X_1^{\prime} X_2^{\prime}\right)\right]^{\prime} E\left(\begin{array}{l} X_1 \\ X_2 \end{array}\right) Y
$$

$$
\left(\begin{array}{l} \beta_1 \\ \beta_2 \end{array}\right)=\left(\begin{array}{ll} E\left[X_1 X_1^{\prime}\right] & E\left[X_1 X_2^{\prime}\right] \\ E\left[X_2 X_1^{\prime}\right] & E\left[X_2 X_2^{\prime}\right] \end{array}\right)^{-1}\left(\begin{array}{l} E\left[X_1 Y\right] \\ E\left[X_2 Y\right] \end{array}\right)
$$

This is derived from the general linear model estimation method, specifically the Ordinary Least Squares (OLS) method, under the assumption that:

* &#x20;The expected value of the error term $$U$$ is zero and that $$U$$ is uncorrelated with $$X$$.
* Existence and invertibility of matrix:

$$
\left(\begin{array}{ll} E\left[X_1 X_1^{\prime}\right] & E\left[X_1 X_2^{\prime}\right] \\ E\left[X_2 X_1^{\prime}\right] & E\left[X_2 X_2^{\prime}\right] \end{array}\right)
$$

Question: Can we derive formulae for $$\beta_1$$ and $$\beta_2$$ that admit some interesting interpretations?

1. Partial Effects: The coefficients in $$\beta_1$$ and $$\beta_2$$ can be interpreted as the partial effects of the variables in $$X_1$$ and $$X_2$$ on $$Y$$, controlling for the other variables. This means that $$\beta_1$$ captures the impact of $$X_1$$ on $$Y$$ while holding $$X_2$$ constant, and vice versa for $$\beta_2$$.
2. Multicollinearity Consideration: In cases where there is multicollinearity (i.e., high correlation) between some variables in $$X_1$$ and $$X_2$$, partitioning the regression can help understand how each group of variables uniquely contributes to explaining the variation in $$Y$$.
3. Group-Specific Analysis: This partitioning is particularly useful when $$X_1$$ and $$X_2$$ represent distinct groups of variables, such as demographic factors versus economic indicators. It allows for the isolation of the effects of each group on $$Y$$.
4. Interpreting in Context: The interpretation of $$\beta_1$$ and $$\beta_2$$ will highly depend on the specific context of the study. For instance, in an economic growth model, $$X_1$$ might include labor and capital variables, while $$X_2$$ includes policy variables. The coefficients would then tell us about the distinct impacts of these groups on economic growth.
5. Statistical Significance: It's important to evaluate the statistical significance of the estimated coefficients in $$\beta_1$$ and $$\beta_2$$ to determine if the observed relationships are not due to random chance.
6. Estimation Challenges: If $$X_1$$ and $$X_2$$ are highly correlated, the inverse of the matrix in the formula may be difficult to compute accurately, leading to estimation problems. This is a common issue in models with multicollinearity.

### Result Based on BLP

BLP: for a random variable $$A$$ and a random vector $$B$$, denote by $$\operatorname{BLP}(A \mid B)$$ the best linear predictor of $$A$$ given $$B$$, i.e.

$$
\operatorname{BLP}(A \mid B) \equiv B^{\prime}\left(E\left[B B^{\prime}\right]\right)^{-1} E[B A] .
$$

If $$A$$ is a random vector, then define $$\mathrm{BLP}(A \mid B)$$ component-wise.

And we also define $$\tilde{A}=A-\operatorname{BLP}(A \mid B)$$.

**Now, come back to our problem:** $$Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U$$

Define $$\tilde{Y}=Y-\operatorname{BLP}\left(Y \mid X_2\right)$$ and $$\tilde{X}_1=X_1-\operatorname{BLP}\left(X_1 \mid X_2\right)$$. Consider the linear regression

$$
\tilde{Y}=\tilde{X}_1^{\prime} \tilde{\beta}_1+\tilde{U} \text { where } E\left[\tilde{X}_1 \tilde{U}\right]=0
$$

as for example, in the second interpretation of the linear regression model: Best Linear Approximation that we described before, then we can have that:

$$
\tilde{\beta}_1=\left(E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\right)^{-1} E\left[\tilde{X}_1 \tilde{Y}\right]=\beta_1
$$

**Proof:**

First we can have the following result based on the definition of $$\tilde{Y}$$ and $$\tilde{X}_1$$:

* $$Y=X_2^{\prime} \gamma+U_2$$ $$\Rightarrow$$ $$\mathbb{E}\left[X_2 U_2\right]=0$$ $$\Rightarrow$$ $$U_2=\tilde{Y}$$$$=Y-X_2^{\prime} \gamma$$
* $$X_1 = X_2^{\prime} \eta+e$$ $$\Rightarrow$$ $$\mathbb{E}\left[X_2 e\right]=0$$ $$\Rightarrow$$ $$e=\tilde{X}_1$$$$\Rightarrow$$ $$\mathbb{E}\left[X_2 \tilde{X}_1^{\prime}\right]=0$$

Above can be got because $$U_2$$ and $$e$$ are projections from linear regression models.

For formula $$\tilde{\beta}_1=\left(E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\right)^{-1} E\left[\tilde{X}_1 \tilde{Y}\right]$$,  we will first separate the right-hand side $$E\left[\tilde{X}_1 \tilde{Y}\right]$$

$$E\left[\tilde{X}_1 \tilde{Y}\right] = E\left[\tilde{X}_1 (Y-X_2^{\prime} \gamma)\right]$$$$= E\left[\tilde{X}_1 Y\right]-E\left[\tilde{X}_1X_2^{\prime} \gamma\right]$$

Since $$\tilde{X}_1$$ can be viewed as a scaler, we can have that as $$\mathbb{E}\left[X_2 \tilde{X}_1^{\prime}\right]=0$$, then $$E\left[\tilde{X}_1 X_2^{\prime} \gamma\right] = E\left[X_2\tilde{X}_1^{\prime}  \gamma\right] = E\left[X_2\tilde{X}_1^{\prime}  \right]\gamma = 0$$

Now we have that: $$E\left[\tilde{X}_1 \tilde{Y}\right]=E\left[\tilde{X}_1 Y\right]$$, take the original formula $$Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U$$ inside, we can have that:&#x20;

* $$U \perp X_1$$, and $$U \perp X_2$$, since we are under the interpretation of the Best Linear Approximation.
* $$E[\tilde{X}_1 Y] = E[\tilde{X}_1 (X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U)]$$$$=E\left[\tilde{X}_1X_1^{\prime} \right]\beta_1+E\left[\tilde{X}_1X_2^{\prime}\right] \beta_2+E\left[\tilde{X}_1U\right]$$
  * As we have shown $$E\left[\tilde{X}_1 X_2^{\prime}\right] =0$$ $$\Rightarrow$$ $$E\left[\tilde{X}_1 X_2^{\prime}\right] \beta_2=0$$
  * As $$U \perp X_1$$ $$\Rightarrow$$ $$E\left[\tilde{X}_1 U\right]=0$$

Now we got that $$E\left[\tilde{X}_1 \tilde{Y}\right]=E\left[\tilde{X}_1 Y\right]=E\left[\tilde{X}_1 X_1^{\prime}\right] \beta_1$$, now for $$E\left[\tilde{X}_1 X_1^{\prime}\right]$$, we can have that:

$$E\left[\tilde{X}_1 X_1^{\prime}\right] = E\left[\tilde{X}_1 (X_2^{\prime} \eta+e)^{\prime}\right] = E\left[\tilde{X}_1 X_2^{\prime} \eta\right]+E\left[\tilde{X}_1e^{\prime}\right]$$

* For $$E\left[\tilde{X}_1 X_2^{\prime} \eta\right]$$, as $$e \perp X_2^{\prime} \eta$$ because of the projection, we have $$\tilde{X}_1 = e \perp X_2^{\prime} \eta$$, so $$E\left[\tilde{X}_1 X_2^{\prime} \eta\right]=0$$
* For $$E\left[\tilde{X}_1 e^{\prime}\right]$$, as $$e=\tilde{X}_1$$, we have that $$E\left[\tilde{X}_1 e^{\prime}\right] = E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]$$

Now we got that $$E\left[\tilde{X}_1 \tilde{Y}\right]=E\left[\tilde{X}_1 Y\right]=E\left[\tilde{X}_1 X_1^{\prime}\right] \beta_1 = E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\beta_1$$

Take this into the formula of $$\tilde{\beta}_1$$, we can have that:

$$
\tilde{\beta}_1=\left(E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\right)^{-1} E\left[\tilde{X}_1 \tilde{Y}\right] = \left(E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\right)^{-1}E\left[\tilde{X}_1 \tilde{X}_1^{\prime}\right]\beta_1＝\mathbb{I}\beta_1=\beta_1
$$

Now we successfully proved the above equation.

### Interpretation

Above equaation can be interpreted like this: $$\beta_1$$ in the linear regression of $$Y$$ on $$X_1$$ and $$X_2$$ is equal to the coefficient in a linear regression of the error term from a linear regression of $$Y$$ on $$X_2$$ on the error terms from a linear regression of the components of $$X_1$$ on $$X_2$$.

**This formalizes the common description of** $$\beta_1$$ **as the "effect" of** $$X_1$$ **on** $$Y$$ **after  "controlling for** $$X_2$$**. "**

Take $$X_2=$$ constant and $$X_1 \in \mathbf{R}$$. Then $$\tilde{Y}=Y-E[Y]$$ and $$\tilde{X}_1=X_1-E\left[X_1\right]$$. Hence,

$$
\beta_1=\left(E\left[\left(X_1-E\left[X_1\right]\right)^2\right]\right)^{-1} E\left[\left(X_1-E X_1\right)(Y-E[Y])\right]=\frac{\operatorname{Cov}\left[X_1, Y\right]}{\operatorname{Var}\left[X_1\right]}
$$

**Proof:**

As $$X_2$$ is a constant, we define $$X_2=1$$ for simplicity. In this way, we have $$Y=\beta_2+\beta_1 X_1+U$$.

Therefore, we use $$X_2$$ to estimate $$X_1$$ and $$Y$$, we can have that:

* $$X_1 = C + e$$, to get the BLP of $$X_1$$, we minimize over $$\min _C E\left(X_1-C\right)^2$$ $$\Rightarrow$$ FOC: $$-2 E\left(X_1-C\right)=0$$ $$\Rightarrow$$ $$C=E[X_1]$$
* $$Y=D+e$$, to get the BLP of $$Y$$, we minimize over $$\min _D E\left(Y-D\right)^2 \Rightarrow$$ FOC: $$-2 E\left(Y-D\right)=0 \Rightarrow D=E\left[Y\right]$$

In this way, we can get that $$\tilde{Y}=Y-E[Y]$$ and $$\tilde{X}_1=X_1-E\left[X_1\right]$$.

Now, based on the interpretation we shown above, we can have that:

$$
\tilde{Y}=\beta_ 1\tilde{X}_1+\epsilon
$$

So, in order to solve the $$\beta_1$$, we have that we need to minimize over $$E_{\beta}(\tilde{Y}-\beta_1 \tilde{X}_1)^2$$

The FOC for this problem is $$E(\tilde{Y}-\beta _1\tilde{X}_1) \tilde{X}_1=0$$ $$\Rightarrow$$ $$E(\tilde{Y} \tilde{X}_1)=\beta _1E(\tilde{X}_1 \tilde{X}_1)$$

So, we got&#x20;

$$
\beta_1=\frac{E\left(\tilde{Y} \tilde{X}_1\right)}{E\left(\tilde{X}_1^2\right)}
$$

Take $$\tilde{Y}=Y-E[Y]$$ and $$\tilde{X}_1=X_1-E\left[X_1\right]$$ into this equation, we have $$\beta_1=\left(E\left[\left(X_1-E\left[X_1\right]\right)^2\right]\right)^{-1} E\left[\left(X_1-E X_1\right)(Y-E[Y])\right]=\frac{\operatorname{Cov}\left[X_1, Y\right]}{\operatorname{Var}\left[X_1\right]}$$ being proved.

Now, we start to check the individual elements in vector $$\beta$$:

**If we use our formula to interpret the coefficient** $$\beta_j$$**, we obtain:**

$$
\beta_j=\frac{\operatorname{Cov}\left[\tilde{X}_j, Y\right]}{\operatorname{Var}\left[\tilde{X}_j\right]} .
$$

$$\Rightarrow$$ each coefficient in a multivariate regression is the bivariate slope coefficient for the corresponding regressor, after "partialling out" all the other variables in the model.

### Estimating Sub-Vectors of Beta

Partition $$X$$ and $$\beta$$ as before and consider

$$
Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U
$$

We use $$\hat{\beta}=\left(\hat{\beta}_1^{\prime}, \hat{\beta}_2^{\prime}\right)^{\prime}$$ to denote the LS estimator of $$\beta$$ in a regression of $$Y$$ on $$X$$.

We now derive estimation counterparts to the previous results about solving for sub-vectors of $$\beta$$. That is, $$\hat{\beta}_1$$ can also be obtained from a "residualized" regression.

As we can have that $$\tilde{Y}=\tilde{X}_1^{\prime}\beta_1 +\epsilon$$,  just treat this residualized regression as an ordinary regression we have shown before. Using OLS to get the best estimator of $$\beta_1$$

$$
\hat{\beta}_1=\left(\frac{1}{n} \sum_{1 \leq i \leq n} \tilde{X}_{1 i} \tilde{X}_{1 i}{ }^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_{1 \leq i \leq n} \tilde{X}_{1 i} \tilde{Y}_i\right)=\left(\sum_{1 \leq i \leq n} \tilde{X}_{1 i} \tilde{X}_{1 i}{ }^{\prime}\right)^{-1}\left(\sum_{1 \leq i \leq n} \tilde{X}_{1 i} \tilde{Y}_i\right)
$$

### Matrix Form

Let $$\mathbb{X}_1=\left(X_{1,1}, \ldots, X_{1, n}\right)^{\prime}$$ and $$\mathbb{X}_2=\left(X_{2,1}, \ldots, X_{2, n}\right)^{\prime}$$.

Denote by $$\mathbb{P}_1$$ the projection matrix onto the column space of $$\mathbb{X}_1$$ and $$\mathbb{P}_2$$ the projection matrix onto the column space of $$\mathbb{X}_2$$.

Define Residual Makers $$\mathbb{M}_1=\mathbb{I}-\mathbb{P}_1$$ and $$\mathbb{M}_2=\mathbb{I}-\mathbb{P}_2$$.&#x20;

* Apply $$\mathbb{M}_2$$ to $$\mathbb{X}_1$$ to get the residualized version of $$\mathbb{X}_1$$: $$\tilde{\mathbb{X}}_1=\mathbb{M}_2 \mathbb{X}_1$$
* Apply $$\mathbb{M}_2$$ to $$\mathbb{Y}$$ to get the residualized version of $$\mathbb{Y}$$: $$\tilde{\mathbb{Y}}=\mathbb{M}_2 \mathbb{Y}$$

The regression model now becomes $$\widetilde{\mathbb{Y}}=\beta_1 \widetilde{\mathbb{X}}_1+\epsilon$$, where $$\epsilon$$ is the error term.

Then use Ordinary Least Squares (OLS) to estimate $$\beta_1$$. The formula for $$\hat{\beta}_1$$ is similar to before:&#x20;

$$
\hat{\beta}_1=\left(\tilde{\mathbb{X}}_1^{\prime} \tilde{\mathbb{X}}_1\right)^{-1} \tilde{\mathbb{X}}_1^{\prime} \widetilde{\mathbb{Y}}
$$
