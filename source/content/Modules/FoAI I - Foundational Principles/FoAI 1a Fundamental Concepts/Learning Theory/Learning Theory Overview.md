# Learning Theory (Module 1a)

The **Learning Theory** lecture on 22 October 2025 sets the stage for understanding how and why machine‑learning algorithms generalise from finite data.  Classical learning theory distinguishes between bias/variance and approximation/estimation, introduces population and empirical risk, and provides guarantees on generalisation via PAC learning and VC dimension.  The lecture also shows how modern deep learning challenges these assumptions and introduces PAC–Bayes theory as a bridge between classical and modern viewpoints.

## Contents

The lecture is broken down into several major topics.  Each page in this folder summarises a part of the material and links to related concepts:

| Topic                                                   | Description                                                                                                                                                                                  |
| ------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[Bias–variance vs approximation–estimation]]**       | Defines population risk, Bayes model, best‑in‑class and empirical risk; explains how approximation and estimation errors differ and why the terms “bias” and “variance” are often conflated. |
| **[[Model risk and empirical risk minimisation]]**      | Introduces population risk, the Bayes model, best‑in‑class models and the empirical risk minimisation (ERM) framework.                                                                       |
| **[[Approximation vs estimation error decomposition]]** | Decomposes excess risk into approximation and estimation errors and discusses how they manifest in practice.                                                                                 |
| **[[Foundation models and additional error sources]]**  | Discusses how pre‑trained foundation models change the approximation–estimation picture and introduces transfer/alignment error.                                                             |
| **[[PAC learning basics]]**                             | Explains the idea of probably approximately correct (PAC) learning, gives sample complexity bounds for finite hypothesis classes and introduces infinite classes.                            |
| **[[VC dimension and shattering]]**                     | Defines the Vapnik–Chervonenkis (VC) dimension, explains shattering and provides generalisation bounds based on VC dimension.                                                                |
| **[[Overparameterised models and double descent]]**     | Describes why classical VC theory cannot explain modern deep learning, introduces the double‑descent phenomenon and hints at implicit regularisation.                                        |
| **[[PAC learning vs foundation models]]**               | Compares classical PAC assumptions with the realities of foundation models and discusses how sample complexity is replaced by transfer/alignment considerations.                             |
| **[[PAC–Bayes theory]]**                                | Presents the PAC–Bayes framework, including the PAC–Bayes bound, the KL complexity term and the interpretation in terms of flat minima and implicit regularisation.                          |
| **[[PAC–Bayes limitations and research directions]]**   | Summarises the practical limitations of PAC–Bayes theory and outlines current research directions such as data‑dependent priors and variational posteriors.                                  |

The notes are designed to be self‑contained but are highly interconnected.  Use the links to explore the relationships between concepts and to reinforce your understanding.