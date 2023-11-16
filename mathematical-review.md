---
description: >-
  This is the basic mathematical definitions and calculation methods for
  Econometircs.
---

# Mathematical Review



### Best Predictor

Given a random vector $$X$$, we want to forecast $$Y$$, Let $$g(X)$$ be a predictor of $$Y$$. Then define the the mean squared error of predictor $$g(X)$$ as $$\mathbb{E}[(Y-g(X))^2]$$. We can have that the CEF $$m(x) = \mathbb{E}(Y|X=x)$$ is the best predictor, which has the smallest mean squared prediction error. Which means if we have $$\mathbb{E}(Y^2) < \infin$$, then for any predictor $$g(X)$$, we have:

&#x20;                                                   $$\mathbb{E}[(Y-g(X))^2] \geq \mathbb{E}[(Y-m(X))^2]$$

&#x20;**Proof**:

$$\mathbb{E}[u^2] = \mathbb{E}[(Y-g(X))^2]=\mathbb{E}[(Y-m(X) + m(X) -g(X))^2]$$

&#x20;          $$=\mathbb{E}[(Y-m(X))^2] + \mathbb{E}[(m(X)-g(X))^2]+2\mathbb{E}[(Y-m(X))(m(X) -g(X))]$$

&#x20;          $$\geq \mathbb{E}[(Y-m(X))^2]$$

since: $$\mathbb{E}[(Y-m(X))(m(X) -g(X))] = \mathbb{E}[\mathbb{E}[(Y-m(X))(m(X) -g(X))|X]]$$

as under condition $$X$$, $$m(X) -g(X)$$ is no longer a random variable, by the defination of $$m(X)$$

$$\mathbb{E}[\mathbb{E}[(Y-m(X))(m(X) -g(X))|X]] = \mathbb{E}[(m(X) -g(X))\mathbb{E}[(Y-m(X))|X]] = 0$$

So above inequality becomes equality when $$m(X) = g(X)$$, therefore, $$m(X)$$ is the smallest.
