Here’s a structured and concise **10-mark answer** on **AdaBoost (Adaptive Boosting)**:

---

### ⚡ **AdaBoost (Adaptive Boosting)**

**AdaBoost** is one of the earliest and most popular **boosting algorithms** in machine learning. It combines multiple **weak learners** (usually decision stumps) into a single strong learner by focusing more on **difficult-to-classify instances**.

---

### 🧠 Key Idea:

Each new model added to the ensemble focuses on correcting the **errors** made by the previous models. Misclassified data points are given **higher weights**, so that subsequent models give them more attention.

---

### 🔁 **Working of AdaBoost**:

1. **Initialize Weights**:
    
    - All training samples are assigned equal weights initially.
        
2. **Train Weak Learner**:
    
    - A weak learner (e.g., decision stump) is trained on the data.
        
3. **Calculate Error**:
    
    - Calculate the model's error on the weighted data.
        
    - Give more weight to misclassified samples.
        
4. **Update Weights**:
    
    - Increase weights for misclassified points, decrease for correct ones.
        
5. **Add Learner to Ensemble**:
    
    - Assign a weight to the learner based on its accuracy.
        
    - Repeat steps 2–5 for a set number of rounds or until performance plateaus.
        
6. **Final Prediction**:
    
    - In **classification**, each model votes based on its accuracy.
        
    - The final prediction is the **weighted majority vote**.
        

---

### 📌 Example:

Suppose we have a dataset for classifying spam emails. AdaBoost will:

- Start by training a decision stump on the data.
    
- Identify emails it misclassifies (e.g., hard-to-spot spam).
    
- Focus more on these emails in the next iteration.
    
- Combine the results of all learners for the final output.
    

---

### ✅ Advantages:

- **Simple** to implement.
    
- Works well with **low-bias, high-variance** models.
    
- Often achieves **high accuracy**.
    

---

### ⚠️ Disadvantages:

- **Sensitive to noisy data** and **outliers**.
    
- Needs **careful tuning** to prevent overfitting.
    

---

### 📊 Applications:

- Text classification (e.g., spam filtering)
    
- Face detection
    
- Fraud detection
    
- Credit scoring
    

---

### 🔚 Conclusion:

AdaBoost is a powerful boosting technique that adaptively focuses on errors to build a strong classifier from weak learners. It is particularly effective when the base learners are simple and slightly better than random guessing.

---

Would you like a visual flowchart or Python implementation example of AdaBoost?