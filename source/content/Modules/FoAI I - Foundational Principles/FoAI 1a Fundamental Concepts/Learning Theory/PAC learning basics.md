# PAC learning basics

**Probably Approximately Correct (PAC) learning** provides a formal framework for understanding when empirical performance on training data guarantees good performance on unseen data.  Introduced by Valiant, the PAC model quantifies how much data is required to ensure that the learned hypothesis is close to optimal with high probability.

>[!tip] Intuition
>PAC formalizes the intuition behind **estimation error**, turning "how much data is enough" into a mathematical question:
>*"Probably (with high confidence)* $\approx$ *Approximately (with small error) Correct."*

## Informal definition

Given a hypothesis class $\mathcal{F}$, a learning algorithm is **PAC‑learnable** if, for every accuracy parameter $\omega > 0$ and confidence parameter $\varepsilon > 0$, there exists a sample size $n(\omega,\varepsilon)$ such that when we draw $n$ i.i.d. samples from $P(x,y)$, the algorithm produces a hypothesis $\hat{f}$ satisfying

$$
\Pr\big[ R(\hat{f}) - R(f^*) \leq \omega \big] \geq 1 - \varepsilon.
$$

In words: with probability at least $1-\varepsilon$, the true risk of the learned model is within $\omega$ of the best possible risk within $\mathcal{F}$.  The parameters $\omega$ and $\varepsilon$ quantify how close (approximately) and how confident (probably) we need to be.

## Finite hypothesis classes

If $\mathcal{F}$ contains only finitely many functions, PAC guarantees become concrete.  Suppose $|\mathcal{F}| < \infty$.  Then for any $\omega,\varepsilon>0$, with probability at least $1-\varepsilon$,

$$
R(\hat{f}) - R(f^*) \leq \frac{1}{2n}\big( \log |\mathcal{F}| + \log \tfrac{2}{\varepsilon} \big)
$$

where $n$ is the number of samples.  Rearranging shows that to guarantee a risk gap of at most $\omega$ with confidence $1-\varepsilon$ we require

$$
n = O\!\left( \tfrac{1}{\omega^2}\big[ \log|\mathcal{F}| + \log\tfrac{1}{\varepsilon} \big]\right).
$$

This bound highlights two intuitions: a larger hypothesis class needs more data, and demanding higher confidence (smaller $\varepsilon$) requires more samples.

## Infinite classes

Having finitely many parameters does **not** guarantee a finite hypothesis class.  For example, linear models $f_w(x)=w\cdot x$ with $w\in \mathbb{R}^d$ constitute an uncountably infinite class.  Neural networks and polynomial models with real‑valued weights are also infinite classes.  To obtain PAC guarantees in this setting we need other capacity measures such as the VC dimension.

### Links to other topics

* The notion of a hypothesis class and best‑in‑class model is defined in [[Model risk and empirical risk minimisation]].
* For a discussion of the VC dimension and how it yields sample complexity bounds for infinite classes, see [[VC dimension and shattering]].
* The limitations of PAC theory in modern deep learning are addressed in [[Overparameterised models and double descent]] and [[PAC learning vs foundation models]].
