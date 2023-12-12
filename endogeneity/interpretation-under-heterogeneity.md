# Interpretation Under Heterogeneity

Recall that in the model

$$
Y=X^{\prime} \beta+U
$$

the effect of a change in $$X$$ (say, from $$X=x$$ to $$X=x^{\prime}$$ ) is the same for everybody.

**However, the effect of a change in** $$X$$ **on** $$Y$$ **can be different for different people.** To capture this: allow for $$\beta$$ to be random. When $$\beta$$ is random, we may absorb $$U$$ into the intercept and simply write

$$
Y=X^{\prime} \beta .
$$

## Notation

1. With a random sample where variables are indexed by $$i$$, we would write $$Y_i=X_i^{\prime} \beta_i$$, which makes it explicit that every individual has a unique effect $$\beta_i$$.
2.  Assume $$k=1$$ and write $$D$$ in place of $$X_1$$, which is assumed to take values in $$\{0,1\}$$, i.e. $$D$$ is binary. Then,

    $$
    Y=\beta_0+\beta_1 D .
    $$
3.  We interpret $$\beta_0$$ as $$Y(0)$$ and $$\beta_1$$ as $$Y(1)-Y(0)$$, where $$Y(1)$$ and $$Y(0)$$ are potential or counterfactual outcomes. Using this notation, we may rewrite the equation as

    $$
    Y=D Y(1)+(1-D) Y(0)\\\text{or}\\Y= \begin{cases}Y(1) & \text { if } D=1 \\ Y(0) & \text { if } D= 0 .\end{cases}
    $$

    1. $$Y(0)$$ denotes the value of the outcome that would have been observed if (possibly counter-to-fact) $$D$$ were 0 ;
    2. $$Y (1)$$ denotes the value of the outcome that would have been observed if (possibly counter-to-fact) $$D$$ were 1.
4. The variable $$D$$ is typically called the **treatment**&#x20;
5. $$Y(1)-Y(0)$$ is called the **treatment effect**. The quantity $$E[Y(1)-Y(0)]$$ is usually referred to as the **average treatment effect (ATE).** This denotes the "**treatment effect on the overall population"**.
6. &#x20;The quantity $$E[Y(1)-Y(0) \mid D=1]$$ is called the **average treatment effect on treatment group (ATET).** This denotes the "**treatment effect on populations who are treated"**.

Note that:

**The treatment effect is for one individual, however, we cannot observe both outcomes (**$$Y(0) \& Y(1)$$**) from one individual at the same time.**

### **Four Types of People in treatment**

1. Always Taker: $$D(1)=1 \quad D(0)=1$$
2. Complier: $$D(1)=1 \quad D(0)=0$$
3. Never Taker: $$D(1)=0 \quad D(0)=0$$
4. Defier: $$D(1)=0 \quad D(0)=1$$

### Random Assignment

If $$D$$ were randomly assigned (e.g., by the flip of a coin), then

$$
(Y(0), Y(1)) \perp D
$$

In this case, under mild assumptions, the slope coefficient from OLS regression of $$Y$$ on a constant and $$D$$ yields a consistent estimate of the average treatment effect.

Note that if $$D$$ is randomly assigned or the treated group is randomly drawn from sample (Treated group represents for whole population). Then ATE = ATET.

If $$D$$ is binary, we have that: $$Y=\beta_0+\beta_1 D+U$$

$$
\beta_1=\frac{\operatorname{Cov} ( Y, D)}{\operatorname{Var}(D)}=E[Y \mid D=1]-\mathbb{E}[Y \mid D=0]=\mathbb{E}[Y(1) \mid D=1]-\mathbb{E}[Y(0) \mid D=0]
$$

As $$(Y(0), Y(1)) \perp D$$, we can have that $$\beta_1 = E[Y(1)]-E[Y(0)]$$ = ATE / ATET

The estimator of $$\beta_1$$ is&#x20;

$$
\hat{\beta}_1=\frac{1}{n} \sum_{i=1}^n Y_i D_i-\frac{1}{n} \sum_{i=1}^n Y_i \left(1-D_i\right)=\bar{Y}_{D=1}-\bar{Y}_{D=0} .
$$

Therefore, we got $$plim_{n \rightarrow \infin} \hat{\beta_1}=\beta_1$$, which is ATE / ATET.

However, if $$D$$ is not randomly assigned, $$\beta_1 =$$ ATET + Bias. Since under this case,&#x20;

$$
E[Y \mid D=1]-\mathbb{E}[Y \mid D=0] \\= \underbrace{E\left[\mathrm{Y}_{1 i} \mid \mathrm{D}_i=1\right]-E\left[\mathrm{Y}_{0 i} \mid \mathrm{D}_i=1\right]}_{\text {average treatment effect on the treated }}+\underbrace{E\left[\mathrm{Y}_{0 i} \mid \mathrm{D}_i=1\right]-E\left[\mathrm{Y}_{0 i} \mid \mathrm{D}_i=0\right]}_{\text {selection bias }}
$$

This can also be reformed to $$\beta_1 =$$ ATE + Bias.

### Selction

In general, we expect $$D$$ to depend on $$(Y(1), Y(0))$$. Under this condition, OLS does not yield a consistent estimate of the average treatment effect.&#x20;

Note that as treatment $$D$$ is not randomly assigned, which means it is for a selected group, we have that ATE $$\neq$$ ATET.

To proceed further, we therefore assume, as usual, that there is an instrument $$Z$$. Let $$Z \in{0,1}$$.

Consider the slope coefficient from TSLS/IV regression of $$Y$$ on $$D$$ with $$Z$$ as an instrument, $$Z$$ is also binary:

$$
\frac{\operatorname{Cov}[Y, Z]}{\operatorname{Cov}[D, Z]}=\frac{E[Y \mid Z=1]-E[Y \mid Z=0]}{E[D \mid Z=1]-E[D \mid Z=0]}
$$

