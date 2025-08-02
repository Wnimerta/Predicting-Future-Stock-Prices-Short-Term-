# 📈 Predict Future Stock Prices (Short-Term)

Welcome to the **Stock Price Prediction Project**! This project uses historical stock data and machine learning to forecast short-term price movements.

---

## 📂 Dataset Overview

* **Source**: Yahoo Finance (via yfinance or CSV)
* **Features Used**:

  * Open, High, Low, Close Prices
  * Volume
  * Moving Averages (5, 10, 20 days)
* **Target**: Future Closing Price

---

## 🎯 Objectives

* Fetch historical stock market data
* Create lagged features and moving averages
* Train regression models to predict next-day prices
* Visualize actual vs predicted trends

---

## 🧰 Technologies Used

* Python 🐍
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn
* yfinance

---

## 🧪 Steps Performed

### 1️⃣ Data Collection

```python
import yfinance as yf
data = yf.download('AAPL', start='2020-01-01', end='2023-01-01')
```

### 2️⃣ Feature Engineering

```python
data['MA10'] = data['Close'].rolling(window=10).mean()
data['MA20'] = data['Close'].rolling(window=20).mean()
data['Target'] = data['Close'].shift(-1)
```

### 3️⃣ Data Cleaning & Splitting

```python
data.dropna(inplace=True)
X = data[['Close', 'MA10', 'MA20']]
y = data['Target']
```

### 4️⃣ Model Training

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X, y)
```

### 5️⃣ Prediction & Visualization

```python
predicted = model.predict(X)
plt.figure(figsize=(14, 6))
plt.plot(y.values, label='Actual')
plt.plot(predicted, label='Predicted')
plt.title("Stock Price Prediction")
plt.legend()
plt.show()
```

---

## 📊 Visuals

* 📉 Line chart of Actual vs Predicted closing prices
  <img width="1048" height="546" alt="image" src="https://github.com/user-attachments/assets/a0be2075-c4c5-4660-848e-553af5d6fbf1" />

---

## 💡 Key Learnings

* Lagging features help capture market patterns
* Moving averages smooth noise and improve accuracy
* Linear regression provides a simple but solid baseline

---

## 🧑‍💻 Author

**Nimerta Wadhwani**
💼 AI/ML Intern @ Developers Hub
🔗 [LinkedIn](https://www.linkedin.com/in/nimerta-wadhwani-816362253)

---

## ✅ License

This project is for educational purposes only. Investment decisions should not be based on this model.
