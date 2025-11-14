## ChemGymRL
### Summary
ChemGymRL is an open-source, interactive framework designed to serve as a simulated laboratory for applying Reinforcement Learning to chemical discovery. It aims to bridge the gap between digital chemistry and automated robotic laboratories, which are often hindered by a lack of training data.

• **Structure:** The environment consists of a series of interconnected virtual "benches," each modeling a specific chemical process:

    ◦ **Reaction Bench (RxN):** An agent controls temperature, pressure, and reactant amounts to maximize the yield of a target product.

    ◦ **Extraction Bench (ExT):** An agent uses solvents and physical manipulation to separate desired and undesired products from a mixture.

    ◦ **Distillation Bench (DiT):** An agent heats and cools a vessel to separate materials based on their boiling points.

• **Key Insight:** In benchmark tests involving a complex Wurtz reaction, the Proximal Policy Optimization (PPO) algorithm consistently outperformed other standard RL algorithms (A2C, DQN, SAC, TD3). PPO agents were able to match or exceed the performance of rule-based heuristic policies, demonstrating that RL can learn effective strategies for optimizing multi-step chemical synthesis processes in a simulated environment.
### Key insights
- Environment split into three different benches: extraction (ExT), distillation (DiT), and reaction (RxN)
- Individual agents operate at each bench, working towards their own goals
	- Successfully making materials requires the skilled operation of each individual bench as well as using them as a collective
- Vessels contain materials and can move between benches: output of one bench becomes input of another --> models real chemistry lab
	- Vessels track the hidden internal state of their contents
		- Agent observation of this internal state and the methods by which they can do this can be configured by user 
TL;DR: PPO finds optimal path in all benches

