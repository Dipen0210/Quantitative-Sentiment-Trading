# Quantitative-Sentiment-Trading

This project implements an end-to-end **sentiment-based algorithmic trading strategy** that integrates **Natural Language Processing (NLP)** with **technical indicators** to generate, evaluate, and backtest trading signals. The pipeline utilizes real-time financial news, fine-tuned transformer models (FinBERT), and market momentum indicators (RSI, MACD) to drive data-informed investment decisions.

---

## 🔍 Overview

The project is divided into two phases:

1. **Model Evaluation and Sentiment Classification**
   - Benchmarks traditional ML models (Logistic Regression, Naive Bayes, SVM, Random Forest) against FinBERT on a labeled Kaggle financial news dataset.
   - Fine-tunes FinBERT using Hugging Face Transformers for domain-specific sentiment classification.
   - Achieves **89% accuracy** and **macro F1-score of 0.85** on the test set.

2. **Trading Signal Generation and Backtesting**
   - Applies FinBERT to real-time news headlines fetched via NewsAPI.
   - Extracts stock tickers from headlines using a custom entity-matching dictionary.
   - Fetches recent OHLC data for each ticker using Yahoo Finance.
   - Computes **RSI** and **MACD** for momentum analysis.
   - Aggregates sentiment and technical signals into final BUY, SELL, or HOLD decisions.
   - Simulates trades using a custom backtesting engine with realistic portfolio logic.

---

## 🧠 Tech Stack

- **NLP Model:** FinBERT (`yiyanghkust/finbert-tone`)
- **ML Libraries:** scikit-learn, Transformers (Hugging Face)
- **Data APIs:** NewsAPI, yFinance
- **Backtesting:** Custom Python engine
- **Visualization:** Matplotlib, Seaborn

---

## 📊 Results

| Metric                      | Value              |
|----------------------------|--------------------|
| Starting Capital           | $100,000           |
| Final Portfolio Value      | $125,970.73        |
| Net Profit                 | $25,970.73         |
| Return on Investment (ROI)| +25.97%            |
| Total Trades Executed(sell)     | 1                  |
| Top Model (Sentiment)      | FinBERT            |

---

## 📈 Signal Strategy

Final trading signals are generated using the average of three components:

- **Sentiment Signal** (from FinBERT)
- **RSI Signal**
- **MACD Signal**

Each component is mapped as:
- `+1 = BUY`
- ` 0 = HOLD`
- `−1 = SELL`

Averaged signal thresholds:
- Final Score > 0.33 → BUY  
- Final Score < −0.33 → SELL  
- Otherwise → HOLD

---

## 📉 Backtesting Logic

- Capital is equally distributed among BUY signals.
- Buys are placed at the next available open price.
- Assets are sold on a SELL signal or after 5 days.
- Portfolio tracks cash, holdings, trade log, and cumulative returns.

---

## 🚀 Future Enhancements

- Integrate live brokerage APIs (e.g., Alpaca, Interactive Brokers) for real-time trading.
- Add more technical indicators (e.g., Bollinger Bands, ATR) for signal robustness.
- Expand to high-frequency intraday decision-making.
- Support broader asset classes (ETFs, commodities, crypto).
- Add explainability tools (e.g., SHAP, LIME) for model transparency.

---

## Output

<img width="860" height="506" alt="Screenshot 2025-05-08 at 1 22 40 AM" src="https://github.com/user-attachments/assets/2b71ac67-9494-42e5-89fd-589ab4dbd8e7" />

<img width="1387" height="383" alt="Screenshot 2025-04-18 at 11 38 37 PM" src="https://github.com/user-attachments/assets/4a88f6b6-0aab-4bd8-b3d9-d11b8b225d8b" />

<img width="464" height="169" alt="Screenshot 2025-04-18 at 11 46 25 PM" src="https://github.com/user-attachments/assets/ecc1199b-5c9d-41a8-b61c-3fce9135f99c" />

---
