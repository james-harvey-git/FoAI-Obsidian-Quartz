# Approximation vs estimation error decomposition

Building on the definitions in [[Bias–variance vs approximation–estimation]] and [[Model risk and empirical risk minimisation]], we can dissect the gap between the ERM solution and the optimal predictor into two principal components: **approximation error** and **estimation error**.  This decomposition provides insight into how model capacity and data size affect performance.

## The decomposition

Let $\hat{f}$ denote the empirical risk minimiser, $f^*$ the best‑in‑class model and $f_0$ the Bayes model.  The **excess risk** of $\hat{f}$ relative to the Bayes model is

$$
R(\hat{f}) - R(f_0) = \underbrace{[R(\hat{f}) - R(f^*)]}_{\text{Estimation error}} + \underbrace{[R(f^*) - R(f_0)]}_{\text{Approximation error}}.
$$

This decomposition is illustrated in the slides: the excess risk splits into an **estimation error** term $R(\hat{f}) - R(f^*)$ and an **approximation error** term $R(f^*) - R(f_0)$.  The approximation error reflects how well our hypothesis class can represent the true function; the estimation error reflects how accurately we can estimate the best model from finite data.

## Behaviour as model complexity varies

* **Low‑capacity models (e.g. linear regression):** These models may suffer from large approximation error because they cannot represent complex relationships.  However, with limited parameters they have low estimation error.  For example, in the in‑class exercise the linear model (Model A) has higher approximation error than a neural network (Model B) but lower estimation error.
* **High‑capacity models (e.g. deep networks):** Richer function classes can approximate a broader range of functions, reducing approximation error.  But with finite data the estimation error can increase because the model may overfit.  Nevertheless, in over‑parameterised regimes modern optimisation and regularisation techniques (e.g. implicit regularisation or early stopping) can mitigate estimation error.

## Beyond approximation and estimation: additional error types

For complex models there are other sources of error not captured by the simple decomposition:

* **Optimisation error** arises when the training algorithm fails to find a good minimum of the loss function due to non‑convexity, poor initialisation or limited training time.
* **Model specification error** occurs when the hypothesis class includes non‑admissible or physically implausible functions.  In deep networks this can lead to unrealistic solutions.
* When using foundation models the classical decomposition breaks down completely and a **transfer (alignment) error** must be added – see [[Foundation models and additional error sources]].

Understanding how approximation and estimation errors trade off informs model selection: choosing a model class that balances expressivity with data efficiency is key to good generalisation.

### Links to other topics

* The effects of foundation models on this decomposition are discussed in [[Foundation models and additional error sources]].
* Over‑parameterised models and the resulting double‑descent phenomenon are examined in [[Overparameterised models and double descent]].
