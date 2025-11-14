As discussed in [[Modern Bayes Research]], Bayesian reasoning is concerned with *probabilistic coherence* rather than *causal reasoning*. 

## Likelihood: Correlation Vs Causation
![[Pasted image 20251113132653.png]]
- The likelihood $p(\theta|X)$ contains a **probabilistic graphical model** (PGM) for your problem which describes the **statistical dependencies** between all quantities in your model. 
	- A PGM only encodes correlations, not causal relation which can exhibit interventions. A conditional probability has no mechanism for encoding a forceful setting of a variable to a value which breaks the usual causal mechanisms that would have determined it.
- However, it does not strictly harbour the **data generating process** (DGP) as it does not allow **interventions** - where a variable in a system is forced to take a particular value, breaking the usual causal mechanisms that would have determined it (e.g. exogenous noise).
- In contrast, a **structural causal model** (SCM) does incorporate interventions such as exogenous noise
>[!key-insight] Key Insight
>A PGM does not define a data generation model *under* interventions.

## Is Causality Required?
While causal models add structure to describe interventions, Bayesian reasoning doesn't require causality - it operates at the level of probabilistic coherence.

A recent line of thought is to do away with causal inference approaches and to add specific mirror-like "counterfactual" variables to mirror an intervention (see [[Model Misspecification]]).

## Related
- For more on causal methods, see [[Modules/FoAI I - Foundational Principles/FoAI 1a Fundamental Concepts/Causal Methods/index|Causal Methods Index]]
- [[Model Misspecification]]
- [[Bayesian Inference]]
- [[Modern Bayes Research]]
