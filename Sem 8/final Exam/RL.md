# module 1 

# 1. What is RL

Reinforcement Learning (RL) is a subfield of **machine learning** that focuses on how an agent can learn to make decisions by interacting with an environment to achieve a goal. It is inspired by behavioral psychology, where learning is driven by rewards and punishments.

### **Key Concepts in Reinforcement Learning**

#### 1. **Agent and Environment**

- **Agent**: The learner or decision-maker (e.g., a robot, software program).
- **Environment**: Everything the agent interacts with to achieve its goal (e.g., a game, a robot's surroundings).

#### 2. **State (s)**

- A state is a snapshot of the environment at a given time.
- Example: In chess, the arrangement of pieces on the board.

#### 3. **Action (a)**

- An action is what the agent can do in a state.
- Example: Move a pawn, move a robot forward.

#### 4. **Policy (π)**

- A policy is a strategy or function that maps states to actions.
- It tells the agent what to do in a particular situation.
#### 5. **Reward (r)**

- A reward is a scalar feedback signal the agent receives after performing an action.
- It guides the learning by telling the agent how good or bad an action was.
- Goal: Maximize cumulative reward over time.

#### 6. **Value Function (V)**

- A value function estimates how good a state is, in terms of expected future rewards.
- Helps the agent evaluate long-term benefits beyond immediate rewards
#### 7. **Q-Function (Action-Value Function, Q(s, a))**

- Measures the expected return of taking an action in a state and following the policy thereafter.
- Helps in comparing different actions.

#### 8. **Exploration vs Exploitation**

- **Exploration**: Trying new actions to discover their rewards.
- **Exploitation**: Using known information to maximize rewards.
- RL balances both for optimal learning

### **Types of Reinforcement Learning**

1. **Model-Free RL**    
    - The agent learns directly from interaction without building a model of the environment.
    - Examples:
        - **Q-Learning**
        - **SARSA (State-Action-Reward-State-Action)**

2. **Model-Based RL**    
    - The agent builds a model of the environment and uses it to plan actions.

3. **Value-Based Methods**    
    - Focus on learning value functions (e.g., Q-learning).

4. **Policy-Based Methods**    (Deterministic and stocastic)
    - Directly learn the policy without value functions (e.g., REINFORCE algorithm).
        
5. **Actor-Critic Methods**
    - Combine value and policy learning using two models: actor (policy) and critic (value).


### **RL Problem Formulation: Markov Decision Process (MDP)**

An MDP is used to mathematically define an RL problem. It consists of:

- **S**: Set of states
- **A**: Set of actions
- **P(s’|s,a)**: State transition probabilities
- **R(s,a)**: Reward function
- **γ (gamma)**: Discount factor (between 0 and 1), defines how much future rewards are worth.

### **Real-World Applications**

- **Robotics**: Teaching robots to walk or pick objects.
- **Games**: AlphaGo, OpenAI Five (Dota 2), Deep Q-Network (Atari games).
- **Self-driving Cars**: Learning to navigate roads and traffic.
- **Finance**: Automated trading strategies.
- **Healthcare**: Personalized treatment plans.

### **Example: RL in a Maze**

1. **Agent**: A mouse in a maze.
2. **State**: Mouse’s position.
3. **Action**: Move up, down, left, right.
4. **Reward**: +10 for reaching the cheese, -1 for hitting a wall.
5. **Goal**: Learn the best path to reach the cheese with maximum reward.

---
# 2. MDP

A **Markov Decision Process (MDP)** is a **mathematical framework** used to describe **decision-making** in environments where outcomes are partly random and partly under the control of an agent. It forms the foundation of **reinforcement learning** problems

### 🔷 Components of an MDP

An MDP is formally defined by a **5-tuple**:



| Symbol | Component              | Description                                                               |
| ------ | ---------------------- | ------------------------------------------------------------------------- |
| S      | States                 | All possible situations the agent can be in.                              |
| A      | Actions                | All possible actions the agent can take.                                  |
| P      | Transition Probability | Probability of moving from one state to another after taking an action.   |
| R      | Reward Function        | Immediate reward received after transitioning from one state to another.  |
| γ      | Discount Factor        | How much future rewards are worth compared to immediate ones (0 ≤ γ < 1). |
![[Pasted image 20250509133808.png]]
### 🔷 Example of MDP: Grid World

Imagine a robot in a 3x3 grid:

- **States (S)**: All 9 positions in the grid.
- **Actions (A)**: Move up, down, left, right.
- **Transition Probabilities (P)**: 80% chance it moves in the intended direction, 20% it slips.
- **Reward (R)**: +10 if it reaches the goal, -1 for hitting a wall.
- **Discount Factor (γ)**: 0.9, so future rewards are slightly less valuable.


![[Pasted image 20250509133843.png]]
### 🔷 Solving an MDP

You can solve an MDP using:
- **Value Iteration**: Iteratively update state values.
- **Policy Iteration**: Iteratively improve the policy.
- **Q-learning, SARSA**: Learn action values from interaction.


---

# Q- learning

**Q-Learning** is one of the most popular **model-free reinforcement learning algorithms**. It allows an agent to learn the **optimal policy** for decision-making **without knowing the model** (i.e., transition probabilities or reward functions).

Q-learning learns a **Q-value** for each **state-action pair (s, a)**, which estimates the **expected cumulative reward** of taking action **a** in state **s**, and following the **best possible strategy** thereafter.


### 🧠 Q-Function
Q(s,a)=Expected return after taking action a in state s

![[Pasted image 20250509162807.png]]

### 📈 Step-by-Step Q-Learning Algorithm

1. **Initialize** Q-values arbitrarily (e.g., all zeros)
2. **For each episode**:
    - Set initial state s
    - Repeat until terminal state:
        1. Choose action aaa using a policy (e.g., **ε-greedy**)
        2. Take action aaa, observe reward rrr and next state s′s's′
        3. Update Q(s, a) using the update rule
        4. Set s←s′
3. **Repeat** until convergence

### ⚖️ Exploration: ε-Greedy Policy
To balance **exploration** and **exploitation**, Q-learning often uses the **ε-greedy strategy**:

- With probability ε: choose a **random** action (explore)
- With probability 1−ε: choose action with **highest Q-value** (exploit)

### ✅ Example: Simple Grid World

- **States**: Positions on a 4x4 grid
- **Actions**: Up, Down, Left, Right
- **Reward**: +10 for reaching the goal
- Q-learning will learn which direction to move in each cell to maximize total reward

### 🔁 Advantages of Q-Learning

- Works in **discrete action and state spaces**
- **Off-policy**: learns the optimal policy independently of the agent’s behavior policy
- No need to know transition probabilities

### ⚠️ Limitations

- Does **not scale well** to large or continuous state spaces
- Needs a table of Q-values for each state-action pair (huge in complex environments)
- Can take a long time to converge

### 🔍 Extensions
- **Deep Q-Learning (DQN)**: Uses a neural network instead of a Q-table to handle large or continuous spaces
- **Double Q-Learning**: Reduces overestimation bias in Q-values

---
# **SARSA (State-Action-Reward-State-Action)**

**SARSA** is a model-free **on-policy** reinforcement learning algorithm that learns the **Q-value function** for a policy **based on the actions it actually takes**. It is closely related to Q-learning, but differs in how it updates the Q-values.

![[Pasted image 20250509180716.png]]
![[Pasted image 20250509180734.png]]
![[Pasted image 20250509180928.png]]

⚖️ Comparison: SARSA vs Q-Learning

| Feature     | **SARSA**                         | **Q-Learning**               |
| ----------- | --------------------------------- | ---------------------------- |
| Policy Type | **On-policy**                     | **Off-policy**               |
| Update uses | Actual next action a′a'           | Max Q-value over all actions |
| Behavior    | Safer, more cautious              | Greedy and optimistic        |
| Stability   | More stable in noisy environments | May learn riskier strategies |

#### 🛣️ Example: Cliff Walking
In environments with dangerous states (e.g., cliff), SARSA learns **safer paths** (avoids risky actions) because it learns from **what the agent actually does**, while Q-learning learns the **best possible path** (which may be risky).

### ✅ When to Use SARSA
- When you want the policy to reflect **actual behavior** (on-policy).
- When **exploration** behavior needs to be accounted for in learning.
- When the environment is **stochastic or dangerous**, and safer behavior is preferred.

---

# 🤖 **Deep Q-Network (DQN**)

A **Deep Q-Network (DQN)** is a reinforcement learning algorithm that combines **Q-learning** with **deep neural networks** to handle **large or continuous state spaces**, where traditional Q-tables become infeasible.

### 🔷 Motivation for DQN
In classic Q-learning, you store and update a **Q-table** for every possible state-action pair. But in real-world problems like video games or robotics:
- State space is **huge or continuous** (e.g., image pixels).
- You can’t store Q-values in a table.
- Solution? **Use a neural network** to approximate the Q-function.

### 🧠 What DQN Does
DQN uses a **deep neural network** to approximate the **Q-function**:

**Q(s,a;θ)≈expected return**

- s: Input state
- a: Action
- θ: Neural network weights
- Output: Predicted Q-value for each action in state sss
### 🛠 Key Components in DQN

| Component           | Purpose                                                         |
| ------------------- | --------------------------------------------------------------- |
| **Q-Network**       | Approximates the action-value function using a neural net       |
| **Target Network**  | Stabilizes learning by using a separate, slowly-updated network |
| **Replay Buffer**   | Stores past experiences to decorrelate training data            |
| **ε-Greedy Policy** | Balances exploration and exploitation during training           |

### 🎮 Example: Playing Atari Games

- **State (s)**: Raw pixels of the game screen
- **Actions (a)**: Joystick movements (e.g., up, down, fire)
- **Reward (r)**: Game score
- DQN learns to play games like **Breakout** and **Pong** directly from screen inputs!

### ⚠️ Limitations & Solutions

|Challenge|Solution|
|---|---|
|Instability during training|Use **target network**|
|Correlated data samples|Use **experience replay**|
|Overestimation bias|Use **Double DQN**|
|Partial observability|Use **Recurrent DQN (RNNs)**|

---

# N-Armed Bandit Problem

The **n-armed bandit problem** is a classic **reinforcement learning (RL)** problem that illustrates the **exploration vs. exploitation trade-off**. It is named after a row of "one-armed bandits" (slot machines), where the agent (learner) chooses one machine at a time to play, aiming to maximize the total reward over time.

### **Problem Statement**

- You are given **n slot machines (arms)**.
- Each arm provides a **random reward** from a fixed, unknown probability distribution.
- At each time step ttt, the agent selects one of the n arms at ∈ {1,2,...,n}.
- The goal is to **maximize the total reward** received over a sequence of plays.

![[Pasted image 20250510172647.png]]


### **4. Key Concepts**

#### a. **Exploration vs Exploitation**

- **Exploration**: Trying out different arms to learn their rewards.
- **Exploitation**: Choosing the arm that has given the highest reward so far.
#### b. **Action-Value Function**

- Denoted as Qt(a)Q_t(a)Qt​(a): estimated value of action aaa at time ttt.
- Updated using:

Qt+1​(a)=Qt​(a)+α(Rt​−Qt​(a))

    where α\alphaα is the learning rate.


### **5. Algorithms to Solve**

#### a. **ε-Greedy Algorithm**

- With probability ε, explore (choose random arm).
    
- With probability 1−ε, exploit (choose best-known arm).

#### b. **Optimistic Initial Values**

- Initialize Q(a) with high values to encourage exploration early on.
#### c. [[UCB (Upper Confidence Bound)]]

- Selects arms based on uncertainty:

![[Pasted image 20250510175808.png]]

where Nt​(a) is the number of times arm a has been chosen.

#### d. **Thompson Sampling**

- Bayesian approach: sample from posterior distribution of each arm’s reward and choose the arm with the highest sample.


### **6. Real-Life Applications**

- Online advertisement selection
- A/B testing in marketing
- Clinical trial designs
- News recommendation systems

### **7. Diagram Ideas**

1. **Simple Bandit Diagram**: n slot machines labeled A, B, C… with arrows showing the agent choosing one.
2. **Exploration vs Exploitation Graph**: A timeline showing different arms being selected.
3. **ε-Greedy Strategy Flowchart**: showing decision process: random vs best-known.

---

# Action-Value Method

The **Action-Value Method** is a core concept in reinforcement learning, used to estimate the **value of different actions** (also called **arms** in the bandit problem) based on the **rewards** they have yielded in the past. It helps the agent decide which action to take next.

### **Purpose**

The goal is to **learn the value Q(a)** of each action aaa to **maximize total rewards** over time. This value represents the **expected reward** of taking action aaa.

### **3. Definitions**

- **Action-value Qt(a)**: The estimated average reward for action aaa at time ttt.
- **True value q∗(a): The actual expected reward of action aaa, which is unknown to the agent.

### **4. Estimating Action-Values**
#### **a. Sample-Average Method**
The value of an action aaa is updated using:

![[Pasted image 20250510195103.png]]

Where:

- n: number of times action aaa has been taken,
- Ri​: reward received on the ithi^{th}ith time.

#### **b. Incremental Update Rule (Efficient Form)**

Qt+1​(a)=Qt​(a)+α(Rt​−Qt​(a))

Where:

- α : learning rate (between 0 and 1),
- Rt​: reward received at time t,
- Qt(a): current estimate.

This method is better for **non-stationary problems** (where reward probabilities change over time).


### **5. How It Works**

1. Initialize all Q(a) to 0 or optimistic values.    
2. At each step:
    - Choose an action using a policy (e.g., greedy, ε-greedy, UCB).
    - Receive reward Rt.
    - Update the action-value estimate using the formula.

### **6. Example**

Suppose an agent has two actions:
- Action A: rewards = 1, 2, 3
- Action B: rewards = 2, 2, 2

Using sample-average method:

- Q(A)=(1+2+3)/3=2Q(A) = (1+2+3)/3 = 2
- Q(B)=(2+2+2)/3=2Q(B) = (2+2+2)/3 = 2

If B gives less variable results, it might be preferred depending on exploration strategy.

### **7. Advantages**

- Simple and effective method for learning value functions.
- Forms the foundation for more complex RL algorithms.
- Works well in both stationary and non-stationary environments (with proper α).

### **8. Diagram Ideas**

1. **Action-Value Table**:
    - Show actions A, B, C with their estimated Q(a)  values and update steps.
2. **Update Flowchart**:
    - Action selected → Reward received → Q(a) updated.
3. **Line Graph**:
    - Time vs. Q(a) estimates showing how values converge.

### **9. Relation to Bandit Algorithms**

- Used in **ε-greedy**, **UCB**, and **Thompson Sampling**.
- Central to updating beliefs about each arm’s quality.

---

# **Optimistic Initial Values in Reinforcement Learning**

The **Optimistic Initial Values** technique is a simple yet powerful method for encouraging **exploration** in **multi-armed bandit problems**. It biases the agent to try all actions early on by **starting with high initial estimates** for action values.

### motivation:

In the standard ε-greedy algorithm, **exploration is random**. However, with **optimistic initial values**, the agent **naturally explores** because the **initial action-value estimates are overly optimistic**, leading the agent to try each action at least once.

### Steps:
- Start with **high initial values** for all Q(a), e.g., 5 or 10.
- The agent chooses actions greedily (selects the action with highest Q(a).
- As actions are tried and actual rewards are received (usually lower than initial estimate), Q(a) gets updated and reduces.
- Untried actions still look “better” because their Q(a) is still high.
- This **drives exploration** without needing randomization (like in ε-greedy).

![[Pasted image 20250510233317.png]]


### **5. Example**

Let’s say:

- 3 arms with true mean rewards: A=1.0, B=1.5, C=2.0
- Initialize all Q(a)=5.0Q(a) = 5.0Q(a)=5.0

Initially, each arm looks equally good (optimistically). After pulling each arm and getting actual lower rewards, the agent reduces the estimated value. But untried arms still appear better and will be selected until explored.


### **Advantages**

- Simple and elegant way to **encourage exploration**.
- **No need for randomness** or tuning ε.
- More **deterministic behavior** than ε-greedy.

### **Limitations**

- Works well in **stationary** environments.
- **Initial value must be chosen carefully**; too high/low affects learning.
- Not ideal for **non-stationary problems** unless combined with adaptive methods.

### **Applications**

- Online learning systems
- Recommendation engines
- Early-stage exploration in RL agents

