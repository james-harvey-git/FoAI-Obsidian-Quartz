## Key Definitions
#### $\sigma$-Algebra
>[!note] Definition: $\mathbf{\sigma}$**-Algebra**
> A $\mathbf{\sigma}$**-algebra** $\mathcal{F}$ on a sample space $\Omega$ is a collection of subsets of $\Omega$ such that:
> 1. $\Omega \in \mathcal{F}$ (entire sample space is an event)
> 2. If $A \in \mathcal{F}$, then $A^c \in \mathcal{F}$ (closed under complements)
> 3. If $A_1, \ A_2, \ A_3, \ ... \in \mathcal{F}$, then $\bigcup_{i=1}^{\infty} A_i \in \mathcal{F}$ (closed under countable unions)

>[!tip] Intuition
>$\mathcal{F}$ represents all events that are knowable or observable.
>Each $A \in \mathcal{F}$ corresponds to a "question" we can ask about the random world.

>[!example] Example: Coin Flips
> Let $X_t =$ result of the $t$-th flip, and $\mathcal{F}_t = \sigma(X_1,...,X_t)$.
> Then $\mathcal{F}_t$ contains all events determined by the first t outcomes.
#### Filtrations: Information Over Time

>[!note] Definition: Filtration
>A **filtration** $(\mathcal{F}_t)_{t\ge 0}$ is an **increasing family of** $\mathbf{\sigma}$**-algebras:** $$\mathcal{F}_0 \subseteq \mathcal{F}_1 \subseteq \mathcal{F}_2 \subseteq \cdots$$
>Meaning as time passes we only gain information: $$\text{More data} \implies \text{more events become measurable}$$

>[!tip] Intuition
>$\mathcal{F}_t$ encodes "everything known up to time t." A filtration represents the process of knowledge accumulation.

#### Adapted Processes
>[!note] Definition: Adapted Processes
>A stochastic process $(X_t)$ is **adapted** to a filtration $(\mathcal{F}_t)$ if $X_t$ is $\mathcal{F}_t$-measurable for all $t$.

>[!tip] Intuition
> - Being adapted means the process respects a causal flow of information.
> - $X_t$ depends only on information available up to time $t$ - not on the future.

#### The Martingale Property

>[!note] Definition: Martingale
>A process ($X_t$) is a **martingale** with respect to the filtration $(\mathcal{F}_t)$ if $$\mathbb{E}[X_{t+1}\mid \mathcal{F}_t] = X_t, \ \ \mathbb{E}[|X_t|] < \infty$$
>*Note: A martingale is defined with respect to a filtration but the condition at each step uses the $\sigma$-algebra $\mathcal{F}_t$ for the corresponding time step in the filtration.*

>[!tip] Intuition
>- Given all current information, your expected future value is the same as the present value.
>- Martingales model a "fair game" - there is no predictable gain over time.

>[!example]- Symmetric random walk
>Let $(X_t)$ be defined as $$X_t = X_{t-1} + Z_t$$ 
>where:
>- $Z_t$ are i.i.d. random variables taking values +1 or -1 each with probability 1/2;
>- $X_0 = 0$
>Let the filtration be on the $\sigma$-algebra $\mathcal{F_t}=\sigma(Z_1, Z_2,...,Z_t), i.e. all the information up to time $t$. Then we have $$\mathbb{E}[X_{t+1}\mid \mathcal{F}_t] = \mathbb{E}[X_t + Z_{t+1}\mid \mathcal{F}_t] = X_t + \underbrace{\mathbb{E}[Z_{t+1}\mid \mathcal{F}_t]}_{= 0} = X_t$$
>And thus $(X_t)$ is martingale. We see that there is no expected gain on the random walk $X_t$ given all current information (the history of tosses).

#### Doob Martingale
>[!note] Definition: Doob Martingale
>For any integrable random variable $X$ and filtration $(\mathcal{F}_t)$: $$M_t = \mathbb{E}[X \mid \mathcal{F}_t]$$
>defines the **Doob martingale**.

Showing that this satisfies the martingale property utilises the Tower Property (Law of Iterated Conditional Expectations): $$\mathbb{E}[M_{t+1}\mid \mathcal{F}_t] = \underbrace{\mathbb{E}[\mathbb{E}[X\mid \mathcal{F}_{t+1}]\mid \mathcal{F}_t] = \mathbb{E}[X\mid \mathcal{F}_t]}_{\text{Tower Property}} = M_t$$
Thus we see that the **the next step conditional expectation (*given no new information*) is the same as the current conditional expectation.**
>[!tip] Intuition
>- Imagine trying to predict a final outcome $X$ (e.g. tomorrow's stock price or total rainfall) as you receive information over time
>- Each $M_t = \mathbb{E}[X \mid \mathcal{F}_t]$ is your best guess given what you currently know.
>- The Doob martingale says that, although your estimates change as new data arrives, they do so fairly - *there is no tendency to systematically over- or under-estimate the final outcome*.
>- In the absence of new information, things stay the same.
>- Upon receiving new information, our filtration grows from $(\mathcal{F}_t)$ to $(\mathcal{F}_{t+1})$ and our best guess becomes $M_{t+1} = \mathbb{E}[X \mid \mathcal{F}_{t+1}]$
>- The martingale property ensures that *before you see that new information* your expected update is neutral: $$\mathbb{E}[M_{t+1}-M_t \mid \mathcal{F}_t] = 0$$

#### Conditionally i.i.d.
>[!note] Definition: Conditionally i.i.d.
>A set of random variables is said to be **conditionally i.i.d.** if there exists a suitable **shared** parameter(s) $\theta$ s.t. the joint distribution becomes conditionally i.i.d.: $$p(X_1=x_1,\dots,X_n=x_n|\theta)=p(X_1=x_1|\theta)\dots p(X_n=x_n|\theta$$

>[!tip] Intuition
>The data $X$ is **conditionally** i.i.d. **given** parameter $\theta$ so historical information can feed into predicting the future: $$p(X_{n+1},\theta|X_1=x_1,\dots,X_n=x+n)=p(X_{n+1}|\theta)p(\theta|X_1=x_1,\dots,X_n=x_n)$$

#### Exchangability
>[!note] Definition: Exchangeability
>If a sequence of random variables is **exchangeable** then there is no information in their order, i.e. $$p(X_1=x_1,X_2=x_2,\dots,X_n=x_n)=p(X_{\pi(1)}=x_1,X_{\pi(2)}=x_2,\dots,X_{\pi(n)}=x_n)$$
>where $\pi$ denotes a permutation operation.
>
>Note: exchangeability is a *weaker* assumption than independence, but crucially exchangeability assumptions apply to many real world problems.
## Doob's Consistency Theorem
### Posterior Probabilities as a Martingale
Let $\Theta$ be a parameter with prior $\Pi_0$, and let $$\mathcal{F}_t = \sigma(X_1, ..., X_t)$$
represent the information from the first $t$ data points.
>[!note]- $\Theta$ as a random variable and as a parameter space
>Note that $\Theta$ can mean two different things depending on the context:
>1. A random variable
>2. A parameter space for the random variable which contains all possible values that the random variable can take

#### Posterior probability as conditional expectation
For any measurable set $A \subseteq \Theta$: $$M_t = \mathbb{E}[\mathbf{1}_{\Theta \in A}\mid \mathcal{F}_t] = \Pi_t(A) = P(\Theta \in A|X_1,...,X_t)$$
<details>
<summary>Note</summary>
(See [[Indicator Random Variable]] for an explanation on indicator random variables as used above.)
</details>
The above tells us how to represent the **posterior** $\Pi_t$ after observing the first $t$ data points as an expectation conditional on information $\mathcal{F}_t$.

Note that we must have $\mathbf{1}_{\Theta \in A} \in \{0, \ 1\}$ (see [[Indicator Random Variable]]), which implies $0\leq M_t = \Pi_t(A)\leq1$ as the expectation must remain between 0 and 1. Additionally, the martingale property tells us that $\mathbb{E}[M_{t+1}\mid \mathcal{F}_t] = M_t$ i.e. the conditional expectation has no systematic drift. Hence, $(\Pi_t(A))_{t\geq 0}$ is a **bounded martingale**.

### (1) Martingale Convergence
#### Doob's Martingale Convergence Theorem
>[!theorem] Theorem: Doob's Martingale Convergence Theorem
>If $(M_t)$ is a bounded martingale, then $$M_t \rightarrow M_\infty \text{ almost surely as } t \rightarrow \infty$$

#### Application to posterior probabilities
For every $A \subseteq \Theta$, $$\Pi_t(A) = \mathbb{E}[\mathbf{1}_{\Theta \in A} \mid \mathcal{F}_t] \implies \Pi_t(A) \rightarrow \Pi_\infty(A) \ \text{a.s.}$$ 
Thus each posterior probability converges almost surely.
As $t$ increases, $\mathcal{F}_t$ grows, so your conditional expectation "stabilises" - *you have learned all there is to learn about $X$ from the filtration.*

### (2) Identifying the limit
Assume data come from the **true** parameter $\theta_0$ i.e. $$X_i \sim P_{\theta_0} \ \text{i.i.d.}$$
Note that this assumption is core to the frequentist framework: there is a ground truth distribution with fixed parameters and randomness comes from the sampling of the data. See [[Frequentist Vs Bayesian]] for more on this.
#### Likelihood behaviour
>[!note]- Notation
>$p_\theta(X_1, \dots,X_n) = p(X_1,\dots,X_n \mid \theta)=\prod_{i=1}^n p(X_i\mid \theta)$ is the same as the likelihood.

For any $\theta \neq \theta_0$, $$\frac{p_{\theta}(X_1,...,X_n)}{p_{\theta_0}(X_1,...,X_n)} \rightarrow 0 \ \text{a.s. under} \ P_{\theta_0} \ \text{as} \ n\rightarrow \infty$$
>[!note]- Derivation
>First take the log of the ratio of the likelihoods: $$\frac{1}{n}\log{\frac{p_\theta(X_1,\dots,X_n)}{p_{\theta_0}(X_1,\dots,X_n)}}=\frac{1}{n}\sum_{i=1}^n\log{\frac{p_\theta(X_i)}{p_{\theta_0}(X_i)}}$$
>By [[The Law of Large Numbers]], as $n\rightarrow\infty$: $$\frac{1}{n}\sum_{i=1}^n\log{\frac{p_\theta(X_i)}{p_{\theta_0}(X_i)}} \rightarrow \mathbb{E}_{P_{\theta_0}}[\log{\frac{p_\theta(X_i)}{p_{\theta_0}(X_i)}}] = -\text{KL}(P_{\theta_0}\lVert P_\theta)$$
>where KL is the Kullback-Leibler divergence, which is strictly positive if $\theta \neq \theta_0$. Exponentiating we have $$\frac{p_\theta(X_1,\dots,X_n)}{p_{\theta_0}(X_1,\dots,X_n)} = \exp{\left(\sum_{i=1}^n\log{\frac{p_\theta(X_i)}{p_{\theta_0}(X_i)}} \right)} \rightarrow \exp(-n\text{KL}(P_{\theta_0}\lVert P_\theta))$$
>and hence, as the KL divergence is strictly positive, this quantity must vanish as $n\rightarrow\infty$.

#### Posterior Collapse
Hence: 
$$ 
\Pi_t(A) \to 

\begin{cases}

1, & \text{if } \theta_0 \in A, \\

0, & \text{if } \theta_0 \notin A,

\end{cases}

\quad P_{\theta_0} \text{-a.s.}
$$
and thus the limiting random measure is $\Pi_\infty = \delta_{\theta_0}$.

In other words, uncertainty about the parameter $\theta$ as characterised by the posterior vanishes in the limit of large $n$, and our Bayesian framework collapses to the frequentist point approximation. 

### Doob's Consistency Theorem (1949)

Putting (1) and (2) together, we arrive at Doob's Consistency Theorem:
- Each posterior probability $\Pi_t(A)$ is a bounded martingale.
- Bounded martingales converge (Doob's martingale convergence theorem).
- Under the true parameter, posterior mass outside neighborhoods of $\theta_0$ vanishes.
- $\implies$ Posterior collapses: $\Pi_t \rightarrow \delta_{\theta_0}$ 

## De Finetti's Representation Theorem
>[!theorem] Theorem: De Finetti's Representation Theorem
>For **any** infinite exchangeable random sequence, it is **always** possible to write: $$p(X_1=x_1,\dots,X_n=x_n)=\int \prod_{i=1}^n p(X_i|\theta)p(\theta)d\theta$$
>as $n\rightarrow \infty$.

>[!tip] Implications for (infinite) exchangeable sequences
>- There is always a parameter $\theta$ which makes $X_1, \dots, X_n$ conditionally independent
>- This parameter must always have a distribution $p(\theta)$ associated with it
>- And there is always a sampling model p(X|\theta)
>- Exchangeable sequences are mixtures of conditionally i.i.d. sequences under the prior measure
>$\implies$ **We should be Bayesian when exchangeability applies!**

>[!warning]- Caveats
>- De Finetti proved for binary exchangeable sequences only
>	- The Generalised Representation Theorem by Hewitt & Savage appeared later
>- Strictly speaking, only applies to *infinite* sequences but Diaconis and Freedman have developed forms/bounds for infinite sequences
>- Things become complex for partial exchangeability and more nuanced dependence structures
>- It is an *existence* theorem only

See [[Latent Variable Models]] for the connection to latent variables.

## Key Insights
>[!key-insight] Key Insights
>- De Finetti shows that if data are exchangeable, a Bayesian model must exist.
>- Doob shows that if we update beliefs through Bayes' rule, they will converge (i.e. posterior will collapse) consistently.
>- Exchangeability is not just a theoretical assumption - it is a practical modelling principle
>$\implies$ It gives us a situation when Bayesian inference *optimally* applies, and guides how to build our models.

## Related Notes
- [[Bayesian Inference]]
- [[Latent Variable Models]]






