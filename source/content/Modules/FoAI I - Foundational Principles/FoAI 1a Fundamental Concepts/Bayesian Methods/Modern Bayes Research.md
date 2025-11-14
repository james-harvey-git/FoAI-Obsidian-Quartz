In this note, some of the issues with Bayesian inference methods and the modern research to combat these are outlined.

In recent years, *explicit* Bayesian modeling has reduced in popularity or exposure. For instance, the majority of modern ML is explicitly frequentist because of the tractability of the point approximation (see [[Frequentist Vs Bayesian]]). But unlike previous centuries, it remains in widespread *implicit* use throughout science and engineering.

Traditional Bayesian Analysis is *purist*, pragmatically we need to deal with the following:
- **Prior elicitation** - defining a "good" prior is hard (see [[Modules/FoAI I - Foundational Principles/FoAI 1b Modern Concepts and Practices/Diffusion Models/index|index]])
- **Uncertainty quantification** - MCMC and VB under-estimate posterior variance (see [[MCMC Methods]] and [[Variational Inference]] respectively)
- **Causality** - Bayesian reasoning is concerned with probabilistic coherence not causal reasoning (see [[Modules/FoAI I - Foundational Principles/FoAI 1a Fundamental Concepts/Causal Methods/index|index]] and [[Causality in Bayes]])
- **Model misspecification** - all the theorems discussed in this topic only hold under the *true* model (see [[Model Misspecification]])

Modern Bayesian research seeks to address these issues.