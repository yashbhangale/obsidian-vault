The **Upper Confidence Bound (UCB)** is a powerful strategy to solve the **n-armed bandit problem**. It addresses the **exploration vs. exploitation dilemma** in a principled way by choosing actions based not only on their average rewards but also on the **uncertainty (or confidence)** about those estimates.


### **2. Motivation**

In ε-greedy, exploration is random. But UCB selects actions **systematically**, favoring:

- Actions with **high average reward**, and
- Actions that have been **played less often** (to reduce uncertainty).

![[Pasted image 20250510181211.png]]

Where:

- Qt(a) : Estimated average reward of arm aaa at time ttt.
- Nt(a) : Number of times arm aaa has been selected.
- ln⁡ t : Total number of time steps encourages gradual exploration.
- c: A positive constant controlling **degree of exploration**.


| Term                          | Meaning                                                      |
| ----------------------------- | ------------------------------------------------------------ |
| Qt(a)                         | Exploitation term – current estimate of arm's value.         |
| $\sqrt{\frac{\ln t}{N_t(a)}}$ | Exploration term – becomes smaller as Nt(a)N_t(a) increases. |
| c                             | Controls how much to explore uncertain arms.                 |

![[Pasted image 20250510181416.png]]


### **6. Example**

Imagine 3 arms:

- Arm A: mean reward = 0.5
- Arm B: mean reward = 0.7
- Arm C: unexplored

Even if B has the highest current average, UCB may select C because it hasn’t been tried much and could potentially be better.

### **7. Advantages**

- Balances exploration and exploitation effectively.
- Theoretically proven to have **logarithmic regret** (very efficient).
- Does **not** require tuning ε\varepsilonε like ε-greedy.

### **8. Diagram Ideas**

1. **UCB Formula Breakdown**:  
    Show a bar for each arm with:    
    - average reward (base),
    - exploration bonus (upper bar).

2. **Line Graph**:
    - x-axis: time
    - y-axis: rewards or UCB values for different arms over time.

3. **Flowchart**:    
    - Initialization → UCB calculation → Action selection → Reward update.


### **9. Real-World Applications**

- Online recommendation systems
- News/article selection
- Online advertising (ad click-through optimization)