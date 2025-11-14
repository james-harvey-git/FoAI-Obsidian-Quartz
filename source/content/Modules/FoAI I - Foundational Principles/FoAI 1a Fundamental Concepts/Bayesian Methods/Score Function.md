
>[!note] Definition
>$$s(\theta) = \nabla_{\theta}\log{p(X\mid \theta)}$$

- Measures how sensitive the likelihood is to changes in $\theta$
- Tells us the *direction* of steepest ascent of the likelihood
### Connection to Bayes' Rule
Taking the logs of Bayes' Theorem (see [[Bayesian Inference]]): $$\log{p(\theta \mid X)} = \log{p(X \mid \theta)} + \log{p(\theta)} - \log{p(X)}$$
and thus: $$\nabla_{\theta}\log{p(\theta |X)}=\underbrace{\nabla_{\theta}\log{p(X|\theta)}}_{\text{Score Function}}+\nabla_{\theta}\log{p(\theta)}$$
Note that the above equation is completely independent of $p(X)$.
