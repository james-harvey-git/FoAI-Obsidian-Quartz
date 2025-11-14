# Bias–variance vs approximation–estimation

Machine‑learning researchers often use the terms **bias**, **variance**, **approximation error** and **estimation error** interchangeably, yet they refer to different notions.  Classical learning theory provides a clear vocabulary:

* **Population risk.**  The expected loss of a model $f$ with respect to the true data generating distribution $P(x,y)$.  Formally, $R(f) = \mathbb{E}_{x,y}[\ell(y,f(x))] = \int \ell(y,f(x))\,\mathrm{d}P(x,y)$.  Because we rarely know $P(x,y)$ exactly, the population risk is usually unobservable.
* **Bayes model ($f_0$).**  The (possibly non‑unique) function that minimises the population risk among all measurable functions: $f_0 \in \arg\inf_{f\in\mathcal{F}} R(f)$.  It represents the best possible predictor in theory.
* **Best‑in‑class model ($f^*$).**  When we restrict ourselves to a family of models $\mathcal{F}$, the best‑in‑class model is $f^* = \arg\inf_{f\in\mathcal{F}} R(f)$.  If the true Bayes model is not contained in $\mathcal{F}$, $f^*$ will differ from $f_0$.
* **Empirical risk and the ERM solution.**  Given a dataset $D = \{(x_i,y_i)\}_{i=1}^n$ drawn i.i.d. from $P(x,y)$, the empirical risk $\hat{R}(f)$ approximates $R(f)$ by averaging the loss over the samples.  The empirical risk minimiser (ERM) $\hat{f} = \arg\inf_{f\in\mathcal{F}} \hat{R}(f)$ is the model that minimises this empirical risk.

### Bias, variance, approximation and estimation

The distinction between **bias** and **variance** arises when we consider the behaviour of a learning algorithm under repeated sampling: bias measures the systematic deviation of the estimator’s predictions from the true function, while variance measures how much those predictions fluctuate across different samples.  In contrast, **approximation** and **estimation** errors refer to the gap between theoretical models:

* **Approximation error** is the difference between the risks of the best‑in‑class model and the Bayes model, $R(f^*) - R(f_0)$.  It arises because $\mathcal{F}$ may not be expressive enough to represent the true function.
* **Estimation error** is the difference between the risks of the empirical risk minimiser and the best‑in‑class model, $R(\hat{f}) - R(f^*)$.  It captures the effect of finite data: with more samples the ERM would converge to $f^*$.
* **Excess risk** is $R(\hat{f}) - R(f_0)$ and decomposes into approximation + estimation error.

These definitions clarify that **bias–variance** and **approximation–estimation** operate at different levels.  Bias and variance concern the sampling distribution of an estimator, whereas approximation and estimation errors compare idealised models.  Throughout these notes we will focus on approximation–estimation because it provides a precise way to quantify modelling and data limitations.

### Links to other topics

* For formal definitions of population risk, Bayes model, best‑in‑class model and empirical risk, see [[Model risk and empirical risk minimisation]].
* The decomposition into approximation and estimation error is explored in [[Approximation vs estimation error decomposition]].
* For further insight into the difference between the approximation/estimation and bias-variance decompositions see [[brownBiasVarianceNot]].
