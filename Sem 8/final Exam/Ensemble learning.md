
**Ensemble Learning** is a ==machine learning technique== where **multiple models** (often called **weak learners**) are **combined** to build a **stronger and more accurate model**.

Instead of relying on a single model (like just one decision tree), ensemble learning combines several models to improve **prediction performance**, **reduce overfitting**, and **increase robustness**.

---

## 🔹 Why Use Ensemble Learning?

- A single model might make errors or be biased.
- Combining many models **averages out errors** and **makes better predictions**.

---

## 🔹 Types of Ensemble Learning

### 1. [[**Bagging (Bootstrap Aggregating)**]]

- Multiple models trained on **different random subsets** of the data. ( sampling technique )
- Final prediction: **majority vote** (classification) or **average** (regression).
- 🔸 **Popular Algorithm**: Random Forest
> 🔹 Goal: Reduce **variance**, handle overfitting.

---

### 2. **Boosting**

- Models are trained **sequentially**, each one focusing on the **mistakes** of the previous one.
- Final prediction: weighted vote or sum.
- 🔸 **Popular Algorithms**: AdaBoost, Gradient Boosting, XGBoost

> 🔹 Goal: Reduce **bias**, build a strong model from weak ones.

---

### 3. **Stacking**

- Combines **different types of models** (e.g., SVM + decision tree + logistic regression).
- A **meta-model** learns to combine their outputs.

> 🔹 Goal: Leverage strengths of **diverse models**.

---

## 🔹 Real-Life Examples

- Used in **Kaggle competitions** to win top prizes.
- Applied in **fraud detection, medical diagnosis, recommendation systems**, etc.
---

## 🔹 Advantages

- Improves **accuracy** and **generalization**.
- Reduces **overfitting**.
- Works well even with **weak models**.

---

## 🔹 Disadvantages

- More **computationally expensive**.
- Harder to **interpret** than single models.
- Can be **slower to train and predict**.

---

## 📌 Simple Analogy:

Think of a **committee** making a decision. One person may be wrong, but when you combine the opinions of many, the final decision is usually more **balanced and accurate**.

---

Would you like a diagram showing the difference between Bagging, Boosting, and Stacking visually?