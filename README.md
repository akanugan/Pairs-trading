# Pairs Trading Strategy: Statistical Arbitrage with AAPL & MSFT

## Project Introduction
Pairs trading is a **market-neutral trading strategy** that identifies two historically correlated stocks and executes trades when their relative prices diverge. The assumption is that the spread between the two stocks will revert to its historical mean, allowing traders to profit from this reversion.

In this project, we implement a **pairs trading algorithm** using AAPL and MSFT, testing for **cointegration** and using **Z-score thresholds** to determine trade entry and exit points.

## Data Collection
We collect historical stock price data for AAPL and MSFT from Yahoo Finance using the `yfinance` library. The dataset includes **Adjusted Closing Prices** from 2020 to 2024.

### **Key Steps:**
- Fetch stock data using `yfinance`.
- Perform a **cointegration test** to ensure the stock pair is statistically linked.
- Compute the **spread** and **Z-score** to identify trading opportunities.

## Methodology

### **1. Cointegration Test**
We use the **Engle-Granger Cointegration Test** to check if the price series of AAPL and MSFT move together in the long run. If the p-value is **less than 0.05**, the stocks are considered cointegrated.

### **2. Spread & Z-score Calculation**
- We use **Ordinary Least Squares (OLS)** regression to determine the hedge ratio between the stocks.
- The **spread** is computed as:
  
  \[ \text{Spread} = \text{AAPL Price} - ( \beta \times \text{MSFT Price} ) \]
  
- The **Z-score** is calculated to normalize the spread:
  
  \[ Z = \frac{( \text{Spread} - \text{Mean Spread} )}{\text{Standard Deviation of Spread}} \]

### **3. Trading Rules**
- **Go Long (Buy AAPL, Sell MSFT)** if **Z-score < -1** (Expect spread to increase).
- **Go Short (Sell AAPL, Buy MSFT)** if **Z-score > 1** (Expect spread to decrease).
- **Exit Position** when the Z-score returns to within **-0.5 to 0.5**.

## Key Results

- **Cointegration Test:** If the p-value < 0.05, the stocks are cointegrated and suitable for pairs trading.
- **Spread & Z-score Visualization:** Plots of spread movement and Z-score fluctuations help identify trading signals.
- **Backtest Performance:** The strategy is backtested on historical data, simulating capital growth over time.

### **Sample Plots:**
1. **Spread Over Time:** Highlights mean reversion.
2. **Z-score of Spread:** Identifies entry/exit points.
3. **Backtest Performance:** Shows the impact of the trading strategy on capital.

## How to Run the Code
1. Install required dependencies:
   ```bash
   pip install pandas numpy yfinance statsmodels matplotlib plotly
   ```
2. Run the Jupter Notebook - supported by Colab or Kaggle
3. View generated **plots** and **backtest results**.

## Next Steps / Future Enhancements
- **Enhancing Backtesting:** Include transaction costs and slippage.
- **Stop-Loss Implementation:** Introduce risk management measures.
- **Automated Trading:** Deploy the strategy using live data on a trading platform (e.g., Alpaca API).
- **Machine Learning Extension:** Apply clustering to discover new pairs dynamically.

---
### 📌 **Project Summary:**
This project showcases **quantitative finance techniques** to build an **algorithmic trading strategy** using Python. It demonstrates skills in **data analysis, statistical modeling, and backtesting**, making it a great addition to any portfolio in **quantitative research, financial engineering, or data science**.

Would love to hear feedback! 🚀

