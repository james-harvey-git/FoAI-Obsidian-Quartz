As discussed in [[Model Misspecification]], in practical situations systems are typical **M-open world** where we require a more flexible update rule to account for model misspecification. Generalised Bayes achieves this by replacing the likelihood with a loss.

## Bayesian Decision Theory
Statistics can be viewed as a **decision problem** **under uncertainty**:
- Let $\theta$ denote an unknown state of nature and $a$ an action
- Decisions are evaluated by a **loss function** $L(a,\theta)$
- The optimal action minimises **expected loss** (i.e. risk): $$
a^*=\text{arg}\min_{a}\mathbb{E}_{p(\theta|X)}[L(a,\theta)]
$$
- Contrast with classical decision theory where the expectation is wrt to sampling distribution of $X$

>[!key-insight] Key Insight
>For a Bayesian, rational decisions are those that *minimise* **posterior expected loss**.

## Generalised Bayes
Bissiri, Holmes & Walker (2016): updating beliefs **is itself a decision problem**:
- Choose a posterior $q(\theta)$ to minimise: $$
q^*(\theta)=\arg \inf_{q}\mathbb{E}_{q}[L(\theta;X)]+\frac{1}{\eta}\text{KL}(q\lvert  \rvert p)
$$
- Here:
	- $L(\theta;X)$: loss describing the data's informational content (replaces likelihood) - lower loss = higher informational content/support for that parameter value
	- $\text{KL}(q\lvert  \rvert p )$: penalty for deviating from the prior
- Solution is the **Generalised Bayes posterior**: 
$$
\boxed{
q^*(\theta)\propto p(\theta)\exp(-\eta L(\theta;X))}
$$
	Note: Also known as the **Gibbs posterior**.

>[!key-insight] Key Insight
>*Updating = deciding which beliefs to hold, balancing data and prior*

### The Generalised Bayesian Update
The Generalised Bayesian Update, also known as the **Gibbs posterior** is 
$$
\boxed{p(\theta|X)\propto p(\theta)\exp(-\eta L(\theta;X))}
$$
where:
- $p(\theta)$: prior belief
- $L(\theta;X)$: data-dependent loss (note: **not necessarily log-likelihood**)
- $\eta>0$: learning-rate / temperature parameter

This update retains the Bayesian **form**, but broadens what "evidence" means.

*Note: [[Bayesian Inference|Standard Bayes]] is a special case of the Generalised Bayes update:* 
$$
L(\theta;X)=-\log p(X|\theta) \implies p(\theta|X)\propto p(\theta)p(X|\theta)
$$
### Benefits of Generalised Bayes in an M-open world
Generalised Bayes offers a way to:
- Retain **coherent belief updating** without a likelihood
	- Preserves consistency - Doob still applies
	- Still belief updating, just under broader notions of evidence
- Incorporate **model misspecification and robustness**
- Align inference with **predictive or decision objectives**
	- **Bridges with modern approaches in AI**, e.g. gives a framework for what were previously ad-hoc regularisation strategies (see [[Frequentist Vs Bayesian]]).

>[!key-insight] Key Insight
>*Generalised Bayes is Bayesian reasoning for an imperfect world - a world with interventions.*

### Scope of the Generalised Bayes Update
The update 
$$
p(\theta|X)\propto p(\theta)\exp(-\eta L(\theta;X))
$$
is only valid for **parameters that appear in the loss function** $L(\theta;X)$.
If a component $\theta_{j}$ does not appear in $L$: 
$$
p(\theta_{j}|X)=p(\theta_{j})
$$
In other words, coherence requires belief revision only where the loss provides evidence - this prevents spurious updating of uninformed parametes.

>[!key-insight] Key Insight
>*Generalised Bayes is local in scope: only beliefs connected to the loss are revised.*

### Applications of Generalised Bayes
- [[PAC–Bayes theory|PAC-Bayes]] / [[Learning Theory Overview|Learning Theory]]: treat  $L$ as empirical risk (i.e. negative log-likelihood) $\to$ connects to regularised risk minimisation (see [[Frequentist Vs Bayesian]] for more on this)
- **Robust Bayes**: replace log-likelihood with $\beta$-divergence or Huber loss $\to$ down-weight outliers
- **Online learning**: adapt $\eta$ dynamically $\to$ information-theoretic updates
- **Approximate inference**: [[Variational Inference|variational]] or [[Ensemble Learning|ensemble]] updates mimic generalised Bayes behaviour
