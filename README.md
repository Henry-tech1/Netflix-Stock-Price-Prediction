# 📈 Netflix Stock Price Prediction Using LSTM and XGBoost

**Group Project – April 2025**  
**Adanian Labs**   

## 👥 Contributing Members
- Henry Mwangi  
- Zuena Kiezy  
- Loryne Muthoni  
- Apphia Keino  
- Isaac Onyach

---

## 🧠 Project Overview

This project aims to predict Netflix (NFLX) stock prices using a **hybrid modeling approach** that combines **Long Short-Term Memory (LSTM)** networks and **XGBoost** regression. The dataset spans from **2002 to early 2025**, offering high volatility and rich features ideal for exploring machine learning forecasting techniques.

---

## 🚀 Approach Taken

We adopted a multi-step approach to tackle the stock price prediction challenge:

1. **Data Preprocessing**  
2. **Feature Engineering**  
3. **Hybrid Model Implementation (LSTM + XGBoost)**  
4. **Hyperparameter Tuning**  
5. **Model Evaluation & Interpretation (using SHAP)**

---

## 🧹 Data Preprocessing

- Loaded dataset using `pandas` from CSV.
- Explored and cleaned 5729 rows x 7 columns of financial data.
- Converted data types from `object` to appropriate numerical formats.
- Handled missing values (forward-fill).
- Removed stock split text entries.
- Normalized features using `MinMaxScaler` to the range (-1, 1).

---

## 🛠 Feature Engineering

Key engineered features included:

- **Financial indicators**: Daily return %, trading range, and price movement.
- **Temporal features**: Cyclical transformations for day and month using sine and cosine.
- **Lag features**: 1-day, 2-day, and 3-day lagged closing prices.
- **Rolling statistics**: 
  - 5-day rolling average
  - 5-day rolling standard deviation (volatility indicator)

---

## 🔁 Hybrid Modeling Approach

### LSTM
- **Input Shape**: 60-day sliding window of past data
- **Model Architecture**: 
  - LSTM Layer (50 units)
  - Dropout (20%)
  - Dense output layer
- **Compilation**: Adam optimizer, MSE loss
- **Train/Test Split**: 80/20

### XGBoost
- **Features**: Engineered tabular features
- **Hyperparameters**: 1000 estimators, learning rate = 0.01
- **Advantages**: Quick training, high performance on tabular data

### Combining Models
- Aligned output predictions from LSTM and XGBoost.
- Trimmed data to match sample dimensions before hybrid integration.

---

## ⚙️ Hyperparameter Tuning

Used **Optuna** for both models:

- **LSTM**: Tuned number of layers, hidden units, dropout rate, learning rate.
- **XGBoost**: Tuned depth, learning rate, regularization terms, and tree-specific settings.

---

## 📊 Model Evaluation & Interpretation

### Evaluation Metrics
| Metric   | XGBoost      | LSTM         | Winner     |
|----------|--------------|--------------|------------|
| R²       | 0.9992       | 0.9868       | XGBoost    |
| MSE      | 1.17e-4      | 1.96e-3      | XGBoost    |
| MAPE     | 4.86%        | 21.25%       | XGBoost    |

### Interpretation
Used **SHAP** to interpret XGBoost:
- Most important features: Lagged prices, rolling standard deviation.
- LSTM provided deep insights into temporal price trends.

---

## ❗ Challenges Faced

- Initial delays due to team coordination and scheduling.
- Uneven contribution and unclear task delegation.
- Integration issues: 3D (LSTM) vs. 2D (XGBoost) input format.
- Limited experience with time-series modeling.
- SHAP results revealed unexpected behavior requiring validation.

### Solutions for Future Projects
- Use Slack or similar tools for structured collaboration.
- Rotate roles to ensure balanced contributions.
- Use contribution dashboards (e.g., GitHub Projects or Trello).

---

## 💡 Key Insights

- Hybrid models can leverage LSTM’s sequential learning with XGBoost’s feature-focused accuracy.
- Rolling volatility and lagged price features are top contributors.
- XGBoost excels in precision, LSTM excels in pattern recognition.

---

## 🏁 Conclusion

The project successfully demonstrated the effectiveness of a **hybrid approach** to stock price prediction. By combining **LSTM’s temporal modeling** with **XGBoost’s feature-based precision**, the model achieved robust, interpretable, and highly accurate results.

---

## 🗂 Directory Structure

```plaintext
Netflix-Prediction/
│
├── data/
│   └── NFLX_Stock_2002-2025.csv
│
├── notebooks/
│   ├── LSTM_Model.ipynb
│   ├── XGBoost_Model.ipynb
│   └── Feature_Engineering.ipynb
│
├── models/
│   ├── trained_lstm.h5
│   └── xgboost_model.json
│
├── reports/
│   ├── final_report.pdf
│   └── presentation.pptx
│
├── README.md
└── requirements.txt


