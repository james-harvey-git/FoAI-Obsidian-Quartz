Variational inference is a technique borrowed from physics in which an unknown/intractable posterior distribution is approximated by a simpler distribution characterised by a **variational parameter**. This is then optimised to reduce the KL divergence between the true posterior and variational posterior.
## Variational Inference Procedure
The procedure for variational inference is as follows:
- Find the probability distribution $q_{\phi_{i}}(Z|X_{i})$, characterised by the variational parameter $\phi_{i}$, that is **close** to the true posterior $p_{\theta}(Z|X_{i})$ in the distribution space.
- Closeness between two distributions $P,Q$ with probability density functions $p(x),q(z)$, respectively, can be measured via the KL-divergence $$
\text{KL}(P\lvert  \rvert Q)=\int \log \left( \frac{p(x)}{q(x)} \right)p(x)dx
$$
- The distribution $q_{\phi_{i}^*}(Z|X_{i})$, where $$
\phi_{i}^*= \arg\min_{\phi_{i}}\text{KL}(q_{\phi_{i}}(Z|X_{i})\lvert  \rvert p_{\theta}(Z|X_{i}) )$$
  is a variational approximation of the true $p_{\theta}(Z|X_{i})$.

## Evidence Lower Bound (ELBO)
In the following, the way variational inference links the posterior approximation to the marginal likelihood $p_{\theta}(\mathbf{X})=\prod_{i=1}^{N}p_{\theta}(X_{i})$ is shown.

First rearrange the VI objective (the KL divergence): $$
\begin{align}
\text{KL}(q_{\phi_{i}}(Z|X_{i})\lvert  \rvert p_{\theta}(Z|X_{i}) ) &= \mathbb{E}_{q_{\phi_{i}}}[\log q_{\phi_{i}}(Z|X_{i})-\log p_{\theta}(Z|X_{i})] \\
&= \mathbb{E}_{q_{\phi_{i}}}[\log q_{\phi_{i}}(Z|X_{i})-\log p_{\theta}(Z, X_{i})+\log p_{\theta}(X_{i})] \\
&= \log p_{\theta}(X_{i})-\underbrace{ \mathbb{E}_{q_{\phi_{i}}}[\log p_{\theta}(Z,X_{i})-\log q_{\phi_{i}(Z|X_{i})}] }_{\text{A lower bound of} \log p_{\theta}(X_{i}) }
\end{align}$$
Since the KL divergence is a strictly positive quantity for two *different* distributions, we see that the log (marginal) likelihood (i.e. evidence) $\log p_{\theta}(X_{i})$ of $X_{i}$ is lower bounded by the Evidence Lower Bound (ELBO): $$
\begin{align}
\mathcal{L}(\theta,\phi_{i};X_{i})&=\mathbb{E}_{q_{\phi_{i}}}[\log p_{\theta}(Z,X_{i})-\log q_{\phi_{i}}(Z|X_{i})] \\
&= \mathbb{E}_{{q_{\phi_{i}}}}[\log p_{\theta}(X_{i}|Z)-\text{KL}(\log q_{\phi_{i}}\lvert  \rvert p(Z))] \\
\end{align}$$
