# Overparameterised models and double descent

Classical VC theory predicts that increasing model capacity should increase the risk of overfitting.  Yet modern deep networks often contain **millions or billions of parameters**, have very large VC dimension, and nevertheless generalise well.  One manifestation of this gap between theory and practice is the **double‑descent phenomenon**.

## Why classical VC theory falls short

In the PAC–VC framework, a hypothesis class with finite VC dimension is learnable, and increasing the VC dimension increases the risk of overfitting.  Deep neural networks, however, often have extremely large or effectively infinite VC dimension.  Despite this, they can generalise even when they fit random labels.  This observation shows that VC dimension alone cannot explain the generalisation behaviour of modern models.

## The double‑descent curve

Empirical studies show that the test error as a function of model capacity often follows a **double‑descent** shape: the error decreases as capacity increases up to the *interpolation point* (where training error becomes zero), rises sharply as capacity just exceeds this point and then falls again as capacity grows further.  In the classical regime (left of the interpolation point) increasing capacity reduces approximation error but increases estimation error.  In the modern regime (right of the interpolation point), adding parameters can actually **decrease** test error again.

## Possible explanations

There is no consensus on a single cause of double descent, but several factors have been proposed:

* **Implicit regularisation.**  Optimisation algorithms like gradient descent (and stochastic gradient descent) tend to find flat minima – solutions in parameter space where many nearby weight configurations achieve similar training loss.  Such minima correspond to simpler functions and thus better generalisation.
* **Overparameterisation.**  In very high‑dimensional parameter spaces, many minima exist.  The optimiser may preferentially locate “benign” minima with good generalisation properties.
* **Alignment with data structure.**  Additional parameters beyond the interpolation point can help the model align its behaviour with the underlying data structure rather than memorising noise.

The take‑home message is that generalisation in deep learning is influenced not just by model capacity but by the **implicit biases of the optimisation process** and the structure of the data.

### Links to other topics

* For the capacity measures that underlie classical theory, see [[VC dimension and shattering]].
* Modern theoretical tools that incorporate algorithmic bias, such as PAC–Bayes theory, are introduced in [[PAC–Bayes theory]] and [[PAC–Bayes limitations and research directions]].
