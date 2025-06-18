# 🤖 Exercise: Neural Networks – Predicting Customer Purchase Behavior

## 🎯 Objective
Build and train a simple neural network using TensorFlow/Keras to **predict whether a customer will make a purchase** based on:
- ⏱️ **Website visit duration**
- 📄 **Number of pages visited**

This is a **binary classification** task using **synthetic data** for fast and clear demonstration.

---

## 🧪 Step 1: Generate Synthetic Data

```python
import numpy as np
import pandas as pd
import warnings

warnings.filterwarnings('ignore')

# Generate synthetic features
np.random.seed(0)
data_size = 200
features = np.random.rand(data_size, 2)  # VisitDuration, PagesVisited

# Label generation rule
labels = (features[:, 0] + features[:, 1] > 1).astype(int)  # Binary classification (0 or 1)

# Convert to DataFrame
df = pd.DataFrame(features, columns=['VisitDuration', 'PagesVisited'])
df['Purchase'] = labels

# View sample data
df.head()
```

---

## 🧹 Step 2: Preprocess the Data

```python
from sklearn.model_selection import train_test_split

# Split features and target
X = df[['VisitDuration', 'PagesVisited']]
y = df['Purchase']

# Split into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

---

## 🏗️ Step 3: Build and Train the Neural Network

```python
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Build the neural network
model = Sequential([
    Dense(10, activation='relu', input_shape=(2,)),  # Hidden layer
    Dense(1, activation='sigmoid')  # Output layer for binary classification
])

# Compile the model
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# Train the model
model.fit(X_train, y_train, epochs=10, batch_size=10)
```

---

## 📊 Step 4: Evaluate the Model

```python
# Evaluate the model
loss, accuracy = model.evaluate(X_test, y_test)
print(f"Test Accuracy: {accuracy:.4f}")
```

---

## 💡 Key Takeaways
- This example demonstrates how a neural network can be quickly trained on simple features for binary classification.
- The activation functions used:
  - **relu** in the hidden layer for non-linearity.
  - **sigmoid** in the output layer for binary classification.
- Binary cross-entropy is used as the loss function, appropriate for binary classification tasks.

> 🔁 Feel free to increase epochs or tweak layer sizes for experimentation.

---

## ⚠️ Cleanup Reminder
> After you're done, remember to stop your GPU instance or workspace to avoid unnecessary charges.
