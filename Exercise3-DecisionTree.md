# 🌳 Exercise: Decision Tree – Predicting Customer Churn

## 🧠 Scenario

You are a **data analyst at a telecom company**. The marketing department has noticed a **rise in customer churn** and needs your help to predict which customers are most likely to leave next month.

Customer churn = when a customer stops doing business with a company.  
Predicting churn helps businesses proactively retain customers.

---

## 📋 Dataset Description

We are using a **synthetic dataset** with the following columns:

| Column | Description |
|--------|-------------|
| `CustomerID` | Unique ID for each customer |
| `Age` | Customer age |
| `MonthlyCharge` | Monthly bill amount |
| `CustomerServiceCalls` | Number of customer service interactions |
| `Churn` | Target variable (`Yes` or `No`) |

---

## 🔧 Step-by-Step Instructions

### ✅ 1. Setup the Environment
Import required libraries:
- `pandas` for data handling
- `scikit-learn` for ML modeling
- `matplotlib` for visualization

### ✅ 2. Create the Dataset
Use synthetic values to simulate real-world telecom data.

### ✅ 3. Data Preparation
- Split data into features (`X`) and target (`y`)
- Use `train_test_split` for training/testing separation

### ✅ 4. Build the Decision Tree Model
- Use `DecisionTreeClassifier` from Scikit-learn
- Train the model with the training data

### ✅ 5. Evaluate the Model
- Predict using test data
- Calculate **accuracy**

### ✅ 6. Visualize the Decision Tree
- Plot the decision tree using `plot_tree`

---

## 💻 Python Code Implementation

```python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
from sklearn import tree

warnings.filterwarnings('ignore')

# Creating a synthetic dataset
data = {
    'CustomerID': range(1, 101),
    'Age': [20, 25, 30, 35, 40, 45, 50, 55, 60, 65]*10,
    'MonthlyCharge': [50, 60, 70, 80, 90, 100, 110, 120, 130, 140]*10,
    'CustomerServiceCalls': [1, 2, 3, 4, 0, 1, 2, 3, 4, 0]*10,
    'Churn': ['No', 'No', 'Yes', 'No', 'Yes', 'No', 'Yes', 'Yes', 'No', 'Yes']*10
}
df = pd.DataFrame(data)

# Features and target variable
X = df[['Age', 'MonthlyCharge', 'CustomerServiceCalls']]
y = df['Churn']

# Splitting into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Decision Tree model
clf = DecisionTreeClassifier()
clf.fit(X_train, y_train)

# Prediction and evaluation
y_pred = clf.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print(f'Model Accuracy: {accuracy}')

# Visualize the decision tree
plt.figure(figsize=(12, 8))
tree.plot_tree(clf, filled=True, feature_names=['Age', 'MonthlyCharge', 'CustomerServiceCalls'], class_names=['No Churn', 'Churn'])
plt.title('Decision Tree for Predicting Customer Churn')
plt.show()
```

---


## 📊 Interpreting the Results
Accuracy Score: Shows the % of correct predictions on test data.

Tree Visualization: Helps understand what conditions lead to churn predictions.

> ✅ By understanding decision paths, businesses can intervene early (e.g., reduce charges or improve customer service) to reduce churn risk.
