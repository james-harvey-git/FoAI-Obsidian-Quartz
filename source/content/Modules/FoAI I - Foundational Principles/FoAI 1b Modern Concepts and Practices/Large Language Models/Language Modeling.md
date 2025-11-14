---
type: concept
module: FoAI I - Foundational Principles
submodule: FoAI 1b Modern Concepts and Practices
topic: Large Language Models
module_tag: foai-i-foundational-principles
submodule_tag: foai-1b-modern-concepts-and-practices
topic_tag: large-language-models
date: 2025-11-05
tags:
  - concept
  - foai-i-foundational-principles
  - foai-1b-modern-concepts-and-practices
  - large-language-models
  - autoregressive-models
---
# Language Modeling
> [!note] Definitions
> - Vocabulary $V$: finite set of tokens (e.g. ASCII characters)
> - $V$: discrete random variable over $V^*$
> - Support of $X$: $\text{supp}(X)\coloneqq V^{*}$ (product space)
> - Autoregressive model: a type of statistical or machine learning model that predicts the current value of a variable based on its **previous values** — that is, the variable _regresses on itself over time_.

Let $x$ be a string and $p(x)$ the probability of observing it, then the goal of language modeling is to approximate $p(x)$ given i.i.d. samples $x^1,...,x^N$. We define our model for next-token prediction as: $$p_{\theta}(y \mid x): V^* \times V^* \rightarrow [0,1]^{|V|}$$where $|V|$ is the dimension of the vocabulary.

> [!tip] Intuition
> In language modeling, we want to sample from some distribution of tokens $p_{\theta}(x)$ and sample from some arbitrary conditional $y \sim p_{\theta}(y|x)$ where $y$ is a completion of x.

> [!example] Example / Application
> [[ttlm_support.pdf#page=6&selection=4,0,4,6|ttlm_support, page 6]]

LLMs are auto-regressive models: they solve the intractability of $p_{\theta}(x)$ and $p_{\theta}(y|x)$ by using Bayes Theorem (chain rule): $$p(x) = p(x_0) \prod_i p(x_i \mid x_0, \ldots, x_{i-1}) = p(x_0) \prod_i[p(x_i \mid x_{<i})]$$For $p(x_0)$, we add a special symbol \<bos> to the vocab, and always start with it --> Don't need to know the marginal since we know $p(x) = 1$ if $x = <\text{bos}>$ and 0 otherwise.

Goal is now to learn $p(x)$ by approximating its conditionals $p(x_i \mid x_{<i})$.

This is achieved by learning a parametric model $p_{\theta}(x)= \prod_i^{\mid x \mid} p_{\theta}(x_i \mid x_{<i})$ where we minimize the loss $$L(x, \theta) = -\log{p_\theta(x)}$$such that for i.i.d. samples we average their losses via $$L(\theta) = -\frac{1}{N}\sum_{n=1}^N \log{p_{\theta}(x^n)}$$
>[!question]- Why autoregressive models?
> - They simplify the joint distribution $p(x,y)$
> - They handle both unconditional generation (sample from $p_{\theta}(x))$ and conditional generation (sample from $p_{\theta}(y \mid x)$
> - The above two points make autoregressive models very flexible and couple with language's flexible data representation to allowed them to both i) scale and ii) solve general diverse problems

>[!warning] Caution
>Modeling language as i.i.d. is problematic, because words are not independent of one another within a sentence.






> [!link] Related
> - [[Introduction to LLMs]]



## 🧮 Key Equations
```math
% Add equations or derivations here
```

## 💡 Insights

## ❓Questions/Gaps
