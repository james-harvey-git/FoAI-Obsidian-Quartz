---
title: "Bias/Variance is not the same as Approximation/Estimation"
authors: ""
year: 
citekey: "brownBiasVarianceNot"
zoteroKey: "8HKTRHFV"
---

## 🧠 Abstract
We study the relation between two classical results: the bias-variance decomposition, and the approximation-estimation decomposition. Both are important conceptual tools in Machine Learning, helping us describe the nature of model fitting. It is commonly stated that they are “closely related”, or “similar in spirit”. However, sometimes it is said they are equivalent. In fact they are different, but have subtle connections cutting across learning theory, classical statistics, and information geometry, that (very surprisingly) have not been previously observed. We present several results for losses expressible as a Bregman divergence: a broad family with a known bias-variance decomposition. Discussion and future directions are presented for more general losses, including the 0/1 classification loss.

## 🏷️ Tags
- (none)

## 📑 Highlights








- losses expressible as a Bregman divergence: (p. 1)







- In contrast to the abstract notion of a “function class” (p. 1)







- risk of real, trained models, in expectation over possible training sets. (p. 1)







- concerns inference of the response/target variable—and not of the parameters, as is more common in classical statistics. (p. 1)







- The empirical risks are the same for any two ERMs (p. 2)<br>💬 f^_erm is not necessarily unique







- approximation error is the additional risk due to using a restricted family F (p. 3)







- This is a systematic quantity, not dependent on any particular data sample. (p. 3)







- estimation error is the additional risk due to our finite training data (p. 3)







- random variable, dependent on the particular data sample. (p. 3)







- keeping data size fixed. (p. 3)







- estimation error will increase, as it becomes harder to find f ∗ in the larger space. (p. 3)







- often intractable to find a global minimum of the training risk (p. 3)







- the choice of learning algorithm, the quality/amount of data, and the capacity of the model family. (p. 3)







- all possible training sets of a fixed size n. (p. 3)







- bias tends to decrease, and variance tends to increase. (p. 3)<br>💬 so main difference between A/E and B/V seems to be that the trade-off is less solid for B/V compared to A/E







- trade-off can be more complex (e.g. with over-parameterized models) and the exact dynamics are an open research issue. (p. 3)







- ri(Y) (p. 3)<br>💬 relative interior because we need the gradient to be well defined at the point where we make our first order taylor approximation







- − φ(q) − ⟨∇φ(q), p − q⟩ (p. 3)<br>💬 This is the first order taylor approximation of phi(p) at q  
  
the whole point of the Bregman divergence is evaluating the difference between a convex function and its first-order linear approximation --> natural extension to loss as p-->y and q-->f







- fφ(x) := arg min  z∈Y  ED  [  Bφ(z, fˆ(x))  ]  = [∇φ]−1 (  ED  [  ∇φ(fˆ(x))  ])  . (p. 4)<br>💬 The intuition behind the Bregman centroid is that it is the model obtained by averaging over all possible trained models within the function class induced by D







- Bias-Variance decompositions do not hold for all losses. The approximation-estimation decomposition, Equation 9, applies for any loss. (p. 4)<br>💬 The bias-variance decomposition which is usually quoted is not well defined for all losses, only those expressible as Bregman divergence







- the excess risk of an ERM, versus the expected risk of an arbitrary trained model. (p. 5)







- The estimation variance measures the random variations of fˆerm around the centroid model. The estimation bias measures the systematic difference between the centroid model and the best-in-family model. (p. 5)







- The approximation error is in fact just one component of the bias, and, the estimation error contributes to both bias and variance. (p. 5)







- ridge regression solution (p. 6)<br>💬 Ordinary least squares with a regularization term lambda*||beta||^2 added to the loss







- Thus, for this special case, bias is equal to the approximation error, and variance is equal to (what remains of) the estimation error. (p. 6)<br>💬 Bias = Approximation error and Variance = Estimation error only for the special case of OLS (linear)  
  
This is because in the case of OLS, we have an analytic loss with a closed form solution (you can find the ERM by just setting the gradient of the loss to zero) and hence every trained model results in a f_erm --> optimization error is zero  
  
Additionally, because the Bregman centroid for OLS is just the mean of the trained models, which is equal to the best in family model $$E_D[\hat{\beta}_0] = \beta_*$$ there is no estimation bias either since the centroid model is always the same as the best in family model.







- the estimation bias Eest(b) = R(  ◦  fφ) − R(f ∗), can take negative values, i.e. (p. 6)







- In this case the geometry of such losses is not well-understood, leaving several open issues. (p. 10)







- centroid model turned out to be a key mathematical object in bridging the decompositions. (p. 10)







- losses expressible as a Bregman divergence: (p. 1)







- In contrast to the abstract notion of a “function class” (p. 1)







- risk of real, trained models, in expectation over possible training sets. (p. 1)







- concerns inference of the response/target variable—and not of the parameters, as is more common in classical statistics. (p. 1)







- The empirical risks are the same for any two ERMs (p. 2)<br>💬 f^_erm is not necessarily unique







- � �� � � �� � � �� � approximation error is the additional risk due to using a restricted family F (p. 3)







- F This is a systematic quantity, not dependent on any particular data sample. (p. 3)







- F estimation error is the additional risk due to our fnite training data (p. 3)







- random variable, dependent on the particular data sample. (p. 3)







- keeping data size fxed. (p. 3)







- |F| estimation error will increase, as it becomes harder to fnd f ∗ in the larger space. (p. 3)







- often intractable to fnd a global minimum of the training risk (p. 3)







- the choice of learning algorithm, the quality/amount of data, and the capacity of the model family. (p. 3)







- all possible training sets of a fxed size n. (p. 3)







- bias tends to decrease, and variance tends to increase. (p. 3)<br>💬 so main difference between A/E and B/V seems to be that the trade-off is less solid for B/V compared to A/E







- trade-of can be more complex (e.g. with over-parameterized models) and the exact dynamics are an open research issue. (p. 3)



## 💭 My Thoughts
- Bias/Variance is a related but distinct concept to Approximation/Estimation error

- Both concepts describe decompositions of a specific type of risk, excess risk for Approximation/Estimation and expected risk for bias/variance

- Approximation/Estimation Decomposition:
	- Excess risk describes the increase in risk incurred by models trained from some function class $\mathcal{F}$ as compared to the Bayes model $y^*$ : $$\underbrace{R(\hat{f}) - R(y^*)}_{\text{excess risk of } \hat{f}} = \underbrace{R(\hat{f}) -R(\hat{f}_{\text{erm}})}_{\text{optimisation error}} + \underbrace{R(\hat{f}_{\text{erm}}) - R(f^*)}_{\text{estimation error}} + \underbrace{R(f^*) - R(y^*)}_{\text{approximation error}}$$
	- Clearly this is quite abstract as we don't necessarily know the Bayes model, but it provides good intuition: 
		- approximation error = measure of model capacity
		- estimation error = measure of how the realization of the class model capacity is limited by finite sample size (measure of overfitting/instability)
		- Optimisation error = measure of how well the training procedure realizes the ERM
	>[!note]
	There is a clear trade-off between approximation error and estimation error: as approximation error decreases (e.g. increasing the size of the function class 
	$\mathcal{F}$), the estimation error will increase --> results in overfitting beyond a certain point

- Bias/Variance Decomposition:
	- Expected risk of a *trained model* $\hat{f}$ refers to the average risk incurred by the model over all possible training sets (e.g. OLS): $$\textbf{expected risk} = \mathbb{E}_{D}\!\left[\mathbb{E}_{xy}\!\left[(y - \hat{f}(x))^2\right]\right]$$
	- The commonly quoted Bias/Variance decomposition for expected risk goes as $$\textbf{expected risk} = \textbf{noise}+\textbf{bias}+\textbf{variance}$$
	  Or in terms of Bregman divergences, 
	  $$\underbrace{

	\mathbb{E}_{D}\!\left[\mathbb{E}_{xy}\!\left[B_{\phi}(y, \hat{f}(x))\right]\right]
	
	}_{\text{expected risk}}
	
	=
	
	\underbrace{
	
	\mathbb{E}_{xy}\!\left[B_{\phi}(y, y^*)\right]
	
	}_{\text{noise}}
	
	+
	
	\underbrace{
	
	\mathbb{E}_{x}\!\left[B_{\phi}(y^*, f_{\phi}^{\circ}(x))\right]
	
	}_{\text{bias}}
	
	+
	
	\underbrace{
	
	\mathbb{E}_{x}\!\left[\mathbb{E}_{D}\!\left[B_{\phi}(f_{\phi}^{\circ}(x), \hat{f}(x))\right]\right]
	
	}_{\text{variance}}$$
	- For squared loss, this becomes 
	 $$\underbrace{

		\mathbb{E}_{D}\!\left[\mathbb{E}_{xy}\!\left[(y - \hat{f}(x))^2\right]\right]
		
		}_{\text{expected risk}}
		
		=
		
		\underbrace{
		
		\mathbb{E}_{xy}\!\left[(y - y^*)^2\right]
		
		}_{\text{noise}}
		
		+
		
		\underbrace{
		
		\mathbb{E}_{x}\!\left[\left(y^* - \mathbb{E}_{D}[\hat{f}(x)]\right)^2\right]
		
		}_{\text{bias}}
		
		+
		
		\underbrace{
		
		\mathbb{E}_{x}\!\left[\mathbb{E}_{D}\!\left[(\hat{f}(x) - \mathbb{E}_{D}[\hat{f}(x)])^2\right]\right]
		
		}_{\text{variance}}$$
	- <u>However</u>, this ==decomposition doesn't hold for all losses==, and the one shown two lines above explicitly only holds for losses which are expressible as Bregman divergences
	- This means the bias-variance trade off isn't as rigid as the approximation-estimation trade off: bias *tends* to decrease and variance *tends* to increase as the size of a model increases but the trade-off can be more complex (e.g. over-parameterized models) --> open research issue
	- Absolute definitions of bias and variance:
	$$
	\begin{aligned}
	\text{Bias} 
	&= \mathbb{E}_{x} \!\left[\, \ell\big(\textbf{y}^{*}(x), \,\bar{f}(x)\big) \,\right], \\
	\text{Variance} 
	&= \mathbb{E}_{x} \!\left[\, \mathbb{E}_{D}\!\left[\, \ell\big(\bar{f}(x), \,\hat{f}_{D}(x)\big) \,\right] \,\right].
	\end{aligned}
	$$
	- Note that bias and variance are actually defined pointwise for a learner's behavior for each input $x$ and thus for expected risk, the expectation over all possible inputs must be taken to measure generalization

- Relationship between Approximation/Estimation & Bias/Variance:
	- For losses expressible as a Bregman divergence, the following decomposition of bias and variance applies: 
	 $$
	\begin{aligned}
	\underbrace{
	\mathbb{E}_x \left[ B_\phi (y^*, \dot{f}_\phi(x)) \right]
	}_{\text{bias}}
	&=
	\underbrace{R(f^*) - R(y^*)}_{\text{approximation error}}
	+
	\underbrace{R(\dot{f}_\phi) - R(f^*)}_{\text{estimation bias}} \\[1.5em]
	\underbrace{
	\mathbb{E}_x \left[ \mathbb{E}_D [ B_\phi (\dot{f}_\phi(x), \hat{f}(x)) ] \right]
	}_{\text{variance}}
	&=
	\underbrace{\mathbb{E}_D [ R(\hat{f}) - R(\hat{f}_{erm}) ]}_{\text{optimisation error}}
	+
	\underbrace{\mathbb{E}_D [ R(\hat{f}_{erm}) - R(\dot{f}_\phi) ]}_{\text{estimation variance}}
	\end{aligned}$$
	- Thus **estimation error is split between both bias and variance** and ==in general bias/variance is not exactly equal to approximation/estimation== 
	- In the case where our loss is ordinary least squares (OLS) then we have the following:
		- Since the loss is analytic with a closed form solution for the ERM (found by setting the gradient of the loss to zero), every trained model $\hat{f}$ results in an ERM $\hat{f}_{erm}$ 
			--> Optimization error is zero
		- The Bregman centroid for the loss is just the mean of the trained models, and as OLS is unbiased this results in the best in family class model $f^*$ with $\mathbb{E}_D[\hat{\beta}_0]=\beta_*$ 
			--> Estimation bias is zero
		- **Hence <u>only</u> for the case of OLS does the Approximation/Estimation and Bias/Variance equivalence hold** 

- Can view the Bregman centroid model as the mean prediction of the learning the procedure

- ==Bias/Variance examines the learner (focuses on the learning algorithm and its stochastic behaviour) whereas Approximation/Estimation focuses on the function space/class and what's achievable within it==

- ![[Pasted image 20251103104315.png]]

- In order to compare excess risk with expected risk and thus derive a relation between approximation/estimation error and bias/variance (the latter of which only makes sense as an averaged quantity), they calculate expected excess risk for a trained model $\hat{f}_D$ averaged over the possible data sets. Note that approximation error is independent of the datasets, and estimation bias is already an averaged quantity over the distribution of datasets through the centroid model. This is why bias is said to be independent of the particular sample used, whereas variance is affected by the sample used. 


## 🔗 Links
- [📄 PDF](PDF)
- [Local file](file:///Users/jamesharvey/Zotero/storage/3BBFS8NQ/Brown%20and%20Ali%20-%20BiasVariance%20is%20not%20the%20same%20as%20ApproximationEstimation.pdf)
- [Open Zotero Item](zotero://select/items/1_8HKTRHFV)