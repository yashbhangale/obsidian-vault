Bhai, Markov Decision Process (MDP) ek ==mathematical framework== hai jo ==decision-making problems ko model karta hai==, jisme ==future state sirf current state aur action pe depend karti hai, past pe nahi.==

![[Pasted image 20250225224136.png]]

#### MDP ke main components:

1. ==**States (S)** – System ki possible conditions ==(e.g., traffic light green, red, ya yellow).
2. ==**Actions (A)** – Jo bhi decisions ya moves le sakte ho== (e.g., rukna, chalna, ya tez bhagna).
3. ==**Transition Probability (P)**== – Kisi state se kisi doosri state pe jaane ki ==probability==, kisi action lene ke baad.
4. ==**Rewards (R)**== – Har action ke baad jo ==reward== ya ==penalty== milti hai.
5. ==**Policy (π==)** – Ek strategy jo batati hai ki kis state pe kaunsa action lena chahiye.

MDP ka main funda yeh hai ki ek **==optimal policy==** dhoondi jaye jo ==long-term reward maximize kare==. Yeh ==reinforcement learning aur AI== me kaafi use hota hai, jisme agent environment ke sath interact karke best policy seekhta hai.

Agar RL ya AI field me jaana hai to MDP samajhna important hai!

Ek simple example lete hain **self-driving car** ka.

#### **MDP ka Breakdown:**

1. **States (S):**
    - Car signal pe hai
    - Road free hai
    - Traffic jam hai
    - Pedestrian cross kar raha hai
2. **Actions (A):**
    - Tez chalana
    - Dheere chalana
    - Rukna
3. **Transition Probability (P):**
    - Agar red signal pe ruk gaye, to green hone ke baad 90% chance hai ki agla state "road free" hoga.
    - Agar bina dekhe tez chale gaye, to 30% chance hai ki "accident" state me chale jaoge.
4. **Rewards (R):**
    - Safe chalane pe +10
    - Accident hone pe -100
    - Signal todne pe -50
5. **Policy (π):**
    - Agar signal red hai → "rukna" best action hai
    - Agar road free hai → "tez chalna" best action hai
    - Agar pedestrian cross kar raha hai → "rukna" best action hai

Self-driving car ka AI ==**optimal policy==** seekhne ke liye MDP use karta hai, ==jisse long-term reward maximize ho aur accident avoid ho.==

Yahi funda gaming, robotics aur finance jaisi fields me bhi apply hota hai!

---

Bhai, **==Value Iteration** aur **Policy Iteration**== dono ==algorithms== **Markov Decision Process (==MDP==)** me best policy find karne ke liye use hote hain. Inka main goal ==__optimal policy== (π_) dhoondhna hai jo ==long-term rewards maximize== kare.

#### **1. Value Iteration Algorithm**

Ye algorithm **==Bellman equation==** use karke har state ki best possible value calculate karti hai aur fir policy derive karti hai.

#### **Steps:**

1. **Initialize** har state ki value V(s) randomly ya zero se.

![[Pasted image 20250225222728.png]]

2. **Repeat** jab tak values converge na ho jaye (change negligible ho).
3. **Extract Policy**: Har state ke liye wo action choose karo jo maximum value de.

🔹 **Use Case:** Jab **fast convergence** chahiye aur values ke basis pe policy nikalni ho.

---

#### **2. Policy Iteration Algorithm**

Ye algorithm ==pehle ek policy assume karti hai, usko evaluate karti hai, aur fir policy ko improve karti hai.==

#### **Steps:**

1. **Initialize** ek random policy π(s).

![[Pasted image 20250225223002.png]]

🔹 **Use Case:** Jab **stable policy** chahiye jo iterative improvements se optimize ho.

---

#### **Value Iteration vs. Policy Iteration**

| Feature           | Value Iteration                                        | Policy Iteration                                         |
| ----------------- | ------------------------------------------------------ | -------------------------------------------------------- |
| Approach          | Values update hoti hain aur fir policy derive hoti hai | Policy update hoti hai aur fir values evaluate hoti hain |
| Convergence Speed | Fast, but more iterations                              | Slow, but stable improvements                            |
| Computation       | Har iteration me full Bellman update                   | Policy evaluation aur improvement ke separate steps      |
| Best for          | Large state spaces                                     | Small to medium state spaces                             |

==Agar **fast result** chahiye to **Value Iteration**, aur agar **stable policy chahiye** to **Policy Iteration** better hai.==

Tujhe kaunsa samajhna hai depth me?