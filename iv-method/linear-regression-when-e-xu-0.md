# Linear Regression When E\[XU]!=0

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X \in \mathbf{R}^{k+1}$$. Assume further that $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$ and let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$



**Not that now, we do not assume** $$E[X U]=0$$**.** Any $$X_j$$ such that $$E\left[X_j U\right]=0$$ is said to be exogenous; Any $$X_j$$ such that $$E\left[X_j U\right] \neq 0$$ is said to be endogenous. Normalizing $$\beta_0$$ if necessary, we view $$X_0$$ as exogenous.

Now we raise a question, what will happen to the OLS estimator in this setting?

The&#x20;

## Endogeneity

**The endogeneity means that there is correlation between regressor** $$X$$ **and error term** $$U$$**. Means** $$Corr(X,U) \neq 0$$**, this leads to the assumption** $$E[X U]=0$$**.**

There are three scenarios that can leads to endogeneity:

1. Omitted Variable
2. Measurement Error
3. Simultaneity

Now, we are going to talk about these scenarios in detail.

### Omitted Variable



### Measurement Error



### Simultaneity



## Instrumental Variables

