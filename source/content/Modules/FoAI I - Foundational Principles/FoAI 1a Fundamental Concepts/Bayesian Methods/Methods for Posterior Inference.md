As mentioned in [[Bayesian Inference]], one of the biggest weaknesses of the Bayesian framework is the intractable marginal likelihood/evidence: $$p(X)=\int p(X|\theta)p(\theta)$$ In this note, we discuss the ways through which this computational barrier can be overcome.
## Markov Chain Monte Carlo (MCMC) Methods
See [[MCMC Methods]] for a more detailed coverage of this topic.

**Markov Chain Monte Carlo (MCMC)** refers to a family of algorithms for sampling from complex probability distributions when direct sampling is difficult or impossible. The core idea is to construct a **Markov chain** whose _stationary distribution_ is the target distribution you want to sample from. By running the chain for many steps, the samples it produces approximate draws from that target distribution.
### **Key Features:**
- Markov chain: 
	Each new sample depends only on the previous one, not on the full history.
- **Monte Carlo:**
    Uses randomness to approximate integrals, expectations, and probabilities.
- **Stationary distribution:**
    The chain is designed so that after a “burn-in” period, the distribution of states converges to the target distribution.
- **Unnormalised densities allowed:**
    MCMC requires only a function proportional to the target pdf — perfect for Bayesian posteriors, where the evidence (normalising constant) is hard to compute.
  

MCMC methods are especially useful in **Bayesian inference**, where the posterior distribution may have no closed form but can be evaluated up to a constant. Note that **MCMC algorithms only provide asymptotic guarantees of convergence** (i.e. in the limit of large sample size) to the true posterior distribution.
### **Common algorithms:**
- **Metropolis–Hastings:** Propose a new sample, accept/reject it based on a likelihood ratio.
- **Gibbs sampling:** Sample each variable from its conditional distribution.
- **Hamiltonian Monte Carlo (HMC):** Uses gradient information and simulated physics to make long-distance proposals with high acceptance rate.
- **Slice sampling:** Samples by “slicing” the density function and exploring level sets.
### Limitations of MCMC methods
As datasets grew larger and models became higher-dimensional, traditional MCMC-based Bayesian inference began to struggle computationally:
- **Curse of dimensionality** - Sampling efficiency deteriorates exponentially with dimensionality. 
- **Conditional sampling** - Sequential conditional updates make MCMC inherently diffcult to parallelise.
- **Need to update all model parameters** - each MCMC iteration requires updating all parameters - in some models, the number of parameters grows with the data size. 

## Variational Inference
See [[Variational Inference]] for a more detailed coverage of this topic.
![[Pasted image 20251112232238.png]]
Variational inference methods estimate the posterior by approximating it with a distribution of a simpler form. In this way, variational methods trade *asymptotic exactness* (i.e. in the limit of large sample size $n$) for *optimisation-based  approximation*. 

The **mean-field approximation** ($O(NP)$) is given by $$p(\theta_1,...,\theta_P|X)\approx \prod_{p=1}^P q_{\phi_P}(\theta_P|X)$$
In the mean-field approximation, a set of *variational parameters* are tied to each data point.

The use of **amortisation** provides a second layer of approximation ($O(N)$): $$\phi_p=f_\nu(X_p)$$
where instead of optimising all variational parameters, you learn a function that maps relevant subsets of data to estimates of those parameters.
