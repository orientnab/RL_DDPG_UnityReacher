# RL DDPG UnityReacher
Implementation of a Deep Deterministic Policy Gradient method for solving [Unity Reacher Environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher).
This project is part of [Udacity Deep Reinforcement Learning](https://github.com/udacity/deep-reinforcement-learning/tree/master/p2_continuous-control) Nanodegree.

## Unity Reacher Environment

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

## Solving the Environment
The task is episodic, and in order to solve the environment, the agent must get an average score of +30 over 100 consecutive episodes.

## Getting Started
You can download the environment from one of the links below.
You need only select the environment that matches your operating system.

Option for Linux, Mac and Windows can be found in [Udacity Deep Reinforcement Learning repository](https://github.com/udacity/deep-reinforcement-learning/tree/master/p2_continuous-control#getting-started).

It is also possible to train the agent in AWS. Full instructions in the aforementioned repository.

## Dependencies
You will need in your system:
- Jupyter
- Pytorch
- Numpy
- Some extras such as Matplotlib

## Instructions
Follow the instructions in `Continuous_Control.ipynb` to get started with training the agent.

## Learning Algorithm
The algorithm used is Deep Deterministic Policy Gradient (DDPG).
Most of the code is based on example for solving the [Pendulum Environment](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum), and a full description of the algorithm can be found there.
Some modifications as well as the output plot were taken from the implementation by [blangwallner](https://github.com/blangwallner/Udacity-Deep-Reinforcement-Learning-ND---Project-2---Continuous-Control).
For the choice of hyperparameters we followed [glebashnik](https://github.com/glebashnik/udacity-deeprl-continuous-control/blob/master/Report.md).

| Hyperparameter | Value |
|---|---:|
| Replay buffer size | 1e6 |
| Replay batch size | 128 |
| Actor hidden units | 384, 256 |
| Actor critic units | 384, 256 |
| Actor learning rate | 3e-4 |
| Critic learning rate | 3e-4 |
| Learning timestep interval | 20 |
| Learning passes | 10 |
| Target update mix | 1e-3 |
| Discount factor | 0.99 |
| Ornstein-Uhlenbeck, mu | 0 |
| Ornstein-Uhlenbeck, theta | 0.15 |
| Ornstein-Uhlenbeck, sigma | 0.02 |
| Max episodes | 200 |
| Max steps | 1000 |

## Important Notes
- The Ornstein-Uhlenbeck sigma value must be very low, otherwise the noise is too intense and the model struggles to converge.
- It is also important to keep the learning rates below 1e-3.
- With 256/256 layers, the model would get stuck around 24 points.
- Adding a third layer massively slows down convergence.

## Future Work and Improvements
The problem is very sensitive to the choice of hyperparameters.
It would be ideal to find a more systematic way to find their optimal values.

A Prioritized Experience Replay could be implemented to further enhance the performance of the agent.

