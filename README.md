# 🌍 Carbon Prediction & Resilience Evaluation

### *Quantifying Ecological Stability via Monte Carlo Simulations & Explainable AI*

## 📌 Overview

Building upon [previous research](https://github.com/camillefagbedji69-cpu/carbon_ml_without_lulc), this project moves beyond static carbon stock prediction. We introduce a **stochastic stress-test framework** to evaluate how spatial units respond to extreme environmental perturbations, providing a robust metric for **Ecological Resilience**.

## ⚙️ Methodology & Framework

### 1. Data Integration

* **Biophysical Drivers**: Tree Proportion (`tree_prop`), NDVI, NDWI.
* **Climatic Variables**: Land Surface Temperature (LST) and Precipitation.
* **Spatial Integrity**: Implementation of **Spatial K-Fold** cross-validation to mitigate data leakage caused by spatial autocorrelation.

### 2. Resilience Stress-Test (Monte Carlo)

To simulate ecosystem vulnerability, we perform 10,000 iterations applying a $\pm 20\%$ perturbation to the top 3 drivers identified by **SHAP**.

* **Vulnerability Index ($V$)**:

$$V = \frac{Y_{baseline} - Y_{simulated}}{Y_{baseline}}$$


* **Resilience Index ($R$)**:

$$R = 1 - V$$


* **Risk Modeling**: Selection of the **10th percentile** (pessimistic scenario) to map the minimum guaranteed capacity of units to maintain carbon stocks.

## 📊 Benchmark & Insights

### Model Performance

Tree-based architectures significantly outperform linear models in capturing non-linear ecosystem dynamics.

| Model | $R^2$ | RMSE (tC/ha) |
| --- | --- | --- |
| **Random Forest** | **0.75** | **196.63** |
| **XGBoost** | **0.75** | **199.32** |
| Gradient Boosting | 0.64 | 237.65 |
| Linear Regression | 0.40 | 306.29 |

### Sensitivity Analysis (SHAP)

The ranking confirms that physical structure and water availability are the primary regulators of carbon stability.

| Variable | Mean SHAP (Absolute) | Impact Role |
| --- | --- | --- |
| **Tree Proportion** | **187.04** | Structural Baseline |
| **Precipitation** | **56.99** | Climatic Driver |
| **NDWI** | **49.96** | Hydrological Health |

## 🚀 "AI for Science" & Policy Impact

* **Strategic Conservation**: Prioritizing zones based on **stability** rather than just current biomass.
* **Risk-Aware Dashboards**: Transitioning from static maps to dynamic tools for forest management in Benin.
* **Carbon Markets**: Providing confidence intervals and "stress-tested" data for more reliable carbon credit valuation.
