# Model risk and empirical risk minimisation

Machine learning is fundamentally about minimising some notion of **risk** or expected loss.  Classical learning theory formalises different notions of risk and defines the models that minimise them.

## Population risk and Bayes model

Given a loss function $\ell(y,f(x))$ and a joint distribution $P(x,y)$, the **population risk** of a model $f$ is

$$
R(f) = \mathbb{E}_{x,y}[\ell(y,f(x))] = \int \ell(y,f(x))\,\mathrm{d}P(x,y),
$$

the expected loss over the true data distribution.  The **Bayes model** $f_0$ is the function (or functions) that minimises this population risk across all measurable functions: $f_0 \in \arg\inf_{f\in\mathcal{F}} R(f)$.  It represents the ideal predictor if we had infinite data and unlimited model capacity.  Unfortunately, $P(x,y)$ is rarely known in practice, so $R(f)$ and $f_0$ are generally unobservable.

## Restricted model families and best‑in‑class

In practice we restrict ourselves to a **hypothesis class** $\mathcal{F}$ (e.g. linear models or neural networks).  Within this class, the **best‑in‑class model** is

$$
f^* = \arg\inf_{f\in\mathcal{F}} R(f),
$$

the model in $\mathcal{F}$ with minimal population risk.  If the hypothesis class does not contain the true Bayes model, $f^*$ will incur non‑zero approximation error.  Examples include using linear functions to approximate a non‑linear target or using ReLU networks when the true function is smooth.

## Empirical risk and the ERM solution

Since we cannot compute $R(f)$ exactly, we approximate it using our sample.  Given data $D = \{(x_i,y_i)\}_{i=1}^n$ drawn i.i.d. from $P(x,y)$, the **empirical risk** is

$$
\hat{R}(f) = \frac{1}{n} \sum_{i=1}^n \ell(y_i, f(x_i)).
$$

The **empirical risk minimiser (ERM)** is the function

$$
\hat{f} = \arg\inf_{f\in\mathcal{F}} \hat{R}(f),
$$

which minimises the loss on the observed data.  The ERM framework is the cornerstone of supervised learning; however, $\hat{f}$ is a random variable because it depends on the particular sample drawn.  If we drew another dataset from the same distribution, the ERM could change.

## Relationship between $f_0$, $f^*$ and $\hat{f}$

Three models are commonly compared:

* **Bayes model $f_0$:** minimises population risk across all measurable functions.
* **Best‑in‑class model $f^*$:** minimises population risk within the chosen hypothesis class $\mathcal{F}$.
* **Empirical risk minimiser $\hat{f}$:** minimises empirical risk on a finite sample.

Because $\mathcal{F}$ may not contain $f_0$ and because $\hat{f}$ is trained on finite data, their risks satisfy
$$
R(\hat{f}) \geq R(f^*) \geq R(f_0),
$$
with the gaps corresponding to estimation and approximation errors.  The aim of learning theory is to characterise how these gaps behave as a function of model capacity and sample size.

### Links to other topics

* The decomposition of these risk differences is discussed in [[Approximation vs estimation error decomposition]].
* How foundation models introduce additional error terms is described in [[Foundation models and additional error sources]].
