[//]: # (Image References)

[image1]: images/ddpg-algorithm.JPG "A2C DDPG"
[image2]: images/ddpg-algorithm-intuition.JPG "A2C DDPG INTUITIVE"
[image3]: images/score.JPG "plot of rewards per episode"
[image4]: images/score1.JPG "plot 1 of rewards per episode"
[image5]: images/plot.JPG "plot"


## Deep Reinforcement Learning Continuous Control Project Submission Report

### Overview

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Learning Algorithm

#### Advantage Actor-Critic (A2C): Deep Deterministic Policy Gradient, Continuous Action-space (DDPG)

![A2C DDPG][image1]

Two Deep Neural Networks, on the left hand side, the "actor" DNN on the right hand side the "critic" DNN.
The "actor" DNN's output is a approximate maximiser which is passed to the "critic" DNN's output to calculate a new target value for training the action value function ("much in the way DQN does").

![A2C DDPG INTUITIVE][image2]

DDPG Paper:
[click here](https://arxiv.org/abs/1509.02971)

More about A3C Q-Prop:
[click here](https://arxiv.org/abs/1611.02247)

#### Hyperparameters used:

##### For ddpg function:
n_episodes (int): maximum number of training episodes = 100<br />
max_t (int): maximum number of timesteps per episode = 1000<br />

##### For ddpg Agent:
BUFFER_SIZE (int): replay buffer size = int(1e6)<br />
BATCH_SIZE (int): minibatch size = 128<br />
GAMMA (float): discount factor = 0.999<br />
TAU (int): for soft update of target parameters = 1e-3<br />
LR_ACTOR (int): learning rate of the actor = 1e-4<br />
LR_CRITIC (int): learning rate of the critic = 1e-4<br />
WEIGHT_DECAY (float): L2 weight decay = 0<br />

#### Actor (Policy) Model.
fcs1_units (int): Number of nodes in the first hidden layer = 400<br />
fc2_units (int): Number of nodes in the second hidden layer = 300<br />

#### Critic (Value) Model.
fcs1_units (int): Number of nodes in the first hidden layer = 400<br />
fc2_units (int): Number of nodes in the second hidden layer = 300<br />

### Plot of Rewards

![plot of rewards per episode][image3]
![plot 1 of rewards per episode][image4]
![plot][image5]

### Ideas for Future Work

#### 1. Amend the various hyperparameters
Amend the various hyperparameters and network architecture to see if you can get your agent to solve the environment faster.

#### 1.1 Automate hyperparameter variations
You could use for example a genetic algorithm to find out what hyperparameters result in desired improvements.

#### 2. Implementing different learning algorithm
You may like to implement [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf) (implemented), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience.
