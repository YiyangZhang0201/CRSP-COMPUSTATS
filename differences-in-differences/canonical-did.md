# Canonical DID

We consider panel data $$y_{i, t}$$ for $$t=1,2$$ and $$i=1,2, \cdots, n$$.

Treatment timing: some units $$\left(D_i=1\right)$$ are treated in period 2 , and everyone else untreated $$\left(D_i=0\right)$$

Potential outcomes: we observe $$y_{i, t}(1) \equiv y_{i, t}(0,1)$$ for treated units, and $$y_{i, t}(0) \equiv y_{i, t}(0,0)$$for untreated units.

Parallel trends:

$$
E\left[y_{i, t=2}(0)-y_{i, t=1}(0) \mid D_i=1\right]=E\left[y_{i, t=2}(0)-y_{i, t=1}(0) \mid D_i=0\right]
$$

No anticipation: $$y_{i, t=1}(1)=y_{i, t=1}(0)$$.

