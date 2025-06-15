# ✅ Solution: Decision Tree – Customer Churn Prediction

## 📌 Lesson Recap

In this exercise, you built and evaluated a **Decision Tree Classifier** to predict **customer churn** using a synthetic dataset for a telecom company.

The model uses:
- `Age`
- `MonthlyCharge`
- `CustomerServiceCalls`

To predict:
- `Churn` (Yes/No)

---

## 🌲 Understanding the Decision Tree Output

When visualizing the decision tree using Scikit-learn, each node in the tree contains several key terms:

### 🔹 Gini
- **Definition**: A measure of impurity or disorder.
- **Range**: 0 (pure) to 0.5 (maximum impurity for binary classification).
- **Goal**: Lower Gini values are preferred—indicating more homogeneity at that node.

### 🔹 Samples
- **Definition**: Total number of data samples that reached that node.
- **Insight**: Indicates how broadly the rule at that node applies.

### 🔹 Value
- **Definition**: Distribution of the target classes.
- **Example**: `[15, 5]` means 15 samples are 'No', 5 are 'Yes'.

### 🔹 Class
- **Definition**: The majority class predicted at that node.
- **Example**: If `Value = [15, 5]`, then `Class = No`.

### 🔹 Feature & Threshold
- **Definition**: The condition used to split the data.
- **Example**: `MonthlyCharge <= 80` means the node splits based on that threshold.

> ✅ These terms help us understand **how** the tree makes decisions and **why** it predicts a certain outcome.

---

## 🔍 Key Concepts in Machine Learning Workflow

### 1. **Splitting the Dataset**
- **Training Set (70%)** – Used to train the model.
- **Testing Set (30%)** – Used to evaluate how well the model generalizes.

### 2. **Training the Model**
- Performed using `model.fit(X_train, y_train)`.

### 3. **Prediction**
- Use `model.predict(X_test)` to generate churn predictions.

### 4. **Accuracy Score**
- Compares predicted vs. actual churn status.
- Example:
  ```python
  from sklearn.metrics import accuracy_score
  accuracy = accuracy_score(y_test, y_pred)
  print(f"Model Accuracy: {accuracy}")
  ```

---

## 🌳 Visualized Decision Tree
Here’s how to visualize the trained model:
  ```python
  from sklearn import tree
  import matplotlib.pyplot as plt
  
  plt.figure(figsize=(12, 8))
  tree.plot_tree(clf, filled=True,
                 feature_names=['Age', 'MonthlyCharge', 'CustomerServiceCalls'],
                 class_names=['No Churn', 'Churn'])
  plt.title('Decision Tree for Predicting Customer Churn')
  plt.show()
  ```

### This visualization: 
- Helps you understand model decisions
- Reveals which features influence churn most

![Graph showing Decision Tree for Predicting Customer Churn](Exercise3.jpeg)  

---

## 🧠 Insights
- Customers with high Monthly Charges and multiple service calls may be more likely to churn.
- Decision trees are interpretable and useful for business stakeholders.
- This model provides a rule-based strategy to identify at-risk customers.

---

## 🔐 Remember:
> ✅ After reviewing your notebook, delete your instance to avoid additional charges or idle usage.


## ✅ Summary
- You trained and tested a DecisionTreeClassifier.
- You visualized and interpreted the decision path.
- You learned how models predict, and how to evaluate and act on those predictions.
