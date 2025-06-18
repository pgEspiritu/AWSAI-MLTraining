# ✅ Solution: Neural Networks – Customer Purchase Prediction

Neural networks are powerful but often seen as **"black box" models** due to their complex internal mechanics. However, in this solution, we’ll explore **two important visualizations** to gain insight into their behavior:

- 📈 **Training Process (Model Accuracy & Loss)**. You can plot the training and validation loss and accuracy over epochs to understand how the model is learning.
- 🧭 **Decision Boundary (How the model separates classes)**. For a simple neural network like the one in our example (with two input features), you can visualize the decision boundary on a 2D plot.

---

# 📊 Model Accuracy and Model Loss

In the neural network exercise to predict customer purchase behavior, **model accuracy** and **model loss** are essential metrics to evaluate how well the model is performing.

---

## ✅ Model Accuracy

- **Definition**: Accuracy is the proportion of correct predictions made by the model compared to the total number of predictions.
- **Formula**:  
  `Accuracy = (Number of Correct Predictions) / (Total Number of Predictions)`
- **Example Interpretation**:  
  An accuracy of **0.90** means the model correctly predicted 90% of the cases (both purchases and non-purchases).
- **Significance**:  
  Higher accuracy implies the model is making more correct predictions, which generally indicates better performance—especially for balanced datasets.

---

## ❌ Model Loss

- **Definition**: Loss is a measure of how far the model's predicted outputs are from the actual target values. It reflects the **model’s error**.
- **Loss Function Used**:  
  **Binary Cross-Entropy**, which is ideal for binary classification problems like purchase vs. no purchase.
  - This function compares the predicted probability (output of sigmoid activation) with the actual label (0 or 1).
  - It computes the error for each prediction and then averages it over all predictions.
- **Interpretation**:  
  - **Lower loss** = better performance, as predictions are closer to true labels.  
  - **Higher loss** = model predictions are less reliable or incorrect.

---

## 🧠 Summary

| Metric         | Description                                                  | Desired Outcome        |
|----------------|--------------------------------------------------------------|------------------------|
| **Accuracy**   | Percentage of correct predictions                            | Higher is better       |
| **Loss**       | Average error between predicted and actual labels            | Lower is better        |
| **Loss Function** | Binary Cross-Entropy (for binary classification tasks)    |                        |


### 🧪 Updated Training Code with `validation_split`:
```python
import warnings
warnings.filterwarnings('ignore')

# Re-train the model with validation tracking
history = model.fit(X_train, y_train, epochs=10, batch_size=10, validation_split=0.2)
```

---

## 📊 Plot Accuracy and Loss over Epochs:
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 5))

# Accuracy
plt.subplot(1, 2, 1)
plt.plot(history.history['accuracy'], label='Train Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.title('Model Accuracy')
plt.xlabel('Epoch')
plt.ylabel('Accuracy')
plt.legend(loc='lower right')

# Loss
plt.subplot(1, 2, 2)
plt.plot(history.history['loss'], label='Train Loss')
plt.plot(history.history['val_loss'], label='Validation Loss')
plt.title('Model Loss')
plt.xlabel('Epoch')
plt.ylabel('Loss')
plt.legend(loc='upper right')

plt.tight_layout()
plt.show()
```

---

## 🧭 Visualizing the Decision Boundary
With 2 input features, we can visualize how the neural network separates the two classes — purchase (1) vs no purchase (0).

### ✳️ What is a Decision Boundary?
- A boundary in the input feature space that separates different predicted classes.
- In our case: based on VisitDuration and PagesVisited.
- Neural networks can learn non-linear decision boundaries.

---

## 🗺️ Code to Visualize the Boundary:

```python
# Create a mesh grid over the feature space
x_min, x_max = df['VisitDuration'].min() - 0.1, df['VisitDuration'].max() + 0.1
y_min, y_max = df['PagesVisited'].min() - 0.1, df['PagesVisited'].max() + 0.1
xx, yy = np.meshgrid(np.linspace(x_min, x_max, 100),
                     np.linspace(y_min, y_max, 100))

# Flatten and predict
grid = np.c_[xx.ravel(), yy.ravel()]
Z = model.predict(grid)
Z = Z.reshape(xx.shape)

# Plot
plt.figure(figsize=(8, 6))
plt.contourf(xx, yy, Z, cmap=plt.cm.Pastel1, alpha=0.8)
plt.scatter(df['VisitDuration'], df['PagesVisited'], c=df['Purchase'], edgecolor='k', cmap=plt.cm.coolwarm)
plt.title('Decision Boundary of Neural Network')
plt.xlabel('Visit Duration')
plt.ylabel('Pages Visited')
plt.colorbar(label='Predicted Class Probability')
plt.show()
```

---

## 🧠 Key Takeaways
- Loss vs Accuracy: Loss shows how wrong the model is; accuracy shows how often it is right.
- Decision Boundary: Gives a visual intuition of how the neural network separates different classes.
- Such insights can help debug and refine models even when internal logic is opaque.

---

## 🔚 Final Note
Don't forget to stop or delete your notebook instance after reviewing the solution to avoid unnecessary compute charges.

---

## 📚 References
- [NumPy Documentation](https://numpy.org/doc/stable/reference/index.html#reference)
- [Matplotlib API Reference](https://matplotlib.org/stable/api/index.html)
