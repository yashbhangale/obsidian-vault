
### 🔹 **Definition:**
**Bagging** is an ensemble learning technique that combines the predictions of multiple models (usually the same type, like decision trees) trained on **different random subsets** of the original data using **bootstrap sampling**. The goal is to improve accuracy and reduce overfitting.


### 🔹 **Key Concepts:**

1. **Bootstrap Sampling:**
    - Random sampling **with replacement**.
    - Each model gets a slightly different training set.
2. **Independent Models:**
    - Multiple models (often called **weak learners**) are trained **in parallel**.
3. **Aggregation:**
    - Final prediction is made by **majority voting** (for classification) or **averaging** (for regression).

---

### 🔹 **Working of Bagging:**

1. Draw **N** random bootstrap samples from the dataset.
2. Train a model on each sample.
3. Combine predictions of all models.

---

### 🔹 **Advantages:**

- Reduces **variance** of predictions.
- Helps prevent **overfitting**.
- Works well with **high-variance models** (e.g., decision trees).

---

### 🔹 **Disadvantages:**

- Doesn't reduce **bias**.
- Can be **computationally expensive**.
- All models are trained independently, which can be **resource-heavy**.

---

### 🔹 **Popular Algorithm using Bagging:**

- **Random Forest**: Uses bagging + random feature selection.

---

### 🔹 **Applications:**

- Credit scoring
- Medical diagnosis
- Fraud detection
- Stock price prediction

---

### 📊 **Diagram Idea:**

A flowchart showing:

1. Dataset → multiple bootstrap samples → multiple models (e.g., tree1, tree2…treeN) → aggregation → final prediction.
