# VC dimension and shattering

When the hypothesis class $\mathcal{F}$ is infinite, the PAC bound depends on a measure of capacity.  The **Vapnik–Chervonenkis (VC) dimension** provides such a measure for binary classification.

## Definition of VC dimension

The VC dimension of a hypothesis class $\mathcal{F}$, denoted $\mathrm{VC}(\mathcal{F})$, is the largest integer $d$ such that there exists a set of $d$ points $\{x_1,\ldots,x_d\}$ that **$\mathcal{F}$ shatters**.  A class $\mathcal{F}$ *shatters* a set of points if, for every possible labelling of those points with $0$ or $1$, there exists a function in $\mathcal{F}$ that realises that labelling.

Intuitively, the VC dimension measures how many points the class can classify in all possible ways.  A higher VC dimension means the class can represent more complex patterns, but it also increases the risk of overfitting.

## Examples

* **Linear classifiers in 2D.**  Any three non‑collinear points in the plane can be separated by a line in all $2^3=8$ ways, but four points arranged in an XOR pattern cannot.  Therefore the VC dimension of 2D linear classifiers is $3$.
* **Continuous parameter models.**  Despite having finitely many parameters, linear models $f_w(x)=w\cdot x$ with $w\in\mathbb{R}^d$ have infinite cardinality, but their VC dimension is finite (equal to $d+1$).  Neural networks can have large or infinite VC dimension depending on architecture.

## Generalisation bounds via VC dimension

If $\mathcal{F}$ has finite VC dimension $d$, it is PAC‑learnable.  In particular, with probability at least $1-\varepsilon$,

$$
R(\hat{f}) - R(f^*) \leq O\left( \frac{d \log(n/d) + \log(1/\varepsilon)}{n} \right)
$$

The bound reveals that the amount of data needed to generalise grows with the VC dimension.  As the sample size $n$ increases, the generalisation gap $R(\hat{f}) - R(f^*)$ decreases.  However, for small $n$ a high VC dimension leads to large generalisation error.

## Trade‑offs and limitations

The VC dimension offers a worst‑case guarantee: a class with finite VC dimension will generalise, but the bound may be loose.  Moreover, VC dimension does not account for algorithmic or data‑dependent effects, which become crucial in over‑parameterised models.  This motivates modern research into implicit regularisation and the PAC–Bayes framework.

### Links to other topics

* For the formal statement of PAC learning in finite classes, see [[PAC learning basics]].
* The modern phenomena of double descent and implicit regularisation are discussed in [[Overparameterised models and double descent]].
* PAC–Bayes theory, which goes beyond VC dimension, is introduced in [[PAC–Bayes theory]].
