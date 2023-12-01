# Measures of Fit

For the Measure of Fit, we usually report $$R^2$$

$$
R^2=\frac{E S S}{T S S}=1-\frac{S S R}{T S S}
$$

where we have that:

* $$T S S=\sum_{1 \leq i \leq n}\left(Y_i-\bar{Y}_n\right)^2$$: total sum of squares
* $$E S S=\sum_{1 \leq i \leq n}\left(\hat{Y}_i-\bar{Y}_n\right)^2$$: explained sum of squares
* $$S S R=\sum_{1 \leq i \leq n} \hat{U}_i^2$$: residual sum of squares
* $$TSS = ESS +SSR$$

Note that, for $$\bar{Y}_n$$, we have that $$\bar{Y}_n = \frac{1}{n} \sum_{i=1}^n Y_i = \frac{1}{n} \sum_{i=1}^n \hat{Y}_i$$

* $$R^2=1$$ if and only if $$S S R=0$$, i.e., $$\hat{U}_i=0$$ for all $$1 \leq i \leq n$$.
* $$R^2=0$$ if and only if $$E S S=0$$, i.e., $$\hat{Y}_i=\bar{Y}_n$$ for all $$1 \leq i \leq n$$.

For the interpretations of these measures:

* View $$\frac{1}{n} \sum_{1 \leq i \leq n}\left(\hat{Y}_i-\bar{Y}_n\right)^2$$ as an estimator of $$\operatorname{Var}\left[Y_i\right]$$
* View $$\frac{1}{n} \sum_{1 \leq i \leq n} \hat{U}_i^2$$ as an estimator of $$\operatorname{Var}\left[U_i\right]$$
* $$R^2$$ may be then viewed as an estimator of $$1-\frac{\operatorname{Var}\left[U_i\right]}{\operatorname{Var}\left[Y_i\right]}$$
* Replacing these estimators with their unbiased counterparts yields "adjusted" $$R^2$$, which is&#x20;

$$
\bar{R}^2=1-\frac{n-1}{n-k-1} \frac{S S R}{T S S}
$$

As $$R^2$$ always increases with the inclusion of an additional regressor, to deal with this problem, we should use "adjusted" $$R^2$$: $$\bar{R}^2$$.
