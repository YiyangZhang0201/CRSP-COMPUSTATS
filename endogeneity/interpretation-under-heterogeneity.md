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

### Random Assignment

If $$D$$ were randomly assigned (e.g., by the flip of a coin), then

$$
(Y(0), Y(1)) \perp D
$$

In this case, under mild assumptions, the slope coefficient from OLS regression of $$Y$$ on a constant and $$D$$ yields a consistent estimate of the average treatment effect.



