# IV Method

**In this section , we are going to focus on Linear Regression When** $$E[XU] \neq 0$$**.**&#x20;

Let $$(Y, X, U)$$ be a random vector where $$Y$$ and $$U$$ take values in $$\mathbf{R}$$ and $$X \in \mathbf{R}^{k+1}$$. Assume further that $$X=\left(X_0, X_1, \ldots, X_k\right)^{\prime}$$ with $$X_0=1$$ and let $$\beta=\left(\beta_0, \beta_1, \ldots, \beta_k\right)^{\prime} \in \mathbf{R}^{k+1}$$ be such that

$$
Y=X^{\prime} \beta+U
$$



**Not that now, we do not assume** $$E[X U]=0$$**.** Any $$X_j$$ such that $$E\left[X_j U\right]=0$$ is said to be exogenous; Any $$X_j$$ such that $$E\left[X_j U\right] \neq 0$$ is said to be endogenous. Normalizing $$\beta_0$$ if necessary, we view $$X_0$$ as exogenous.

Now we raise a question, what will happen to the OLS estimator in this setting?

The&#x20;
