# 💄 Forecasting Lipstick Sales Using Prophet

_A case study by Anu Haridas, Foretara_

This project tests the effectiveness of Prophet in modeling SKU-level sales for a hypothetical lipstick line.  
We explore time series forecasting with logistic growth, marketing campaign impact (regressor), and changepoint sensitivity.

---
## 🎯 Problem Statement

A cosmetic brand wants to forecast sales of a lipstick SKU, factoring in marketing campaigns and growth saturation.

We simulate 2 years of monthly sales data with:
- A gradually increasing trend
- Noise to mimic real-world fluctuation
- A marketing campaign introduced after 24 months

---

## 📊 Dataset Summary

- **Frequency**: Monthly (MS)
- **Period**: Jan 2023 – Dec 2024 (24 months actual + 6 months future)
- **Regressor**: `launch_campaign_intensity`
- **Cap**: 5000 units (logistic ceiling)

---

---

## 📦 What’s Inside

| Folder | Description |
|--------|-------------|
| `notebooks/` | Jupyter/Colab notebooks with Prophet experiments (logistic growth, regressors, changepoint tuning, cross-validation) |
| `research/` | Markdown summaries and experiment logs |
| `data/` | Sample or synthetic datasets used in analysis |
| `outputs/` | Plots, metrics, and backtest result visualizations |

---
## 🧠 Prophet Model Configuration

### 🔧 Key Settings:
- `growth='logistic'` → to simulate sales saturation
- `cap=5000` → upper sales limit
- Custom regressor: `launch_campaign_intensity`
- Cross-validation:
  - Initial: 450 days
  - Horizon: 90 days
  - Period: 90 days

---

## 📈 Current Focus

- Forecasting SKU-level lipstick sales using Prophet  
- Evaluating accuracy across forecast horizons (29d, 60d, 90d)  
- Custom regressors (e.g., campaign intensity)  
- Backtesting + visual vs metric comparisons  
- Clean documentation for reproducibility
## 🧪 Experiments

### ✅ 1. Logistic Growth with Regressor
- Captured baseline trend + campaign-driven shifts

### ✅ 2. Backtesting via Cross-Validation
- Forecast horizon sliced into 29d, 60d, 90d
- Best performance observed at **29d horizon**

### ✅ 3. Changepoint Prior Scale Sensitivity
Tested 3 values:
| Value | Behavior | Visual Fit |
|-------|----------|------------|
| 0.01  | Very rigid, ignores campaign | Under-forecasting |
| 0.1   | Balanced | Mild reaction |
| 0.5   | Highly sensitive | Fast upward shift |

*Observation:* In this case, **all 3 forecasts looked visually similar**, suggesting the campaign signal wasn't strong enough to sharply change trend.

---
## ✅ Key Learnings

- Prophet is **highly configurable** for SKU-level forecasting
- Regressors help simulate business reality (e.g., campaigns)
- Short forecast horizons (e.g., 30 days) are more reliable for this SKU
- Changepoint sensitivity is critical — but not always visually obvious

---

## 🔄 Next Steps

- Add seasonality and holiday impact to capture real-world patterns
- Use real data from SME clients in India or Canada
- Begin testing multi-SKU pipelines (batch forecasts)

---

---

## 👩‍💻 Author

Anu Haridas  
Founder – Foretara  
_Mission: To simplify and democratize forecasting for small and medium businesses across India and Canada_

