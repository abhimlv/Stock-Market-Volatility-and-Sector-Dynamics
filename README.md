# 📈 Stock Market Volatility and Sector Dynamics Analysis

This project analyzes the **volatility patterns** of major stock market sectors and explores their **interrelationships** over time. Leveraging Python, financial APIs, and Power BI, we uncover insights into market behavior through statistical metrics, correlation heatmaps, and interactive dashboards.

---

## 📌 Project Overview

* **Goal**: Analyze volatility and sectoral dynamics of S\&P 500 sectors
* **Timeframe**: January 2022 to February 2023 (approx. 250 trading days)
* **Tools Used**: Python (yFinance, Pandas, NumPy, Matplotlib), Power BI, Financial APIs
* **Key Metrics**: Daily % Change, Standard Deviation (Volatility), Sector Correlations

---

## 🗃️ Data Collection

* Collected **daily closing prices** for 11 S\&P 500 sector ETFs via **yFinance**
* Calculated **daily percent change** and derived **volatility** as the standard deviation

```python
import yfinance as yf
import pandas as pd

tickers = ['XLF', 'XLK', 'XLY', 'XLP', 'XLE', 'XLV', 'XLI', 'XLB', 'XLRE', 'XLU', 'XLC']
data = yf.download(tickers, start='2022-01-01', end='2023-02-28')['Adj Close']
returns = data.pct_change().dropna()
```

📎 *Attach Line Chart of ETF Adjusted Close from Page 2 of report*

---

## 📊 Volatility Calculation

* Computed **sector-wise volatility** using the standard deviation of daily returns
* Visualized top 3 most volatile sectors

📎 *Attach Sector-wise Volatility Bar Chart from Page 3 of report*

```python
volatility = returns.std()
volatility.sort_values(ascending=False).plot(kind='bar')
```

---

## 🔄 Rolling Volatility

* Used a **20-day rolling window** to measure how volatility evolved over time
* This helps reveal periods of market stress or stability

📎 *Attach Rolling Volatility Line Graph from Page 4 of report*

```python
rolling_volatility = returns.rolling(window=20).std()
rolling_volatility.plot(figsize=(12,6))
```

---

## 🔗 Sector Correlation Analysis

* Created a **correlation matrix** of sector returns
* Identified strongly correlated sectors (e.g., XLF & XLK)

📎 *Attach Correlation Heatmap from Page 5 of report*

```python
correlation_matrix = returns.corr()
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
```

---

## 📈 Power BI Dashboard

* Designed an interactive dashboard to explore:

  * Sector-wise price trends
  * Volatility comparisons
  * Year-over-year returns

📎 *Attach screenshots of Power BI dashboard visuals from Page 6–7*

---

## 🧠 Key Insights

* **Technology (XLK)** and **Energy (XLE)** were the most volatile sectors
* Defensive sectors like **Utilities (XLU)** had low volatility
* Strong correlations suggest linked behavior (e.g., growth sectors)
* Rolling volatility shows market fluctuations during inflation/news cycles

---

## 🧰 Tools & Libraries

* **Python**: yFinance, Pandas, NumPy, Seaborn, Matplotlib
* **BI**: Power BI for interactive sector dashboards
* **Finance**: Adjusted Close, Daily Returns, Rolling Std Dev

---

---

## 🔮 Future Work

* Incorporate **macro-economic indicators** like inflation or interest rate data
* Apply **forecasting models** to predict future volatility
* Explore **clustering** of sectors based on volatility profiles

---

## 🧠 Summary

This project delivers a multi-dimensional view of sector dynamics and volatility within the stock market. Through Python-driven analysis and visual storytelling via Power BI, it highlights the value of data-driven market monitoring for investors and analysts alike.
