The process of updating beliefs on a parameter(s) using Bayesian inference is as follows:

1. Begin with **prior** belief over a parameter $\theta$ encapsulated by a probability distribution $p(\theta)$. 

2. Acquire data $X$ according to some process/experiment which is controlled by $\theta$. The probability of observing $X$ given $\theta$ is known as the **likelihood**, $p(X \mid \theta)$. 

3. Compute the **posterior** probability distribution $p(\theta \mid X)$ of $\theta$ given data $X$ using Bayes’ Theorem:
$$
\underbrace{p(\theta \mid X)}_{\text{Posterior}}=\underbrace{\frac{\overbrace{p(X \mid \theta)}^{\text{Likelihood}} \,\overbrace{p(\theta)}^{\text{Prior}}}{\underbrace{p(X)}_{\text{Marginal Likelihood / Evidence}}}}_{\text{Posterior}}
$$
where $\theta$ denotes a parameter and $X$ is data.

>[!warning]- Intractability of the Marginal Likelihood
> The marginal likelihood $$p(X)=\int p(X\mid \theta)dp(\theta)$$
> is generally intractable and is the computational barrier to the application of Bayesian belief updating.

### Iterated Bayesian Updating
The Bayesian update can be iterated via 
$$
\underbrace{p(\theta \mid X_{\text{new},\text{old}})}_{\text{Updated Posterior}}=\frac{\overbrace{p(X_{\text{new}} \mid \theta)}^{\text{Likelihood}}\,\overbrace{p(\theta \mid X_{\text{old}})}^{\text{Prior = Previous Posterior}}}{\underbrace{p(X_{\text{new}} \mid X_{\text{old}})}_{\text{Marginal Likelihood / Evidence}}}
$$
where $X_{\text{old/new}}$ is the old and new data respectively.

This allows *sequential updating* of knowledge.

### Advantages of Bayesian Inference
It allows you to (through the prior): 
1. Define preferred values or ranges for parameters. 
2. Regularise and make models more stable. 
3. Enforce bias or assumptions.

Additionally, it provides a framework for **uncertainty quantification** via the posterior and marginal evidence.



