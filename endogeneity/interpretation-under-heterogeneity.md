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
3.  We interpret $$\beta_0$$ as $$Y(0)$$ and $$\beta_1$$ as $$Y(1)-Y(0)$$, where $$Y(1)$$ and $$Y(0)$$ are potential or counterfactual outcomes. Using this notation, we may rewrite the equation as **Potential Outcome Model:**

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

Expressing in Terms of Expected Values:

* The numerator, $$E[Y \mid Z=1]-E[Y \mid Z=0]$$, represents the difference in the expected value of $$\mathrm{Y}$$ when $$\mathrm{Z}$$ changes from 0 to 1 .
* The denominator, $$E[D \mid Z=1]-E[D \mid Z=0]$$, represents the difference in the expected value of $$\mathrm{D}$$ (take-up of the treatment) when $$\mathrm{Z}$$ changes from 0 to 1.

Take-Up Ratio: The ratio $$\frac{E[D \mid Z=1]-E[D \mid Z=0]}{\operatorname{Var}[Z]}$$ can be interpreted as the take-up ratio. It indicates the percentage of people who will take the treatment when offered (i.e., when $$\mathrm{Z}$$ changes from 0 to 1 ). It's a measure of the effectiveness of the instrument in inducing changes in the treatment variable.

**Proof:**

Standard Regression Formula: In a simple linear regression, without considering endogeneity, the coefficient $$\beta_1$$ is given by:

$$
\beta_1=\frac{\operatorname{Cov}(Y, D)}{\operatorname{Var}(D)}
$$

IV Regression Setup: However, in the presence of endogeneity (where D is correlated with the error term), this formula doesn't yield a consistent estimate. Here's where IV regression using an instrument $$Z$$ comes into play.

Assumptions:

1. Relevance: $$Z$$ is correlated with $$\mathrm{D}$$ (i.e., $$\operatorname{Cov}(D, Z) \neq 0$$ ).
2. Exogeneity: $$Z$$ is not correlated with the error term in the $$Y$$ regression.

Two-Stage Least Squares (TSLS) Process:

1. First Stage: Regress $$\mathrm{D}$$ on $$\mathrm{Z}$$ and get the fitted values $$\hat{D}$$ :

$$
\begin{aligned} & D=\pi_0+\pi_1 Z+\epsilon \\ & \hat{D}=\pi_0+\pi_1 Z \end{aligned}
$$

2. Second Stage: Regress Y on $$\hat{D}$$ :

$$
Y=\alpha_0+\beta_1 \hat{D}+u
$$

Now, let's derive the IV estimate of $$\beta_1$$ :

1. Covariance of $$Y$$ and $$\hat{D}$$ : The covariance of $$Y$$ with $$\hat{D}$$ is given by:

$$
\operatorname{Cov}(Y, \hat{D})=\operatorname{Cov}\left(Y, \pi_0+\pi_1 Z\right)
$$

Since $$\pi_0$$ is a constant, it drops out in the covariance, leaving:

$$
\operatorname{Cov}(Y, \hat{D})=\pi_1 \operatorname{Cov}(Y, Z)
$$

2. Variance of $$\hat{D}$$ : Similarly, the variance of $\hat{D}$ is:

$$
\operatorname{Var}(\hat{D})=\operatorname{Var}\left(\pi_0+\pi_1 Z\right)
$$

Again, $$\pi_0$$ being constant, it drops out, leaving:

$$
\operatorname{Var}(\hat{D})=\pi_1^2 \operatorname{Var}(Z)
$$

3. Substituting in the Second Stage: In the second stage, $$\beta_1$$ is estimated as the coefficient of $$\hat{D}$$ in the regression of $$Y$$ on $$\hat{D}$$ :

$$
\beta_1=\frac{\operatorname{Cov}(Y, \hat{D})}{\operatorname{Var}(\hat{D})}
$$

Substituting our expressions for $$\operatorname{Cov}(Y, \hat{D})$$ and $$\operatorname{Var}(\hat{D})$$ :

$$
\begin{aligned} & \beta_1=\frac{\pi_1 \operatorname{Cov}(Y, Z)}{\pi_1^2 \operatorname{Var}(Z)} \\ & \beta_1=\frac{\operatorname{Cov}(Y, Z)}{\pi_1 \operatorname{Var}(Z)} \end{aligned}
$$

4. Relation to $$\operatorname{Cov}(D, Z)$$ : From the first stage, we know that $$\pi_1=\frac{\operatorname{Cov}(D, Z)}{\operatorname{Var}(Z)}$$. Substituting $$\pi_1$$ :

$$
\beta_1=\frac{\operatorname{Cov}(Y, Z)}{\frac{\operatorname{Cov}(D, Z)}{\operatorname{Var}(Z)} \cdot \operatorname{Var}(Z)}
$$

Simplifying, we get:

$$
\beta_1=\frac{\operatorname{Cov}(Y, Z)}{\operatorname{Cov}(D, Z)}
$$

WALD estimator is the estimator used for this TSLS regression $$\beta_1$$, it can be represented as:

$$
\hat{\beta}_1=\frac{\hat{E[Y \mid Z=1]}-\hat{E[Y \mid Z=0]}}{\hat{E[D \mid Z=1]}-\hat{E[D \mid Z=0]}}
$$

## Potential Treatments

Now, we want to express this quantity&#x20;

$$
\beta_1 = \frac{\operatorname{Cov}[Y, Z]}{\operatorname{Cov}[D, Z]}=\frac{E[Y \mid Z=1]-E[Y \mid Z=0]}{E[D \mid Z=1]-E[D \mid Z=0]}
$$

in terms of the treatment effect $$Y(1)-Y(0)$$ somehow.

Towards our goal, it is useful to also introduce the following equation for $$D$$:

$$
\begin{aligned} D &= Z D(1)+(1-Z) D(0) \\ & =D(0)+(D(1)-D(0)) Z \\ & =\quad \pi_0+\pi_1 Z  \end{aligned}
$$

where $$\pi_0=D(0), \pi_1=D(1)-D(0)$$, and $$D(1)$$ and $$D(0)$$ are **potential or counterfactual treatments**.

We impose the following versions of instrument exogeneity and instrument relevance, respectively:&#x20;

$$
(Y(1), Y(0), D(1), D(0)) \perp Z
$$

$$
P\{D(1) \neq D(0)\}=P\left\{\pi_1 \neq 0\right\}>0
$$

We further assume the following **Monotonicity Condition**:

$$
P\{D(1) \geq D(0)\}=P\left\{\pi_1 \geq 0\right\}=1
$$

This monotonicity condition eliminates the defiers. If the monotonicity does not hold, we can have that under this condition, $$D(0)=0 \quad (Z=1) < D(0)=1\quad(Z=0)$$, which will include the defiers.

### TSLS Estimator to Form Y(1) - Y(0)

Since the potential outcome is $$E[Y \mid Z=1]-E[Y \mid Z=0]$$&#x20;

as we have&#x20;

$$
\left\{\begin{array}{l} Y=D Y(1)+(1-D) Y(0) \\ D=Z D(1)+(1-Z) D(0) \end{array}\right.
$$

We got&#x20;

$$
\begin{aligned} &E[Y \mid Z=1]-E[Y \mid Z=0]\\ & =\mathbb{E}[D Y(1)+(1-D) Y(0) \mid Z=1]-\mathbb{E}[D Y(1)-(1-D) Y(0) \mid Z=0] . \\ & =\mathbb{E}[D(1) Y(1)+(1-D(1)) Y(0) \mid Z=1]-\mathbb{E}[D( 0) Y(1)-(1-D(0)) Y(0) \mid Z=0] \end{aligned}
$$

since the instrument $$Z$$ here is exogenous

$$
\begin{gathered} =\mathbb{E}\left[D(1) Y(1)+(1-D(1)) Y_0\right]-\mathbb{E}[D(0) Y(1)-(1-D(0)) Y(0)] \\ =\mathbb{E}\{[D(1)-D(0)] Y(1)-[D(1)-D(0)] Y(0)\} \\ =\mathbb{E}\{(D(1)-D(0))(Y(1)-Y(0))\} \end{gathered}
$$

As $$D(1)-D(0)$$ is always 0 for Always Taker and Never Taker,  and by monotonicity condition, we ruled out the Defiers.&#x20;

$$
= \mathbb{E}\left[( D ( 1 ) - D ( 0 ) ) \left(Y(1)-Y\left(0\right)\right) \mid D(1)-D(0)=1\right] P(D(1)-D(0)=1)
$$

$$
= \mathbb{E}\left[( D ( 1 ) - D ( 0 ) ) \left(Y(1)-Y\left(0\right)\right) \mid D(1)-D(0)>1\right]
$$

Which only focuses on the Compliers.

### LATE

The TSLS/IV estimand equals

$$
\frac{\operatorname{Cov}[Y, Z]}{\operatorname{Cov}[D, Z]}=E[\underbrace{Y(1)-Y(0)}_{\mathrm{TE}} \mid \underbrace{D(1)>D(0)}_{\text {local }}] \equiv \mathrm{LATE}
$$

This is called the local average treatment effects. Which denotes the **Average treatment effect of the subpopulation of people for whom a change in the value of the instrument switched them from being non-treated to treated: the so-called compliers.**

Since $$\operatorname{Cov}[Y, Z] = E[Y \mid Z=1]-E[Y \mid Z=0] = E\left[Y(1)-Y{(0)} \mid  D(1)>D(0)\right] P(D(1)-D(0)=1)$$&#x20;

$$\operatorname{Cov}[D, Z] = E[D \mid Z=1]-E[D \mid Z=0]=P\left(D(1)>D(0)\right)$$

This is because $$D=Z D(1)+(1-Z) D(0)$$, then&#x20;

$$
\begin{aligned} E[D \mid Z=1]-E[D \mid Z=0] = & E[D(1) \mid Z=1]-E[D(0) \mid Z=0]\\ = & E[D(1)-D(0)] \\ = & 1 \cdot P(D(1)-D(0)=1)+(-1) P(D(1)-D(0)=-1) \\ & +0 \cdot P(D(1)-D(0)=0)\\ =&P(D(1)-D(0)=1) \end{aligned}
$$

Because we ruled out the defiers.

### Monotonicity

As before, we have shown that monotonicity will rule out the defiers.

Monotonicity: while the instrument may have no effect on some people, all those who are affected are affected in the same way. Without monotonicity, we would have

$$
\begin{gathered} E[Y \mid Z=1]-E[Y \mid Z=0]=E[Y(1)-Y(0) \mid D(1)>D(0)] P\{D(1)> \\ D(0)\}-E[Y(1)-Y(0) \mid D(1)<D(0)] P\{D(1)<D(0)\} . \end{gathered}
$$

Treatment effects may be positive for everyone (i.e., $$Y(1)-Y(0)>0$$ ) yet the reduced form is zero because effects on compliers are canceled out by effects on defiers, i.e., those individuals for which the instrument pushes them out of treatment $$(D(1)=0$$ and $$D(0)=1)$$.

This doesn't come up in a constant effect model where $$\beta=Y(1)-Y(0)$$ is constant, as in such case

$$
\begin{aligned} E[Y \mid Z=1]-E[Y \mid Z=0] & =\beta\{P\{D(1)>D(0)\}-P\{D(1)<D(0)\}\} \\ & =\beta E[D(1)-D(0)], \end{aligned}
$$

and so a zero reduced-form effect means either the first stage is zero or $$\beta=0$$.

### Monotonicity with one-sided Compliance

Randomized trial with non-compliance: the treatment assignment as an "offer of treatment" $$Z$$ (the instrument) and the actual treatment $$D$$ determines whether the subject actually had the treatment.

Assume no one in the control group has access to the treatment: $$D(0)=0$$ while $$D(1) \in\{0,1\}$$, in this case, Monotonicity automatically holds: $$D(1) \geq D(0)$$

Since $$D(1)$$ is a choice, a comparison between those actually treated $$(D=1)$$ and the control $$(D=0)$$ group is misleading. Two alternatives are frequently used.

**Intention to Treat Effect:** a comparison between those who were offered treatment $$(Z=1)$$ and the control $$(Z=0)$$ group.

In this case: LATE = ATT: IV using $$Z$$ as an instrumental variable for $$D$$, which leads to LATE. Since $$D(0)=0$$, LATE returns the effect of treatment on the treated (ATT).

LATE: $$E[Y(1)-Y(0) \mid D(1)>D(0)]$$

ATT: $$E[Y(1)-Y(0) \mid D=1]$$
