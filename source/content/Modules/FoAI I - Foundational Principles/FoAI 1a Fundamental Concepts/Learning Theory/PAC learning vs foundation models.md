# PAC learning vs foundation models

The classical PAC framework was developed for models trained from scratch on data drawn i.i.d. from a fixed distribution.  **Foundation models** – massive models pretrained on heterogeneous data and then fine‑tuned or prompted – violate many of these assumptions.

## Classical PAC assumptions

Under the PAC framework:

* Data are drawn **i.i.d.** from a fixed distribution $P(x,y)$.
* The hypothesis class $\mathcal{F}$ is fixed and (often) finite or of controlled capacity.
* Training uses **empirical risk minimisation** from scratch.
* The objective during training and deployment is the same.
* Generalisation guarantees are expressed via sample complexity bounds.

## Foundation models break these assumptions

Foundation models violate or modify each assumption:

* **Data source:** pretraining data are drawn from diverse and heterogeneous sources rather than a single distribution.  Fine‑tuning uses a small sample from a different distribution.
* **Hypothesis class:** the effective model class is extremely large (sometimes unbounded) because of the high capacity of pretrained weights.
* **Training regime:** rather than minimising empirical risk from scratch, fine‑tuning or prompting adapts pretrained parameters.
* **Objectives:** the pretraining objective (e.g. next‑token prediction) differs from the downstream task objective; alignment and prompting adjust the model’s behaviour.
* **Generalisation guarantees:** there are no direct PAC‑style guarantees; researchers rely on empirical scaling laws and robustness analysis.

Nevertheless, the **intuitive principles of PAC learning** – balancing model capacity, data and distribution alignment – continue to guide modern learning theory.  Transfer or alignment error replaces the estimation error as the key term affecting performance; see [[Foundation models and additional error sources]] for more discussion.

### Reinterpreting PAC for foundation models

Modern perspectives view pretraining as amortising sample complexity across many tasks and shift capacity control from explicit measures (like VC dimension) to implicit regularisation via optimiser dynamics and architecture.  Estimation error is replaced by **transfer error**, quantified by the divergence between the source (pretraining) and target distributions.  Domain adaptation bounds, such as those of Ben‑David et al., relate the target risk to the source risk plus a measure of distributional divergence.

### Links to other topics

* The additional error term and diagnostic tips are explained in [[Foundation models and additional error sources]].
* The PAC–Bayes framework provides a way to handle stochastic predictors and implicit regularisation; see [[PAC–Bayes theory]].
