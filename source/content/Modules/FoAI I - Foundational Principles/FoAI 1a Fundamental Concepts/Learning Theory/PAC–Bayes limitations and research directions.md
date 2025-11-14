# PAC–Bayes limitations and research directions

While PAC–Bayes theory provides a compelling bridge between classical learning theory and modern deep learning, it is not without challenges.  Understanding its limitations is important when applying the theory to real‑world models.

## Limitations

1. **Computational intractability.**  Computing the exact posterior $Q(f\mid D)$ or optimising the PAC–Bayes bound is typically intractable for complex models such as deep networks.  Approximations (e.g. variational methods) may not capture the true training dynamics.
2. **Choice of prior.**  The bound depends on a data‑independent prior $P(f)$.  Selecting a realistic yet tractable prior is non‑trivial.  Data‑dependent priors can tighten bounds but may violate the assumptions of the theorem.
3. **Loose or asymptotic constants.**  The constants in PAC–Bayes bounds can be loose, making the bounds qualitatively informative but not numerically tight.  They are often asymptotic and require large sample sizes to become meaningful.
4. **Interpretability in deep networks.**  Mapping SGD dynamics to an explicit posterior or prior is still an open challenge; it is difficult to connect theoretical posteriors to real training trajectories.

## Research directions

Researchers are actively working to overcome these limitations.  Current directions highlighted in the slides include:

1. **Data‑dependent priors.**  Defining priors informed by the data or model structure (e.g. using a subset of training data or pretrained weights) can tighten PAC–Bayes bounds.
2. **Approximate and variational posteriors.**  Learning tractable approximations to the posterior (such as Gaussian or low‑rank distributions) leads to optimisable PAC–Bayes objectives for neural networks.  Stochastic gradient variational inference has been proposed for this purpose.
3. **Connections to flatness and compression.**  Recent work links PAC–Bayes bounds to flat minima and model compression: flat posteriors correspond to low KL divergence, and compressible models have short description lengths.
4. **Towards practical bounds for deep learning.**  Efforts are underway to develop scalable empirical PAC–Bayes bounds that apply to modern architectures and to combine these with information‑theoretic or algorithmic stability approaches.

### Links to other topics

* A derivation of the PAC–Bayes bound and its interpretation is given in [[PAC–Bayes theory]].
* The limitations of classical VC theory and the need for modern perspectives are discussed in [[Overparameterised models and double descent]].
