When discussing model specification, [[Bayesian Inference|Bayesians]] refer to **M-closed** and **M-open** worlds.

## M-closed world
In an **M-closed** **world**:
- The true data generating process described by parameters $\theta^*$ lies within our model family $\{p(X|\theta):\theta\in\Theta\}$ i.e. we have $\theta^*\in\Theta$
- Classical Bayes is **well-calibrated and coherent**
- Posterior concentrates around the true parameter $\theta^*$

## M-open world
In an **M-open world**:
- The true data generating process is **outside** our model family
- The likelihood $p(X|\theta)$ is **misspecified** i.e. the model class does not match the DGP
- Classical Bayes can be **overconfident or misleading**
- Traditionally, Bayesians tried to overcome this by using **Bayesian nonparametrics** to define infinite-dimensional functions and random probability measures
	- i.e. using all possible models as our model class

$\implies$ In M-open world settings, we need a more flexible update rule to account for misspecification. [[Generalised Bayes]] replaces the likelihood with a *loss*.

## Related
- [[Causality in Bayes]]
- [[Bayesian Inference]]
- [[Generalised Bayes]]

