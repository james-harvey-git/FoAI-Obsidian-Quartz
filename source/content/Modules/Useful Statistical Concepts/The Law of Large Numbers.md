The law of large numbers states that if $X_1, \dots, X_n$ are **i.i.d. random variables** with **finite** expectation $\mathbb{E}_{P_\theta}[X_i]<\infty$, then: $$\frac{1}{n}\sum_{i=1}^n X_i \rightarrow \mathbb{E}_{P_\theta}[X_i] \ \text{a.s. as} \ n \rightarrow \infty$$
Meaning: The **sample mean** converges almost surely (i.e. with probability 1) to the **true mean**.

This extends to any *measurable* function $f(X)$ such that the expectation $\mathbb{E}_{P_\theta}[|f(X)|]<\infty$, we can apply the same reasoning since the random variables $f(X_1),\dots,f(X_n)$ are still i.i.d. and thus: $$\frac{1}{n}\sum_{i=1}^n f(X_i) \rightarrow \mathbb{E}_{P_\theta}[f(X_i)] \ \text{a.s. as} \ n \rightarrow \infty$$
