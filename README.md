# Concrete Corrosion Prediction using Machine Learning

## 📌 Project Overview

This project develops a machine learning framework to predict the corrosion rate in reinforced concrete structures using sensor measurements.

Multiple regression models were trained and compared to identify the most accurate and reliable approach.

---

## 🎯 Objective

To estimate corrosion rate based on environmental and structural sensor data such as temperature, humidity, pH, ion concentration, and stress.

---

## 📊 Dataset Description

A dataset of **1000 samples** was used with the following input features:

* Temperature (°C)
* Humidity (%)
* Strain
* pH
* Total Dissolved Solids (TDS ppm)
* Stress in X direction
* Stress in Y direction
* Stress in Z direction

Target variable:

* Corrosion Rate

---

## ⚙️ Methodology

1. Imported dataset and performed basic validation
2. Split data into training and testing sets
3. Trained multiple regression models:

   * Linear Regression
   * Random Forest Regressor
   * Gradient Boosting Regressor
   * XGBoost Regressor
4. Evaluated models using:

   * R² Score
   * RMSE
   * Cross-Validation
5. Compared performance and selected the best model

---

## 📈 Model Performance

| Model             | R² Score  | RMSE     |
| ----------------- | --------- | -------- |
| Linear Regression | **0.979** | **0.28** |
| XGBoost           | 0.966     | 0.36     |
| Gradient Boosting | 0.963     | 0.38     |
| Random Forest     | 0.924     | 0.54     |

Cross-Validation R²: **0.972 ± 0.003**

---

## 🏆 Best Model

Linear Regression achieved the highest accuracy, indicating a predominantly linear relationship between sensor inputs and corrosion rate.

---

## 💾 Saved Models

The following trained models are included:

* `linear_regression_model.pkl`
* `xgboost_model.pkl`
* `gradient_boosting_model.pkl`
* `random_forest_model.pkl`

---

## 🚀 How to Use the Model

### 1️⃣ Install dependencies

```
pip install pandas numpy scikit-learn xgboost joblib
```

### 2️⃣ Load a model

```
import joblib
model = joblib.load("linear_regression_model.pkl")
```

### 3️⃣ Make prediction

```
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
print(prediction)
```

---

## 🧠 Key Insights

* Corrosion rate shows a strong linear dependence on sensor variables
* Simple models can perform as well as complex ensemble methods
* The framework is suitable for real-time corrosion monitoring

---

## 📚 Future Work

* Integrate real sensor data
* Deploy as real-time monitoring system
* Build dashboard for visualization
* Extend to time-series corrosion prediction

---

## 👨‍💻 Author

Machine Learning Corrosion Monitoring Project
