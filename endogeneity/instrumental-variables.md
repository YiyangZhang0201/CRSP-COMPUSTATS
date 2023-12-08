# Instrumental Variables

## Instrumental Variables

In order to overcome the difficulty associated with $$E[X U] \neq 0$$ (endogeneity). We assume that there is an additional random vector $$Z$$ taking values in $$\mathbf{R}^{l+1}$$ with $$l+1 \geq k+1$$ such that $$E[Z U]=0$$.

Any exogenous component of $$X$$ is contained in $$Z$$ (the so-called included instruments). In particular, we assume the first component of $$Z$$ is constant equal to one, i.e., $$Z=\left(Z_0, Z_1, \ldots, Z_l\right)^{\prime}$$ with $$Z_0=1$$.

We also assume that $$E\left[Z X^{\prime}\right]<\infty, E\left[Z Z^{\prime}\right]<\infty$$ and that there is no perfect collinearity in $$Z$$.

In summary, we assume:

1. $$E[Z U]=0$$: **Instrument Exogeneity**
2. $$E\left[Z X^{\prime}\right]<\infty$$
3. $$E\left[Z Z^{\prime}\right]<\infty$$
4. There is no perfect collinearity in $$Z$$
5.  We further assume the rank of $$E\left[Z X^{\prime}\right]$$ is $$k+1$$. This is termed **Instrument Relevance** or **Rank Condition.**

    A necessary condition for 5 to be true is $$l \geq k$$. This is referred to as the **Order Condition**.

To further understand the IV estimator, we need to know the following:

For regression&#x20;

$$
Y=X^{\prime} \beta+U
$$

* $$X$$: dimension is $$(k+1) \times 1$$
* $$Z$$: dimension is $$(\ell+1) \times 1$$, and $$l \geqslant k$$
* $$Z$$ only influence $$Y$$through $$X$$, this means that $$Z$$ only correlated with $$X$$ but not correlated with $$U$$.&#x20;

**Here is an example of using IV in real-world empirical analysis:**

To analyze the education level of out-of-service military people education level's (e.g., years of schooling) relationship with proximity to the school (e.g., distance to the nearest school or a measure of school accessibility), we can choose draft lottery return status (e.g., whether an individual was likely to be drafted for military service) as an Instrument Variable. Now, we check the relevance and exogenity of the draft lottery return status as an IV.

* **Relevance**: The draft lottery status could affect an individual's proximity to school, as those with a higher likelihood of being drafted might choose to stay in school longer or closer to educational institutions.
* **Exogeneity**: The draft lottery status is presumably random and thus not correlated with the unobserved factors affecting education levels directly.

Therefore, the draft lottery return status can serve as a good IV.

## Solving For Beta

Using that $$U=Y-X^{\prime} \beta$$ and $$E[Z U]=0$$, we see that $$\beta$$ solves the system of equations

$$
E[Z Y]=E\left[Z X^{\prime}\right] \beta
$$

**Proof**:

$$E[Z Y]=E\left[Z(U+X^{\prime}\beta)\right] = 0 + E\left[Z X^{\prime}\right] \beta = E\left[Z X^{\prime}\right] \beta$$

Note that the invertible of $$E\left[Z X^{\prime}\right]$$ is not guaranteed. This is because since $$l+1 \geq k+1$$, this may be an over-determined system of equations. There is more information than we need. Which can be shown in the following:

$$
Z=\left(\begin{array}{c} 1 \\ Z_1 \\ \vdots \\ Z_l \end{array}\right)_{(l+1) \times 1} \quad X=\left(\begin{array}{c} 1 \\ X_1 \\ \vdots \\ X_k \end{array}\right)_{(k + 1) \times 1} \quad \beta=\left(\begin{array}{c} 1\\ \beta_1 \\ \vdots \\ \beta_k \end{array}\right)_{(k+1) \times 1}
$$

Therefore, in order to solve for $$\beta$$, we introduce the following lemma:

### Lemma

Suppose there is no perfect collinearity in $$Z$$ and let $$\Pi$$ be such that $$B L P(X \mid Z)=\Pi^{\prime} Z . E\left[Z X^{\prime}\right]$$ has rank $$k+1$$ if and only if $$\Pi$$ has rank $$k+1$$. Moreover, the matrix $$\Pi^{\prime} E\left[Z X^{\prime}\right]$$ is invertible.

Note that if some $$X_j$$ are exogenous, then we do not need IVs for them.

### Solve for Beta

As $$\beta \text { solves: } E[Z Y]=E\left[Z X^{\prime}\right] \beta \text { or } \Pi^{\prime} E[Z Y]=\Pi^{\prime} E\left[Z X^{\prime}\right]\beta$$, then we can have that using the previous lemma and $$\Pi=E\left[Z Z^{\prime}\right]^{-1} E\left[Z X^{\prime}\right]$$, we can derive three formulae for $$\beta$$

Since we have $$X=\left(\begin{array}{c}1 \\ X_1 \\ \vdots \\ X_k\end{array}\right) \quad Z=\left(\begin{array}{c}1 \\ Z \\ \vdots \\ Z_l\end{array}\right)$$, and $$\Pi=\left[\Pi_0, \Pi_1, \cdots, \Pi_k\right]$$, the shape of $$\Pi$$ is $$(l+1)\times(k+1)$$.

First regression $$X$$ on instrument variable $$Z$$:

$$
\begin{aligned} X_0&=Z^{\prime} \Pi_0+U_0=1 \\ X_1&=Z^{\prime} \Pi_1+U_1 \\ X_2&=Z^{\prime} \Pi_2+U_2 \\ \vdots \\ X_k&=Z^{\prime} \Pi_k+U_k \end{aligned}
$$

Then we can get the BLP of $$\Pi_i$$s from these equations:

$$
\begin{aligned} & \Pi_1=\left(\mathbb{E} Z Z^{\prime}\right)^{-1} \mathbb{E}\left[Z X_1\right] \\ & \Pi_2=\left(\mathbb{E} Z Z^{\prime}\right)^{-1} \mathbb{E}\left[Z X_2\right] . \\ & \vdots \\ & \Pi_k=\left(\mathbb{E} Z Z^{\prime}\right)^{-1} \mathbb{E}\left[Z X_k\right] \end{aligned}
$$

Note that if $$X_1$$ is exogenous, then $$Z_1=X_1$$, projection $$X_1$$ on $$Z$$, we can have that,&#x20;

$$
\Pi_1=\left(\begin{array}{c} 0 \\ 1 \\ 0 \\ \vdots \\ 0 \end{array}\right)\text{ where }\beta_1=1
$$

This is because, in $$X_1$$'s regression on $$Z$$, we can have that $$X_1=\beta_0+\beta_1 X_1+\beta_2 Z_2+\cdots+U$$, in this regression model, $$X_1$$ will perfectly explain itself.

#### Equation 1: IV estination

By $$\Pi^{\prime} E[Z Y]=\Pi^{\prime} E\left[Z X^{\prime}\right] \beta$$, we have that,&#x20;

$$
\beta=\left[\Pi^{\prime} E\left(Z X^{\prime}\right)\right]^{-1} \Pi^{\prime} E[Z Y]
$$

&#x20;As $$\Pi=E\left[Z Z^{\prime}\right]^{-1} E\left[Z X^{\prime}\right]$$,  and if $$l=k$$, we can have that:

$$
\begin{aligned} \beta & =\left[E(Z X^{\prime})^{\prime}\left(E\left(Z Z^{\prime}\right)\right)^{-1} E(Z X^{\prime})\right]^{-1} E\left(Z X^{\prime}\right)^{\prime} (E(Z Z^{\prime}))^{-1} E(ZY) \\ & =E\left(Z X^{\prime}\right)^{-1} E\left(Z Z^{\prime}\right)\left[E\left(Z X^{\prime}\right)^{\prime}\right]^{-1}E\left(Z X^{\prime}\right)^{\prime} E\left(Z Z^{\prime}\right)^{-1} E (Z Y) \\ & =E\left(Z X^{\prime}\right)^{-1} E (Z Y) \end{aligned}
$$

#### Equation 2: TSLS Version 1

As we can have that:

$$
X=\left(\begin{array}{c} 1\\ X_1 \\ \vdots \\ X_k \end{array}\right)=\left(\begin{array}{c} Z^{\prime} \Pi_0 \\ Z^{\prime} \Pi_1 \\ \vdots \\ Z^{\prime} \Pi_k \end{array}\right)+\left(\begin{array}{c} U_0 \\ U_1 \\ \vdots \\ U_k \end{array}\right)=\Pi^{\prime} Z+U .
$$

As $$\Pi^{\prime}Z$$ is the BLP of $$X$$, we can have that $$E[U]=0 \text{ and } E[ZU]=0$$.





#### Equation 3: TSLS Version 2









### Interpreting The Rank Condition (**Instrument Relevance)**

















### Partition of Beta: Endogenous Components

Note that the IV can also be the variable itself, in following regression:

$$
Y=X_1^{\prime} \beta_1+X_2^{\prime} \beta_2+U
$$

* If $$E\left[X_1 U\right] \neq 0$$: we can choose to find an IV $$Z_1$$ for $$X_1$$, such that $$E[Z_1 U]=0$$
* If $$E\left[X_2 U\right]=0$$: $$X_2$$ itself can be view as an IV for $$X_2$$, such as $$Z_2 = X_2$$

Here, we partition $$X$$ into $$X_1$$ and $$X_2$$, where $$X_2$$ is exogenous. Partition $$Z$$ into $$Z_1$$ and $$Z_2$$ and $$\beta$$ into $$\beta_1$$ and $$\beta_2$$ analogously.

We have that, in this model:

* $$Z_2=X_2$$ are **included instruments**&#x20;
* $$Z_1$$ are **excluded instruments**&#x20;

We can conveniently re-write this by projecting $$(B L P)$$ on $$Z_2=X_2$$. Consider the case $$k=l$$

$$
B L P\left(Y \mid Z_2\right)=B L P\left(X_1 \mid Z_2\right)^{\prime} \beta_1+X_2^{\prime} \beta_2 .
$$

Define $$Y^*=Y-B L P\left(Y \mid Z_2\right)$$ and $$X_1^*=X_1-B L P\left(X_1 \mid Z_2\right)$$ so that

$$
E\left[Z_1 Y^*\right]=E\left[Z_1 X_1^{* \prime}\right] \beta_1+E\left[Z_1 U\right]
$$

It follows that

$$
\beta_1=\left(E\left[Z_1 X_1^{* \prime}\right]\right)^{-1} E\left[Z_1 Y^*\right]
$$









## IV Estimator

The IV estimator is used under the case that number of instrument variables is equal to the number of explanatory variables. Means using it in the following condition:

$$
\text { Just-identified case: } l=k
$$

Denote $$P$$ the marginal distribution of $$(Y, X, Z)$$. Let $$\left(Y_1, X_1, Z_1\right), \ldots,\left(Y_n, X_n, Z_n\right)$$ be an i.i.d. sequence of random variables with distribution $$P$$.

By analogy with $$\beta=\left(E\left[Z X^{\prime}\right]\right)^{-1} E[Z Y]$$, the natural estimator of $$\beta$$ is simply

$$
\hat{\beta}=\left(\frac{1}{n} \sum_i Z_i X_i^{\prime}\right)^{-1}\left(\frac{1}{n} \sum_i Z_i Y_i\right) .
$$

This estimator is called the instrumental variables (IV) estimator of $$\beta$$. Note that $$\hat{\beta}$$ satisfies

$$
\frac{1}{n} \sum_i Z_i\left(Y_i-X_i^{\prime} \hat{\beta}\right)=0
$$

In particular, $$\hat{U}_i=Y_i-X_i^{\prime} \hat{\beta}$$ satisfies

$$
\frac{1}{n} \sum_i Z_i \hat{U}_i=0 .
$$

**Insight on the IV estimator:** assume $$X_0=1$$ and $$X_1 \in \mathbf{R}$$. An interesting interpretation of the IV estimator $$\beta_1$$ is obtained by multiplying and dividing by $$\frac{1}{n} \sum_{i=1}^n\left(Z_{1, i}-\bar{Z}_{1, n}\right)^2$$, i.e.,

$$
\begin{aligned} \hat{\beta}_1 & =\frac{\frac{1}{n} \sum_{i=1}^n\left(Z_{1, i}-\bar{Z}_{1, n}\right) Y_i / \frac{1}{n} \sum_{i=1}^n\left(Z_{1, i}-\bar{Z}_{1, n}\right)^2}{\frac{1}{n} \sum_{i=1}^n\left(Z_{1, i}-\bar{Z}_{1, n}\right) X_{1, i} / \frac{1}{n} \sum_{i=1}^n\left(Z_{1, i}-\bar{Z}_{1, n}\right)^2} \\ & =\frac{\text { slope of } Y \text { on } Z}{\text { slope of } X \text { on } Z} . \end{aligned}
$$

### Matrix Notation

This estimator may be expressed more compactly using matrix notation. Define

$$
\begin{aligned} & \mathbb{Z}=\left(Z_1, \ldots, Z_n\right)^{\prime} \\ & \mathbb{X}=\left(X_1, \ldots, X_n\right)^{\prime} \\ & \mathbb{Y}=\left(Y_1, \ldots, Y_n\right)^{\prime} \end{aligned}
$$

In this notation, we have

$$
\hat{\beta}=\left(\mathbb{Z}^{\prime} \mathbb{X}\right)^{-1}\left(\mathbb{Z}^{\prime} \mathbb{Y}\right) .
$$
