# Concrete Corrosion Prediction using Machine Learning

## 📌 Project Overview

This project develops a machine learning framework to predict the **corrosion rate in reinforced concrete structures** using environmental and structural sensor measurements.

Multiple regression algorithms were trained and evaluated to determine the most reliable model for corrosion prediction. While simpler models showed strong baseline performance, **XGBoost was selected as the primary model due to its superior ability to model complex relationships and maintain robustness across varying conditions.**

---

# 🎯 Objective

To accurately estimate **corrosion rate** using sensor data representing environmental and structural conditions, including temperature, humidity, chemical properties, and mechanical stresses.

The system aims to support **predictive maintenance and early detection of structural degradation** in reinforced concrete infrastructures.

---

# 📊 Dataset Description

A dataset of **1000 samples** was used for training and evaluation.

### Input Features

* Temperature (°C)
* Humidity (%)
* pH
* Total Dissolved Solids (TDS ppm)
* Stress in X direction
* Stress in Y direction
* Stress in Z direction

### Target Variable

* Corrosion Rate

These variables represent key environmental and mechanical factors that influence electrochemical corrosion processes in reinforced concrete.

---

# ⚙️ Methodology

The machine learning pipeline consisted of the following steps:

1. **Dataset Loading and Validation**

   * Verified feature integrity and numerical consistency.

2. **Data Splitting**

   * 80% Training data
   * 20% Testing data

3. **Model Training**

   The following regression algorithms were implemented:

   * Linear Regression
   * Random Forest Regressor
   * Gradient Boosting Regressor
   * XGBoost Regressor

4. **Model Evaluation**

   Models were evaluated using:

   * R² Score
   * Root Mean Squared Error (RMSE)
   * Cross-Validation

5. **Performance Comparison**

   Model performance metrics were analyzed to identify the most reliable prediction model.

---

# 📈 Model Performance

| Model             | R² Score  | RMSE     |
| ----------------- | --------- | -------- |
| Linear Regression | **0.979** | **0.28** |
| XGBoost           | 0.966     | 0.36     |
| Gradient Boosting | 0.963     | 0.38     |
| Random Forest     | 0.924     | 0.54     |

Cross-Validation R² Score:

```
0.972 ± 0.003
```

This indicates **high model stability and strong predictive performance across multiple data splits**.

---

# 🏆 Model Selection

Although **Linear Regression achieved the highest R² score**, it assumes a **strictly linear relationship** between input variables and corrosion rate.

However, corrosion processes in reinforced concrete are influenced by **complex electrochemical, environmental, and mechanical interactions**. Such relationships are often **nonlinear and interdependent**.

For this reason, **XGBoost was selected as the primary model for this framework.**

Why XGBoost?

XGBoost offers several advantages for engineering prediction tasks:

* **Captures nonlinear relationships** between environmental and stress variables
* **Handles complex feature interactions** without manual feature engineering
* **Reduces overfitting** through gradient boosting regularization
* **Highly scalable and efficient for tabular datasets**
* Widely used in **industrial and research-grade predictive systems**

While Linear Regression performs well for simple linear patterns, **XGBoost provides greater robustness when deployed in real-world environments where conditions may vary significantly.**

Therefore, XGBoost was selected as the **preferred model for deployment and future system expansion.**

---

# 💾 Saved Models

The following trained models are included in this repository:

* `linear_regression_model.pkl`
* `xgboost_model.pkl`
* `gradient_boosting_model.pkl`
* `random_forest_model.pkl`

---

# 🚀 How to Use the Model

## 1️⃣ Install Dependencies

```bash
pip install pandas numpy scikit-learn xgboost joblib
```

---

## 2️⃣ Load a Model

```python
import joblib

model = joblib.load("xgboost_model.pkl")
```

---

## 3️⃣ Make a Prediction

```python
import pandas as pd

sample = pd.DataFrame({
    "temperature_C": [30],
    "humidity_percent": [70],
    "strain": [0.0015],
    "pH": [11.5],
    "TDS_ppm": [800],
    "stress_x": [2],
    "stress_y": [1.5],
    "stress_z": [2.5]
})

prediction = model.predict(sample)

print("Predicted Corrosion Rate:", prediction)
```

---

# 🧠 Key Insights

* Environmental and mechanical sensor data can effectively predict corrosion behavior.
* Corrosion rate demonstrates partially linear relationships with certain variables.
* Ensemble models like **XGBoost can capture more complex patterns**, making them better suited for real-world prediction systems.
* The framework demonstrates **high predictive reliability with cross-validation R² ≈ 0.972**.

---

# 📚 Future Work

Potential improvements for this project include:


* Development of a **real-time corrosion monitoring platform**
* Creation of a **visual dashboard for infrastructure health analysis**
* Extension to **time-series corrosion prediction models**
* Deployment of the model as a **web API or monitoring service**

---



