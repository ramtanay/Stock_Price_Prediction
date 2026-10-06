# 📈 Stock Price Prediction

A machine learning project for predicting the **next trading day's closing price of Apple (AAPL)** using historical market data, engineered technical features, Linear Regression, and Random Forest Regression.

The project follows an end-to-end regression workflow:

**Market Data → EDA → Feature Engineering → Time-Based Split → Model Training → Evaluation → Feature Analysis → Model Comparison**

## 🚀 Project Overview

This project downloads historical AAPL stock market data from **Yahoo Finance** using the `yfinance` library.

The prediction target is:

> **The next trading day's closing price**

Two regression models are trained and compared:

- **Linear Regression**
- **Random Forest Regressor**

The notebook also examines Linear Regression coefficients and Random Forest feature importance.

## 🧠 Models Used

### Linear Regression

Linear Regression is used as the baseline regression model to learn the relationship between the engineered market features and the next day's closing price.

### Random Forest Regressor

Random Forest is used as a non-linear ensemble regression model.

Configuration used:

```python
RandomForestRegressor(
    n_estimators=100,
    random_state=42,
    n_jobs=-1
)
```
### 📊 Dataset

The notebook downloads AAPL data with:
```python
yf.download(
    "AAPL",
    start="2020-01-01",
    end="2026-01-01",
    auto_adjust=True
)
```
```
Original columns:

Date

Open

High

Low

Close

Volume
```

### 🛠️ Feature Engineering

The notebook creates the following derived features:
```
Feature

Description

Daily_Return

Daily percentage change in closing price

MA5

5-day moving average

MA20

20-day moving average

MA50

50-day moving average

Price_Range

High - Low

Open_Close_Diff

Close - Open

Previous_Close

Previous trading day's close

Target
```
Next trading day's closing price

Final model features:
```
Open
High
Low
Close
Volume
Daily_Return
MA5
MA20
MA50
Price_Range
Open_Close_Diff
Previous_Close
```
### 🔍 Exploratory Data Analysis

The notebook includes:
```
Dataset shape and data types

Statistical summary

Missing-value checks

Closing-price trend

Trading-volume trend

Daily-return analysis

Daily-return distribution

Moving-average analysis

Actual vs predicted prices

Random Forest feature importance

Model comparison
```
### 📐 Train/Test Strategy

Since the data is time ordered, the notebook uses a chronological 80/20 train-test split rather than a shuffled split.

First 80% → training set

Last 20% → test set

This keeps future observations out of the training portion.

### 📏 Evaluation Metrics

Mean Absolute Error (MAE)

Measures the average absolute prediction error.

MAE = mean(|actual - predicted|)

Root Mean Squared Error (RMSE)

Measures prediction error while giving larger errors more weight.

RMSE = sqrt(mean((actual - predicted)^2))

R² Score

Measures how well the model explains variance in the target values. Higher values generally indicate a better fit on the evaluated data.

### 📈 Visualizations

The notebook generates:

AAPL Closing Price

AAPL Trading Volume

Daily Returns

Daily Return Distribution

Closing Price with MA5, MA20, and MA50

Linear Regression — Actual vs Predicted

Random Forest — Actual vs Predicted

Random Forest Feature Importance

Linear Regression vs Random Forest Comparison

### 📁 Project Structure
```
Stock_Price_Prediction/
│
├── LICENSE
├── README.md
├── requirements.txt
└── Stock_Price_Prediction.ipynb
```
### ⚙️ Installation

Clone the repository:
```
git clone https://github.com/ramtanay/Stock_Price_Prediction.git
cd Stock_Price_Prediction
```
Create a virtual environment:

Windows
```
python -m venv venv
venv\Scripts\activate
```
macOS / Linux
```
python3 -m venv venv
source venv/bin/activate
```
Install dependencies:
```
pip install -r requirements.txt
```
### ▶️ Run the Notebook

Start Jupyter:

jupyter notebook

Open:
```
Stock_Price_Prediction.ipynb
```
Then run the cells from top to bottom.

The notebook fetches AAPL market data directly through yfinance, so no separate dataset file is required.

🔄 Project Workflow
```
Yahoo Finance
      ↓
AAPL Historical Data
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Next-Day Close Target
      ↓
Chronological 80/20 Split
      ↓
 ┌─────────────────────┐
 │                     │
 ▼                     ▼
Linear Regression   Random Forest
 │                     │
 └──────────┬──────────┘
            ▼
        Evaluation
            ↓
      Model Comparison
```
### ⚠️ Important Note

This project is intended for educational and experimentation purposes.

Stock prices can be affected by many factors that are not included in this notebook, such as news, market sentiment, macroeconomic conditions, company events, and broader market movements.

Therefore, predictions from this project should not be treated as financial advice or guaranteed future prices.

This implementation is a machine learning regression experiment, not a complete trading strategy.
### 🔮 Future Improvements
```
Add RSI, MACD, Bollinger Bands, and other technical indicators

Compare additional models such as XGBoost

Use walk-forward or expanding-window validation

Perform hyperparameter tuning

Predict returns rather than raw prices

Add market-index and sector-level features

Incorporate news or sentiment features

Build a Streamlit dashboard

Save trained models with joblib

Build a real-time prediction pipeline
```

### 👨‍💻 Author

### **Ramtanay Chakraborty**

GitHub: @ramtanay

📄 License

This project is licensed under the MIT License. See the LICENSE file for details.