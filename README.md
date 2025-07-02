# Zelestra-X-AWS-ML-Ascend-Challenge


# ⚡ Solar Panel Efficiency Prediction - Zelestra Hackathon ☀️🔧

## 🧠 Project Overview

As solar energy becomes a cornerstone of sustainable infrastructure, ensuring high solar panel efficiency is vital. Traditional maintenance approaches are often reactive, leading to energy losses and operational costs.

This project was developed as part of the **Zelestra Hackathon**, aiming to predict **solar panel efficiency degradation and potential failures** using a machine learning approach. Our goal was to enable **predictive maintenance** using real-time and historical sensor data.

---

## 🧪 Problem Statement

Develop a machine learning model that predicts performance degradation and potential failures in solar panels using historical and real-time sensor data, enabling predictive maintenance and optimal energy output.

---

## 📂 Dataset

| File Name              | Description                                |
|------------------------|--------------------------------------------|
| `train.csv`            | Training data (20,000 rows, 17 columns)    |
| `test.csv`             | Test data (12,000 rows, 16 columns)        |
| `sample_submission.csv`| Submission format                          |

### 🔢 Features

| Column Name         | Description                                                                         |
|---------------------|-------------------------------------------------------------------------------------|
| id                  | Unique identifier                                                                  |
| temperature         | Ambient air temperature (°C)                                                        |
| irradiance          | Solar energy received per unit area (W/m²)                                          |
| humidity            | Moisture content in the air                                                         |
| panel_age           | Age of the solar panel in years                                                     |
| maintenance_count   | Number of past maintenance activities                                               |
| soiling_ratio       | Efficiency loss due to dust or debris (0.0 to 1.0)                                  |
| voltage             | Voltage output (V)                                                                  |
| current             | Current output (A)                                                                  |
| module_temperature  | Surface temperature of the panel                                                    |
| cloud_coverage      | Sky coverage percentage                                                             |
| wind_speed          | Wind speed in m/s                                                                   |
| pressure            | Atmospheric pressure (hPa)                                                          |
| string_id           | Identifier for a group of panels (e.g., A1, B2)                                     |
| error_code          | Diagnostic error codes (e.g., E00, E01, E02)                                        |
| installation_type   | Type of panel mounting - fixed, tracking, dual-axis                                |
| efficiency (target) | Final energy output efficiency (%)                                                  |

---

## 📐 Evaluation Metric

```python
Score = 100 * (1 - sqrt(mean_squared_error(actual, predicted)))
A higher score indicates better performance.

## 🧠 Models Used

✅ **TabNet Regressor** (Best score: **89.74798%**)  
🟡 **CatBoost Regressor**  
🟡 **XGBoost Regressor**

The **TabNet** model provided the best performance and was used for the final submission.

---

## 🧭 Approach

### 🔹 1. Data Preprocessing

**Categorical Encoding:**  
Encoded `string_id`, `error_code`, and `installation_type` using label encoding or one-hot encoding as needed.

**Feature Engineering:**  
Created new feature `power = voltage × current` to represent total energy output.

**Handling Missing Data:**  
Checked and handled missing or anomalous values.

**Scaling:**  
Normalized numerical features to improve model performance.

---

### 🔹 2. Model Training

- Trained **XGBoost** and **CatBoost** with hyperparameter tuning (Grid/Random Search) and early stopping.
- Trained **TabNet Regressor** with:
  - Learning rate scheduler  
  - Early stopping  
  - Custom metric evaluation  
- Used cross-validation for robust evaluation.

---

### 🔹 3. Evaluation & Ensembling

- Compared model scores using the evaluation metric.
- **TabNet achieved the highest score of 89.74798%.**
- Predictions were generated on the test set and submitted in the required format.

---

## 📊 Results

| Model     | Score (%)     |
|-----------|---------------|
| TabNet    | **89.74798** ✅ |
| XGBoost   | 87.10          |
| CatBoost  | 86.95          |

