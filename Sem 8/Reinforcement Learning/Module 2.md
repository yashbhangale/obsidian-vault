
### **1. N-Armed Bandit Problem**  [[hinglish]]

#### **Introduction**

The **N-Armed Bandit Problem** is a fundamental problem in **Reinforcement Learning (RL)** and **Decision Theory**. It models a situation where a player (agent) must choose from **N different options (slot machines or bandits)**, each with an unknown probability distribution of rewards. The goal is to **maximize the total reward over multiple plays** while balancing exploration (testing new machines) and exploitation (sticking to the best machine found so far).

#### **2. Problem Statement**

- The agent interacts with **N slot machines**, each providing a reward according to an **unknown probability distribution**.
- The task is to **identify the best machine** that offers the highest expected reward.
- The main challenge is to **balance exploration (trying new machines) and exploitation (playing the best-known machine).**

#### **3. Key Challenge: Exploration vs. Exploitation**

- **Exploration**: Trying different slot machines to gain more knowledge about their rewards.
- **Exploitation**: Choosing the machine that has provided the highest reward so far.
- If the agent **explores too much**, it may waste time on bad choices.
- If it **exploits too early**, it might miss discovering an even better machine.

#### **4. Algorithms to Solve the N-Armed Bandit Problem**

✅ **Epsilon-Greedy Algorithm**

- With probability **ε**, the agent explores (chooses a random machine).
- With probability **(1-ε)**, it exploits (chooses the best machine found so far).
- A small **ε (e.g., 0.1)** ensures some exploration while mostly exploiting good choices.
- Simple but not always the most efficient.

✅ **Upper Confidence Bound (UCB) Algorithm**

- Focuses on exploration based on **uncertainty**.
- The formula:  
    Q(a)+C×ln⁡tN(a)Q(a) + C \times \sqrt{\frac{\ln t}{N(a)}}
    - **Q(a)**: Estimated reward of action a.
    - **t**: Total number of trials.
    - **N(a)**: Number of times action a was selected.
    - **C**: Controls exploration rate.
- Ensures that **less-explored actions** get more chances.

✅ **Thompson Sampling**

- Uses **probability distributions (Bayesian approach)** to balance exploration and exploitation.
- Samples actions based on their **posterior probability** of being the best.
- More efficient in many real-world applications like **online ads and A/B testing**.

#### **5. Real-World Applications**

- **Online Advertising**: Deciding which ad to show users for maximum engagement.
- **A/B Testing**: Determining the best website layout, marketing strategy, or drug trial.
- **Clinical Trials**: Testing different treatments while ensuring fewer patients get ineffective treatments.
- **Game Strategies**: Finding optimal moves in decision-based games.

#### **6. Conclusion**

The **N-Armed Bandit Problem** is a classic **decision-making problem** that helps in optimizing choices under uncertainty. **Balancing exploration and exploitation** is the key challenge, and different algorithms (Epsilon-Greedy, UCB, Thompson Sampling) address it in unique ways. This problem has **wide applications in machine learning, business, healthcare, and beyond**.


---


### **2. Action-Value Methods – Detailed Explanation** [[Hinglish action-value]]

#### **1. Introduction**

The **Action-Value Method** is a fundamental concept in **Reinforcement Learning (RL)** used to estimate the value of different actions in a given environment. It helps an agent determine which action will yield the highest expected reward over time. This method is widely used in problems like the **N-Armed Bandit Problem** and **Markov Decision Processes (MDPs)**.

#### **2. Action-Value Function (Q(a))**

The **action-value function** represents the **expected reward** obtained when taking an action **a** in a given state **s**. It is denoted as:

Q(a) = E[R|A = a]

Where:

- Q(a) is the **estimated value** of taking action **a**.
- R is the **reward** received for taking action **a**.
- E\mathbb{E} represents the **expected value** (average reward over time).

The goal of **action-value methods** is to find the optimal action **a∗a^*** that maximizes Q(a):

a* = arg max Q(a)

#### **3. Estimating Action-Values**

To estimate Q(a)Q(a), we use **sample averages**. If an action aa has been selected **N times**, the action-value estimate is:

![[Pasted image 20250222201440.png]]

Where:

- Qn(a) is the estimated value after **N selections**.
- Ri is the **reward received** on the ith selection.

As N increases, Qn(a) **converges to the true value**.

#### **4. Incremental Update Formula**

Instead of storing all past rewards, we use an **incremental update** to efficiently update Q(a)Q(a):

![[Pasted image 20250222201543.png]]

Where:

- α alpha is the **learning rate** (step size, 0 < α ≤ 1 ).
- Rn is the reward received at step n.

This method is more **memory efficient** than storing all rewards.

#### **5. Action Selection Strategies**

✅ **Greedy Selection**

- Always selects the action with the **highest Q(a)** value.
- **Downside**: May get stuck in a **local optimum** and miss better actions.

✅ **Epsilon-Greedy Selection**

- With probability **ϵ\epsilon**, selects a **random action** (exploration).
- With probability **1 − ϵ**, selects the **best action so far** (exploitation).
- Helps balance **exploration vs. exploitation**.

✅ **Softmax Selection**

- Uses a **probabilistic approach** where actions with higher Q(a)Q(a) values are selected more often but not always.
    
- Action probability is given by the **Boltzmann distribution**:
![[Pasted image 20250222201702.png]]


#### **6. Applications of Action-Value Methods**

- **Reinforcement Learning**: Helps in training AI agents to make optimal decisions.
- **Game AI**: Used in decision-making for AI in games like Chess, Go, and Poker.
- **Robotics**: Helps robots learn optimal movements based on reward feedback.
- **Online Recommendation Systems**: Suggests content based on user interactions.

#### **7. Conclusion**

Action-value methods are essential in **Reinforcement Learning**, providing a way to estimate the **expected reward** for different actions. Using sample averages or incremental updates, an agent can gradually **learn the best actions**. Various selection strategies like **greedy, epsilon-greedy, and softmax** help balance **exploration and exploitation**. These methods are widely used in AI, robotics, and optimization problems.


#### **1️⃣ Sample-Average Methods**

**Concept**:

- This method calculates action values as the **average of all past rewards** received for a particular action.
    
![[Pasted image 20250222204450.png]]

**Working**:

- Whenever an action is selected, its new reward is added to the total sum.
- The new **sample average** is recalculated.

**Pros**:  
✅ Simple and effective when rewards are **stationary** (do not change over time).  
✅ Provides an unbiased estimate of **true action values**.

**Cons**:  
❌ Computationally expensive if many actions are selected because it requires storing all past rewards.  
❌ **Slow learning** when dealing with **non-stationary rewards** (i.e., when the environment changes over time).

---

#### **2️⃣ Incremental Update Methods**

**Concept**:

- Instead of storing and averaging all past rewards, this method uses an **efficient update rule** to adjust the action-value estimate **step by step**.
    
![[Pasted image 20250222204504.png]]
**Working**:  
1️⃣ Start with an initial **Q-value** for an action.  
2️⃣ When the action is selected, receive a new reward **RnR_n**.  
3️⃣ Update **Q-value** using the incremental formula.  
4️⃣ The learning rate α\alpha controls how much influence the new reward has on the estimate.

**Pros**:  
✅ More efficient because it doesn’t require storing all past rewards.  
✅ Works well for **non-stationary** environments if **α\alpha** is set properly (higher α\alpha reacts quickly to changes).

**Cons**:  
❌ Can be biased if **α\alpha** is not tuned correctly.  
❌ Older rewards lose influence as newer rewards dominate.

---

#### **Comparison Table**

| Method                 |     | Storage Requirement       | Best for                   | Weakness                                      |
| ---------------------- | --- | ------------------------- | -------------------------- | --------------------------------------------- |
| **Sample-Average**     |     | Stores all rewards        | **Stationary** rewards     | Slow learning, high memory use                |
| **Incremental Update** |     | Only stores last estimate | **Non-stationary** rewards | Sensitive to α\alpha, biased if misconfigured |

---

#### **Conclusion**

- **Sample-average methods** are great for **stable environments** but require **storing all rewards** and **slow adaptation** to changes.
- **Incremental update methods** are better for **dynamic environments**, as they use a **step-size parameter** for faster learning while keeping memory usage low.
- The choice between these methods depends on whether the environment is **stationary or non-stationary**.

These methods form the foundation for **reinforcement learning algorithms**, including **Q-learning and Deep Q-Networks (DQN)**! 🚀