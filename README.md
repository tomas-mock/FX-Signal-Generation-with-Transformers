# 🤖 FX Signal Generation with Transformers

**Dissertation Project – MSc Statistics, London School of Economics (2024–25)**  

---

## 🧠 Project Summary

This repository explores the **application of encoder-only Transformer architectures** for generating mid-frequency trading signals in the **Foreign Exchange (FX) spot market**. Leveraging hourly OHLC data for six major currency pairs from 2013–2023, the models predict the **direction and magnitude** of the next 12-hour move using a **three-class classification framework**.

While Transformer models have revolutionized sequence modeling in NLP, their use in financial forecasting—especially FX—is still emerging. This project evaluates their viability versus traditional methods, focusing on architectural design choices like **context length**, **positional encoding**, and **imbalance-aware loss functions**.

---

## 🧪 Methodology

- **Data:** Hourly OHLC data (2013–2023) for six major currency pairs:  
  `EUR/USD`, `GBP/USD`, `USD/JPY`, `USD/CAD`, `AUD/USD`, `USD/CHF`

- **Task:** Classify the *maximum absolute price move* in the next 12 hours into:  
  `Upward`, `Neutral`, or `Downward`

- **Model:**
  - Encoder-only Transformer (Vaswani et al., 2017)
  - Evaluated across 3 axes:
    - Context window: `24h`, `72h`, `120h`
    - Positional encoding: `Local` vs `Learnable`
    - Loss function: `Focal Loss` vs `Weighted Cross-Entropy`
  - XGBoost baseline (non-sequential) for comparison

- **Evaluation:**
  - **Custom Signal-Accuracy metric** (only scores predictions where trades are taken)
  - **Backtesting (2021–2023):** Simulated trading with realistic transaction costs

---

## 📊 Key Results

- Best Transformer configuration:
  - `72h` context window
  - `Local Positional Encoding`
  - `Focal Loss` with α = `[0.28, 0.36, 0.36]`
  - **Signal Accuracy:** `+1.17` at `12.5%` activity level

- **XGBoost outperformed Transformers** in raw signal accuracy (`+3.70`), but:
  - Transformers offered **lower volatility**, **controlled drawdowns**, and **stable performance** under noisy conditions
  - Indicate potential as **low-risk signal generators** in ensemble frameworks

---

## 🔍 Insights

- **Self-attention layers** successfully capture directional structure, especially with **local temporal priors**
- Performance hinges on **well-calibrated loss functions** to handle class imbalance
- Transformers alone aren't a silver bullet—but contribute **robust, low-risk signal components** to hybrid models

---



