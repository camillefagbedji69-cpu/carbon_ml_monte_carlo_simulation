# Carbon Prediction & Resilience Evaluation via Monte Carlo Simulation

## 📌 Context

Following my [previous research](https://github.com/camillefagbedji69-cpu/carbon_ml_without_lulc), this project aims to quantify the **ecological resilience** of carbon stocks. Beyond mere prediction, this study uses a stochastic approach to evaluate how spatial units respond to extreme environmental variations.

## ⚙️ Methodology

* **Data & Features**: Includes Tree Proportion (`tree_prop`), NDVI, NDWI, LST, and Precipitation.
* **Spatial Validation**: Implementation of **Spatial K-Fold** cross-validation to prevent data leakage due to spatial autocorrelation.
* **Predictive Modeling**: Comparison of four architectures: Linear Regression, Random Forest, XGBoost, and Gradient Boosting.
* **Monte Carlo Simulation (Resilience Stress-Test)**:
* **Iterations**: 10,000 simulations.
* **Perturbation**: $\pm 20\%$ variation applied to the top 3 drivers identified by SHAP.
* **Vulnerability Index ($V$)**: Calculated as the relative loss between the baseline and the simulated scenario:

$$V = \frac{Y_{baseline} - Y_{simulated}}{Y_{baseline}}$$


* **Pessimistic Scenario**: Selection of the **10th percentile** of results to model high-stress conditions.
* **Resilience Index**: Normalization (0 to 1) of the vulnerability to map the capacity of each unit to maintain its carbon stock.

## 📊 Results

### 1. Model Performance

The tree-based models (RF and XGBoost) demonstrate superior performance, capturing the complex non-linearities of the ecosystem.

| Models | $R^2$ | RMSE (tC/ha) |
| --- | --- | --- |
| **Random Forest** | **0.75** | **196.63** |
| **XGBoost** | **0.75** | **199.32** |
| Gradient Boosting | 0.64 | 237.65 |
| Linear Regression | 0.40 | 306.29 |

### 2. Sensitivity Analysis (SHAP)

The importance ranking reveals that physical structure (`tree_prop`) and water availability remain the primary controllers of the system.

| Variables | Mean SHAP Value (Absolute) |
| --- | --- |
| **Tree Proportion** | **187.04** |
| **Precipitation** | **56.99** |
| **NDWI** | **49.96** |
| LST | 7.47 |
| NDVI | 6.63 |

### 3. Resilience Assessment

The normalized resilience index (Mean: 0.38) indicates that under a pessimistic scenario (10th percentile), most spatial units face significant vulnerability.

* **High Resilience (1.0)**: Units capable of maintaining carbon stocks despite climate fluctuations.
* **Low Resilience (0.0)**: Units highly sensitive to changes in tree cover and rainfall.

## 🚀 Perspectives & "AI for Science" Impact

1. **Decision Support**: This index allows for the prioritization of conservation zones based on their stability, not just their current stock.
2. **Climate Risk Mapping**: Moving from static maps to dynamic "risk-aware" dashboards for Beninese forest management.
3. **Stochastic Forecasting**: Integration of Monte Carlo methods to provide confidence intervals for carbon credit markets.
