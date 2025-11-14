# PAC–Bayes theory

Classical PAC learning analyses a single hypothesis $\hat{f}$ chosen by a learning algorithm.  **PAC–Bayes theory** generalises this framework by reasoning about a *distribution* over hypotheses.  It blends PAC learning with Bayesian intuition, leading to generalisation bounds that depend on a prior and posterior distribution over $\mathcal{F}$.

## Setup

Consider a hypothesis class $\mathcal{F}$ (e.g. neural networks) and a loss function $\ell$.  We choose a **prior distribution** $P(f)$ over $\mathcal{F}$, independent of the data.  After observing a dataset $D$, the learning algorithm produces a **posterior distribution** $Q(f\mid D)$.  Predictions are made by sampling $f\sim Q$ and computing $f(x)$.

The goal is to bound the **true risk** of the stochastic predictor (drawn from $Q$) in terms of the **empirical risk** and the divergence between $Q$ and $P$.

## PAC–Bayes bound

One form of the PAC–Bayes bound, due to McAllester, states that for any $\varepsilon\in (0,1)$, with probability at least $1-\varepsilon$ over the choice of the sample $D$, the following holds for all posterior distributions $Q$:

$$
R(Q) \leq \hat{R}(Q) + \frac{\mathrm{KL}(Q\,\|\,P) + \log(2n/\varepsilon)}{2n},
$$

where:

* $R(Q) = \mathbb{E}_{f\sim Q}\,\mathbb{E}_{(x,y)\sim P}\,\ell(y,f(x))$ is the true (population) risk of the stochastic predictor.
* $\hat{R}(Q) = \mathbb{E}_{f\sim Q}\,(1/n)\sum_{i=1}^n \ell(y_i,f(x_i))$ is the empirical risk.
* $\mathrm{KL}(Q\,\|\,P)$ is the Kullback–Leibler divergence between the posterior and prior.

This bound holds simultaneously for all $Q$, making it applicable to any learning algorithm that outputs a posterior distribution.  The complexity penalty $\mathrm{KL}(Q\,\|\,P)$ plays a role similar to the VC dimension in PAC learning but is data dependent.

## Interpretation of the KL term

The KL divergence measures how much the posterior $Q$ differs from the prior $P$.  In the PAC–Bayes view, a small KL implies that the learner’s posterior remains close to the prior and thus encodes little information about the training data.  This corresponds to **low complexity** and tends to yield better generalisation.  Conversely, a large KL means the posterior deviates significantly from the prior, suggesting overfitting.

## Connection to flat minima and implicit regularisation

Deep networks often contain many parameter configurations achieving near‑zero training loss.  Optimisers such as stochastic gradient descent tend to find **flat minima**, regions in parameter space where many nearby configurations perform well.  A posterior concentrated over such a wide region stays closer to the prior,
<details>

<summary>💡 Why?</summary>

Because the prior expresses our beliefs about the model parameters before seeing any data (i.e. pre training), and as we don't know anything about the distribution of parameters that work well, an uninformative broad distribution (like a Gaussian) is assumed. Thus, if the posterior is concentrated over a wider region, it's probability mass isn't concentrated in just one single region of the prior and therefore it more closely matches the prior.

</details>
leading to a smaller KL and better PAC–Bayes generalisation.  This perspective provides a probabilistic explanation for why implicitly regularised models generalise despite their huge capacity.

## Advantages and scope

PAC–Bayes bounds are **data dependent**: they adapt to the actual posterior produced by the learning algorithm.  They naturally accommodate stochastic models or training methods such as dropout.  However, computing or optimising the posterior is often intractable for complex models (see [[PAC–Bayes limitations and research directions]] for discussion).

### Links to other topics

* The limitations of VC dimension motivate moving towards PAC–Bayes bounds; see [[VC dimension and shattering]] and [[Overparameterised models and double descent]].
* Practical challenges, open problems and research directions are described in [[PAC–Bayes limitations and research directions]].
* The break between classical PAC theory and foundation models is discussed in [[PAC learning vs foundation models]].
