**Reinforcement Learning (RL)** is a type of ==machine learning== where an ==agent learns to make decisions by interacting with an environment==.  
The agent performs actions, observes the results (states and rewards), and aims to learn a policy that maximizes cumulative rewards over time.  
It is based on trial and error, and learning is driven by feedback in the form of rewards or penalties.

### 1. **Value-Based Methods**

- Focus: Find the optimal **value function** (V(s) or Q(s, a)).
- Action is chosen based on maximum value.
- **Example**:
    - **Q-Learning**
    - **SARSA**
---

### 2. **Policy-Based Methods**

- Focus: Directly learn the **policy** (π) that maps states to actions without using value functions.
- Good for **continuous action spaces**.
- **Example**:
    - **REINFORCE Algorithm** (Monte Carlo Policy Gradient)

Types: Deterministic and stocastic

### **Model-Based Methods**

- Agent builds a **model** of the environment (transition probabilities).
- Uses the model to plan actions.
- Good when environment dynamics can be learned.
- **Example**:
    - **Dyna-Q algorithm**

![[Pasted image 20250427191233.png]]
# Bellman equation

The Bellman equation is a fundamental concept in reinforcement learning that ==helps an agent estimate the value of a state or state-action pair, which represents the expected cumulative reward from that state or state-action onwards==. It's used in **algorithms like Q-learning and SARSA** to make informed decisions and maximize rewards.

V(s) = max [R(s,a) + Discount factor (gamma) V(s)]

---
# Q-Learning

**Q-Learning** is a **model-free reinforcement learning algorithm** that teaches an agent **how to act optimally** in a given environment by learning the **action-value function (Q-function)**.
- "Q" stands for **Quality** — how good an action is in a given state.
- Goal: Find the best action at each state to **maximize total reward** ver time.
- It does **not need** the environment’s model (transition probabilities).

- **Off-policy algorithm** → Learns the value of the optimal policy independently of the agent’s actions.
- Updates Q-values using **Bellman Equation**.
- Uses the formula:

![[Pasted image 20250427191832.png]]

Steps:
- Initialize Q-values randomly.
- For each step:
    - Choose an action (exploration or exploitation).
    - Perform the action, observe reward and next state.
    - Update Q-value using the formula.
- Repeat until learning is complete.

"Q-Learning is a model-free, off-policy reinforcement learning algorithm that learns the optimal action-selection policy by updating Q-values based on rewards and future value estimates."

---
# Sarsa

**SARSA** stands for **State-Action-Reward-State-Action**

It is a **model-free reinforcement learning algorithm** that learns the **Q-values** based on the action actually taken by the agent, **following its current policy**.

- It is an **on-policy algorithm** → learns the value of the policy that the agent is actually following.
- Q-value update depends on the **action chosen by the policy**, not necessarily the best action.
![[Pasted image 20250427192015.png]]

![[Pasted image 20250427192028.png]]

"SARSA is an on-policy reinforcement learning algorithm that updates Q-values using the action actually taken by the agent, based on its current policy."

---

# Deep Q learning

**Deep Q-Learning** is an extension of Q-Learning where instead of using a Q-table to store Q-values, we use a **Deep Neural Network** to **approximate** the Q-function.

- Useful when **state space is very large or continuous** (example: video games, self-driving cars).
- Neural network input = **state**, output = **Q-values for all possible actions**.

Why DQL

- In simple Q-Learning, Q-table becomes too huge if states are infinite/continuous.
- Deep Q-Learning solves this by using **function approximation** through a **Deep Neural Network**.

- Store past experiences (state, action, reward, next state) in a memory buffer.
- Sample random batches to train — helps in breaking correlations and stabilizing learning.
-  Maintain a copy of the main network called **target network**.
- Update it slowly to make learning more stable.

__Deep Q-Learning is a reinforcement learning technique that uses a deep neural network to approximate the Q-value function instead of maintaining a Q-table, making it scalable to complex environments___

---

# N bandit problem (decision making problem)

Multi armed bandit problem
an agent has **N different actions** (like N different slot machines), and has to choose actions over time to **maximize the total reward**.

- Each action gives a **random reward** from an unknown distribution.
- Agent must **balance**:
    - **Exploration** (try different actions to learn their rewards)
    - **Exploitation** (choose the best-known action to get high reward)

- No "state" concept here, only actions and rewards.
- Focus is purely on **action selection**.
- Simple form of Reinforcement Learning.

N-Bandit Problem is a decision-making problem where an agent selects among N actions to maximize cumulative reward while balancing exploration and exploitation

---
# action value pair
An action-value pair refers to the expected cumulative reward associated with taking a specific action in a specific state, usually represented as Q(s, a).

---

# Exploration

- Trying **new actions** that the agent has not tried much yet.
- Purpose: **Discover** if there are better rewards available.
- Example: Agar ek naye restaurant mein khana try karta hai to wo exploration hai.

# Exploitation

- Choosing the **best-known action** based on past experience to get maximum reward.
- Purpose: **Use** already learned knowledge to earn high reward.
- Example: Apne favorite restaurant jaake hammesha wahi khana khana (jo best lagta hai).

# balance between both

- **Too much exploration** = Waste of time in trying bad actions.
- **Too much exploitation** = Miss kar sakta hai better actions jo shayad aur zyada reward dete.

Exploration is trying new actions to discover better rewards, while exploitation is choosing the best-known action to maximize reward

---
# MDP

MDP is a mathematical framework to model **decision-making problems** where outcomes are partly **random** and partly **under the control of the agent**.

It has 4 main elements:

- **S** = Set of States
- **A** = Set of Actions
- **P** = Transition Probability (next state chances)
- **R** = Reward function (reward milta hai after action)

Goal: Find a **policy** (mapping from states to actions) to **maximize cumulative reward**.

Markov Decision Process is a formal framework for modeling decision-making where outcomes are random and influenced by the agent’s actions

![[Pasted image 20250427193110.png]]

---
# Monte Carlo Method

Monte Carlo methods in RL estimate value functions by running full episodes and using the average of total rewards to update learning

- Monte Carlo Methods are **learning techniques** based on **random sampling**.    
- In RL, they **estimate value functions** and **learn policies** by running **many episodes** and **averaging the rewards** collected.
- Important: Updates happen **only after an episode is finished** (not after every step).


![[Pasted image 20250427193248.png]]

---

# Dynamic programming

**Dynamic Programming (DP)** is a set of algorithms used in reinforcement learning for solving **Markov Decision Processes (MDPs)** **when we know the complete environment model** that means, we know the transition probabilities and rewards for all actions and states.

DP methods help in **finding the optimal policy** (best actions to take) or **the optimal value function** (how good each state is).

### Key Concepts in DP:

1. **Policy Evaluation**:
    - Calculating how good a given policy is  that is, finding the expected returns (values) for each state if we follow that policy.

2. **Policy Improvement**:
    - Making the policy better by choosing actions that lead to higher value states.

3. **Policy Iteration**:
    - Alternating between **policy evaluation** and **policy improvement** until we find the best (optimal) policy.

4. **Value Iteration**:
    - A faster method that combines policy evaluation and improvement into one step, updating value estimates directly.


**Dynamic Programming solves reinforcement learning problems by using a complete knowledge of the environment, to find the best strategy through planning.**

- DP needs a **known model** (cannot work without it).
- It works by **breaking problems into smaller subproblems** (typical of dynamic programming).
- It is **computationally expensive** if the state space is very large.
- Examples: **Policy Iteration** and **Value Iteration** are classic DP methods.

# Policy evaluation (PREDICTION)

**Policy Evaluation** means **calculating the value function** for a given policy.  

![[Pasted image 20250427211024.png]]

Policy Evaluation finds out how good each state is when following a particular policy, by using the environment model.


[[Detail format]]

---


## 1. **Policy Evaluation**

- **Goal**: Find how good a policy is.
- **Meaning**: For a given fixed policy, calculate the expected return (total reward) from each state.
- **How**: Use the Bellman Expectation Equation to update the value of each state.
- **In Short**: **"Calculate values assuming a fixed policy."**

---

## 2. **Policy Improvement**

- **Goal**: Make the policy better.
- **Meaning**: After evaluating a policy, we improve it by choosing better actions that lead to higher value states.
- **How**: For each state, pick the action that gives the highest expected return.
- **In Short**: **"Update the policy to be greedy with respect to the current value function."**

---

## 3. **Policy Iteration**

- **Goal**: Find the best (optimal) policy.
- **Meaning**: It combines **Policy Evaluation** and **Policy Improvement** repeatedly until the policy stops changing (becomes stable).
- **Steps**:
    1. Evaluate the current policy.
    2. Improve the policy.
    3. Repeat until no change.
- **In Short**: **"Evaluate and improve again and again until the policy becomes optimal."**

---

## 4. **Value Iteration**

- **Goal**: Find the optimal value function and policy faster.
- **Meaning**: It is a shortcut method where we **update values directly** using the Bellman Optimality Equation instead of fully evaluating the policy first.
- **Steps**:
    1. Start with random values.
    2. Update values by maximizing expected rewards.
    3. Derive the policy from the final values.
- **In Short**: **"Update values directly without full policy evaluation, to speed up finding the best policy."**
    

---

## 5. **Generalized Policy Iteration (GPI)**

- **Goal**: Framework for learning and improving policies together.
- **Meaning**:  
    GPI means **policy evaluation and policy improvement happen together, in any flexible way**, not necessarily fully completing one before starting the other.
- **Idea**:
    - Partial evaluation + small improvement = still moves towards optimal policy.
    - Slow updates are okay, as long as overall improvement happens.
- **In Short**: **"Policy evaluation and improvement happen together, in a flexible, general process."**

---

# 🔥 Short One-liner Recap for All:

|Concept|One-liner|
|:--|:--|
|Policy Evaluation|Find how good the current policy is.|
|Policy Improvement|Make the policy better by choosing better actions.|
|Policy Iteration|Alternate evaluation and improvement until the policy becomes best.|
|Value Iteration|Update values directly to find best policy faster.|
|Generalized Policy Iteration (GPI)|Flexible combination of evaluation and improvement happening together.|

---


# Asynchronous Dynamic Programming (ADP) — Short Explanation:

In **Asynchronous Dynamic Programming**, we **do not update all states together** at each step.  
Instead, we **update only some states at a time**, maybe even just one state.

- It is **more flexible** than normal DP.
- It can **use the most recent updated values immediately** for further updates.
- It is **useful when the state space is very large**, because updating all states every time is too slow.
### In simple words:

> **Asynchronous DP updates states one-by-one or in any order, instead of all at once, to save time and speed up learning.**

### Why useful?

- Faster convergence.
- Can prioritize important states.
- Works even if updates are not perfect or are random.


---

# 🔵 Monte Carlo Learning 

> **Monte Carlo methods** learn from **complete episodes**.  
> They wait until an episode finishes, and then use the **total reward** to update the value of each state or action.
> 
> Monte Carlo does **not require knowledge of the environment model**.
> 
> **Key point**: Learning happens **after the full experience** is over.

No bootstrapping (no estimation)

---

# 🔵 Temporal Difference (TD) Learning

> **Temporal Difference learning** updates value estimates **step-by-step**, immediately after each action.
> 
> It combines ideas from **Monte Carlo** (learning from experience) and **Dynamic Programming** (using estimates to update estimates).
> 
> TD does **not wait for the full episode**; it learns during the episode.
> 
> **Key point**: Learning happens **after every step** using the immediate reward and the estimated value of the next state.

Uses bootstrapping (uses estimates)

---

# 🔵 On-Policy (Simple Definition):

> **On-Policy** learning means the agent **learns about the same policy** that it is **currently following**.

SARSA algorithm.
# 🔵 Off-Policy (Simple Definition):

> **Off-Policy** learning means the agent **learns about a different (better) policy**, while **following another policy** to collect experience.

Q-Learning algorithm.