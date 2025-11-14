# Foundation models and additional error sources

The classical approximation–estimation decomposition was developed for models trained from scratch on data drawn i.i.d. from a fixed distribution.  **Foundation models** – large models pretrained on massive and heterogeneous datasets – break these assumptions and introduce new sources of error.

## Characteristics of foundation models

* They are pretrained on **massive and diverse external datasets**, often hundreds of billions of tokens or images.
* Their architectures have **extremely high representational capacity**, giving them low approximation error for a wide range of tasks.
* Fine‑tuning on a small amount of task‑specific data typically results in low estimation error.

However, the pretraining and fine‑tuning distributions need not match.  If the data distribution for the downstream task $P(x,y)$ differs significantly from the pretraining distribution $P_{\text{FM}}(x,y)$, the usual decomposition does not capture all sources of error【935844732720841†L270-L297】.

## Transfer / alignment error

When the target distribution differs from the pretraining distribution, there is a **transfer error** (also called alignment or domain‑shift error).  Formally, the risk of the fine‑tuned foundation model $\hat{f}_{\text{FM}}$ can be written as

$$
R_P(\hat{f}_{\text{FM}}) - R(f_0) = \text{Approximation} + \text{Estimation} + \text{Transfer error}.
$$

This transfer error arises from a mismatch between pretraining and target task distributions and can produce outputs that are **plausible but systematically incorrect**.  Foundation models perform well when this term is small; when it is large, **alignment** (e.g. via reinforcement learning from human feedback) becomes a key challenge.

## Diagnosing error types

The slides suggest practical ways to distinguish error sources based on how performance changes with more data or different inputs:

| Error type | Indicator |
|---|---|
| Approximation | Performance **fails even with lots of data**. |
| Estimation | Performance **improves with more labelled data**. |
| Transfer / alignment | Performance **fails despite low training error**; try probing with out‑of‑distribution inputs or contradictory prompts. |

Regression models with good feature extractors sometimes compete surprisingly well with large pretrained models on small tasks, underscoring the importance of assessing approximation and estimation before defaulting to complex foundation models.

### Links to other topics

* The basic approximation–estimation decomposition is presented in [[Approximation vs estimation error decomposition]].
* For a formal comparison of classical PAC assumptions with those underlying foundation models, see [[PAC learning vs foundation models]].
