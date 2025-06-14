## 🧠 Machine Learning Exercise: Supervised and Unsupervised Learning

In this exercise, you will complete two machine learning tasks using the Jupyter Notebook:

- ✅ Supervised Learning  
- ✅ Unsupervised Learning  

You'll generate **synthetic data** for both exercises and execute them in the notebook.

---

## 🔧 Part 1: Predicting Building Energy Efficiency (Supervised Learning)

### 🏗️ Scenario  
You are working for an **architecture firm**, and your task is to build a model that **predicts the energy efficiency rating of buildings** based on features like wall area, roof area, overall height, etc.

---

### 🧪 Supervised Learning Code

```python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error

warnings.filterwarnings('ignore')

# Generate synthetic dataset
np.random.seed(0)
data_size = 500
data = {
    'WallArea': np.random.randint(200, 400, data_size),
    'RoofArea': np.random.randint(100, 200, data_size),
    'OverallHeight': np.random.uniform(3, 10, data_size),
    'GlazingArea': np.random.uniform(0, 1, data_size),
    'EnergyEfficiency': np.random.uniform(10, 50, data_size)  # Energy efficiency rating
}
df = pd.DataFrame(data)

# Data preprocessing
X = df.drop('EnergyEfficiency', axis=1)
y = df['EnergyEfficiency']

# Visualize the relationships
sns.pairplot(df, x_vars=['WallArea', 'RoofArea', 'OverallHeight', 'GlazingArea'], 
             y_vars='EnergyEfficiency', height=4, aspect=1, kind='scatter')
plt.show()

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train the model
model = RandomForestRegressor()
model.fit(X_train, y_train)

# Predict and evaluate
predictions = model.predict(X_test)
mse = mean_squared_error(y_test, predictions)
print(f"Mean Squared Error: {mse}")

# Plot True vs Predicted values
plt.figure(figsize=(10, 6))
plt.scatter(y_test, predictions)
plt.xlabel("True Values")
plt.ylabel("Predictions")
plt.title("True Values vs Predicted Values")
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], 'k--')
plt.show()
```

---

## 🚗 Part 2: Vehicle Clustering (Unsupervised Learning)

### 🛠️ Scenario  
You are working for an **automotive company**, and your task is to **cluster vehicles into groups** based on their features such as weight, engine size, and horsepower.

---

### 🔍 Unsupervised Learning Code  
Use the code below to cluster vehicles based on their specifications using **K-Means Clustering**.

```python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import warnings
from sklearn.cluster import KMeans

warnings.filterwarnings('ignore')

# Generate synthetic dataset for vehicles
np.random.seed(0)
data_size = 300
data = {
    'Weight': np.random.randint(1000, 3000, data_size),
    'EngineSize': np.random.uniform(1.0, 4.0, data_size),
    'Horsepower': np.random.randint(50, 300, data_size)
}
df = pd.DataFrame(data)

# No labels are needed for unsupervised learning
X = df

# Perform KMeans clustering
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(X)

# Plotting the clusters
plt.scatter(df['Weight'], df['Horsepower'], c=kmeans.labels_, cmap='viridis')
plt.xlabel('Weight')
plt.ylabel('Horsepower')
plt.title('Vehicle Clusters')
plt.show()
```

---

> **🔍 Note:**  
> These exercises use **synthetic data** for simplicity and demonstration purposes.  
> In real-world applications, you'll work with **actual datasets** and often require **more complex models** and preprocessing steps.
> 
> The choice of algorithms—**`RandomForestRegressor`** for supervised learning and **`KMeans`** for unsupervised learning—was made based on their **general applicability** and **ease of understanding** for educational purposes.

