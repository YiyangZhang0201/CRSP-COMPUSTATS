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

Note that the IV can also be the variable itself, in following regression:

$$
Y=\beta_0+\beta_1 X_1+\beta_2 X_2+U
$$

* If $$E\left[X_1 U\right] \neq 0$$: we can choose to find an IV $$Z$$ for $$X_1$$, such that $$E[Z U]=0$$
* If $$E\left[X_2 U\right]=0$$: $$X_2$$ itself can be view as an IV for $$X_2$$

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

### Lemma:

Suppose there is no perfect collinearity in $$Z$$ and let $$\Pi$$ be such that $$B L P(X \mid Z)=\Pi^{\prime} Z . E\left[Z X^{\prime}\right]$$ has rank $$k+1$$ if and only if $$\Pi$$ has rank $$k+1$$. Moreover, the matrix $$\Pi^{\prime} E\left[Z X^{\prime}\right]$$ is invertible.

Note that if some $$X_j$$ are exogenous, then we do not need IVs for them.













## Interpreting The Rank Condition
