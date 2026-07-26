# 📈 Machine Learning–Driven Financial Strategy (FAANG Stocks)

A quantitative trading project that combines **feature engineering, machine learning, and backtesting** to evaluate whether short-term stock price movements can be predicted and converted into profitable trading strategies.

---

## Overview

This project investigates the predictive power of machine learning models on **daily FAANG stock data** and evaluates whether modest predictive signals can generate **strong financial returns** when paired with proper execution strategies.

While traditional metrics (accuracy, ROC-AUC) suggest weak predictive power, the **economic performance via backtesting reveals significant alpha generation**.

---

## Objectives

- Predict **next-day stock price direction** (up/down)
- Engineer meaningful features from raw market data
- Compare multiple machine learning models
- Evaluate models using both **statistical metrics** and **trading performance**
- Test execution strategies including **trailing-stop mechanisms**

---

## Dataset

- Source: FAANG stock price data (`faang_stock_prices.csv`), https://www.kaggle.com/datasets/vishardmehta/faang-stock-market-data-with-technical-indicators/data
- Frequency: Daily
- Features:
  - OHLCV (Open, High, Low, Close, Volume)
  - Technical indicators (RSI, MACD, Bollinger Bands, ATR)
  - Lag features (1, 2, 3, 5 days)
  - Rolling statistics (z-scores, volatility)
  - Market interaction signals (cross-sectional mean, NVDA anchor)

- Final dataset:
  - ~14,600 records
  - 60+ engineered features

---

## Methodology

### 1. Feature Engineering
- Lagged variables for price, volume, and indicators
- Rolling normalization using 60-day z-scores
- Volatility estimation (Garman-Klass)
- Higher moments (skewness, kurtosis)
- Market-wide interaction features

### 2. Target Definition
- Binary classification:
  - `1` → price increases next day
  - `0` → price decreases

### 3. Model Training
- Time-series split (no data leakage)
- Train/Test split:
  - Train: ~11,500 samples
  - Test: ~2,900 samples

### 4. Models Evaluated
- Logistic Regression
- Support Vector Machine (SVC)
- Random Forest
- Extra Trees
- XGBoost
- LightGBM
- CatBoost
- AdaBoost
- Neural Network (MLP)
- Voting Ensemble

### 5. Evaluation Metrics
- Accuracy
- ROC-AUC
- Precision / Recall / F1

---

## Results

### Predictive Performance
- Accuracy: ~53–54%
- ROC-AUC: ~0.50–0.53  
   Indicates **low signal-to-noise ratio**, typical in financial markets

### Trading Performance 

| Model        | Strategy Type     | Total Return |
|--------------|------------------|-------------|
| Extra Trees  | Standard         | 232.23%     |
| Extra Trees  | Trailing Stop    | **783.73%** |
| Voting Model | Trailing Stop    | 397.09%     |
| SVC          | Trailing Stop    | 338.64%     |

 

## Takeaways

- Financial markets are **hard to predict statistically**
- Small predictive edges can still produce **large financial gains**
- Execution strategy (e.g., trailing stop) is **as important as the model**
- Ensemble and tree-based methods perform best in practice

---

## Limitations

- No transaction costs or slippage included
- Daily data may miss intraday dynamics
- Potential overfitting in feature space
- Results are **not financial advice**

---

Dataset is primarily availabe on https://www.kaggle.com/datasets/vishardmehta/faang-stock-market-data-with-technical-indicators/data
