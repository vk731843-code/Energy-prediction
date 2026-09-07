# Energy-prediction
# ⚡ Appliance Energy Consumption Prediction Using Linear Regression

## 📌 Project Overview

This project predicts **appliance energy consumption (kWh)** based on **temperature (°C)** using **Simple Linear Regression**.

The model learns the relationship between temperature and energy consumption from historical data and predicts energy consumption for new temperature values.

---

## 🎯 Objectives

* Predict appliance energy consumption based on temperature.
* Build a **Simple Linear Regression** machine learning model.
* Split the dataset into training and testing data.
* Evaluate the model using **Mean Squared Error (MSE)** and **R² Score**.
* Visualize the actual test data and regression line.
* Save the trained model for future predictions.

---

## 📊 Dataset

The project uses the dataset:

**`appliance_energy.csv`**

### Input Feature

| Feature              | Description                                  |
| -------------------- | -------------------------------------------- |
| 🌡️ Temperature (°C) | Temperature used as the independent variable |

### Target Variable

| Target                     | Description                                  |
| -------------------------- | -------------------------------------------- |
| ⚡ Energy Consumption (kWh) | Appliance energy consumption to be predicted |

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data loading and preprocessing
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Scikit-learn** – Machine learning model and evaluation
* **Joblib** – Saving the trained model
* **Google Colab / Jupyter Notebook**

---

## 📁 Project Structure

```text
Appliance-Energy-Prediction/
│
├── appliance_energy.csv
├── appliance_energy_prediction.ipynb
├── appliance_energy_model.pkl
├── README.md
└── requirements.txt
```

---

## ⚙️ Methodology

The project follows these steps:

```text
Dataset
   ↓
Load Dataset
   ↓
Check Missing Values
   ↓
Remove Missing Data
   ↓
Select Feature & Target
   ↓
Train-Test Split
   ↓
Create Linear Regression Model
   ↓
Train Model
   ↓
Make Predictions
   ↓
Evaluate Model
   ↓
Visualize Results
   ↓
Save Model
```

---

## 🔬 Implementation

### 1. Import Required Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
```

### 2. Load the Dataset

```python
df = pd.read_csv('/content/appliance_energy.csv')

print(df.head())
```

### 3. Check and Handle Missing Values

```python
print(df.isnull().sum())

df = df.dropna()
```

Missing values are checked and removed before training the machine learning model.

---

## 📌 Feature and Target Selection

The model uses:

```python
X = df[['Temperature (°C)']]
y = df['Energy Consumption (kWh)']
```

Where:

* **X** → Independent variable (Temperature)
* **y** → Dependent variable (Energy Consumption)

---

## 📚 Train-Test Split

The dataset is divided into **80% training data** and **20% testing data**.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

## 🤖 Model Creation and Training

A Simple Linear Regression model is created:

```python
model = LinearRegression()
```

The model is then trained using the training dataset:

```python
model.fit(X_train, y_train)
```

The basic linear regression relationship can be represented as:

```text
y = mx + c
```

Where:

* `y` = Predicted energy consumption
* `x` = Temperature
* `m` = Regression coefficient
* `c` = Intercept

---

## 🔮 Making Predictions

Predictions are generated using the test data:

```python
y_pred = model.predict(X_test)

print(y_pred)
```

---

## 📈 Model Evaluation

The model is evaluated using:

### Mean Squared Error (MSE)

```python
mse = mean_squared_error(y_test, y_pred)
```

MSE measures the average squared difference between actual and predicted values. A lower MSE generally indicates better prediction performance.

### R² Score

```python
r2 = r2_score(y_test, y_pred)
```

R² indicates how well the model explains the variation in energy consumption. A value closer to **1** generally indicates a better fit.

```python
print(f"Mean Squared Error: {mse}")
print(f"R-Squared: {r2}")
```

---

## 📊 Visualization

The actual test data and regression line are plotted using Matplotlib.

```python
plt.scatter(
    X_test,
    y_test,
    color='blue',
    label='Test Data'
)

plt.plot(
    X_test,
    y_pred,
    color='red',
    label='Regression Line'
)

plt.xlabel('Temperature (°C)')
plt.ylabel('Energy Consumption (kWh)')
plt.legend()

plt.title(
    'Energy Consumption Prediction using Simple Linear Regression'
)

plt.show()
```

The scatter points represent the **actual energy consumption**, while the regression line represents the **model's predicted relationship** between temperature and energy consumption.

---

## 💾 Save the Trained Model

The trained model is saved using Joblib:

```python
import joblib

joblib.dump(
    model,
    'appliance_energy_model.pkl'
)
```

The saved file:

```text
appliance_energy_model.pkl
```

can be used later to make predictions without retraining the model.

---

## 🚀 Future Prediction

The saved model can be loaded using:

```python
model = joblib.load(
    'appliance_energy_model.pkl'
)
```

For example, a new temperature value can be passed to the model to estimate energy consumption.

---

## 🌍 Applications

This type of prediction system can be useful for:

* 🏠 Smart home energy management
* ⚡ Appliance energy monitoring
* 📊 Energy consumption forecasting
* 💡 Energy-saving systems
* 🌱 Energy efficiency analysis
* 🏢 Building energy management

---

## ✅ Advantages

* Simple and easy to implement.
* Easy to understand and interpret.
* Requires low computational resources.
* Fast training and prediction.
* Useful for understanding the relationship between temperature and energy consumption.

---

## ⚠️ Limitations

* Uses only **temperature** as the input feature.
* Real appliance energy consumption depends on several factors.
* Linear Regression assumes a linear relationship between temperature and energy consumption.
* Prediction accuracy depends on the quality and size of the dataset.

---

## 🔮 Future Improvements

The project can be improved by adding more input parameters such as:

* Humidity
* Appliance type
* Operating duration
* Number of appliances
* Time of day
* Day of week
* Previous energy consumption
* Weather conditions

More advanced models such as **Random Forest, Decision Tree, XGBoost, or Neural Networks** can also be compared with Linear Regression.

---

## 📌 Conclusion

This project demonstrates how **Simple Linear Regression** can be used to predict appliance energy consumption based on temperature.

The workflow includes data preprocessing, feature selection, train-test splitting, model training, prediction, performance evaluation, visualization, and model saving.

It provides a basic foundation for developing more advanced **smart energy monitoring and prediction systems**.

---

## 👨‍💻 Author

**Vinoth Kumar**

⭐ If you find this project useful, consider giving the repository a star!
