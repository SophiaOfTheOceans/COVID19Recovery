# Forecasting Economic Recovery After COVID-19

## Overview

This project analyzes how pre-pandemic economic conditions and public health policies during the COVID-19 pandemic correlate with post-pandemic economic recovery. Using country-level data, I compare linear and non-linear models to assess whether machine learning approaches better capture recovery dynamics than traditional econometric methods.

The goal is not to build a deployment-ready forecasting system, but to develop an interpretable, data-driven framework for understanding post-crisis recovery patterns across heterogeneous economies.

---

## Data

Two primary data sources were used:

* **World Bank World Development Indicators**: GDP, GDP per capita, and population data (2019–2023)
* **Oxford COVID-19 Government Response Tracker (OxCGRT)**: Country-level policy stringency and intervention measures (2020–2022)

After merging and filtering, the final dataset includes **112 countries** that experienced a GDP decline during the pandemic period.

---

## Problem Framing & Target Definition

Economic recovery is defined as the **percentage of GDP regained by 2023 relative to each country’s pandemic-era GDP decline**:

> Recovery = (GDP_2023 − Minimum_Pandemic_GDP) / (GDP_2019 − Minimum_Pandemic_GDP)

This normalization allows meaningful comparison across countries with vastly different economic scales and baseline GDP levels.

---

## Modeling Approach

Two complementary models were used:

* **Linear Regression**: Used primarily for interpretability and to assess directional relationships between policy measures and recovery outcomes.
* **Random Forest Regression**: Used to capture non-linear interactions and rank the relative importance of predictors.

Predictors included:

* Public health policy measures (e.g., event cancellations, workplace closures)
* Pre-pandemic economic indicators
* Population size and summary policy metrics

---

## Evaluation Strategy

Given the limited sample size (112 countries) relative to the number of predictors, the models were used primarily for **exploratory and explanatory analysis** rather than production-grade prediction.

Evaluation focused on:

* Goodness-of-fit (R², Adjusted R²)
* Stability and consistency of key predictors
* Interpretability vs. flexibility tradeoffs

This approach prioritizes insight into recovery drivers while acknowledging overfitting risks inherent in small-sample, high-dimensional settings.

---

## Key Results

**Model Fit**

| Model             | R²    | Adjusted R² |
| ----------------- | ----- | ----------- |
| Linear Regression | 0.337 | -0.035      |
| Random Forest     | 0.884 | 0.807       |

**Key Findings**

* Random Forest substantially outperformed linear regression in overall fit, reflecting the non-linear nature of recovery dynamics.
* The magnitude of GDP decline during the pandemic was the strongest predictor across both models.
* Policy measures such as public event cancellations and workplace closures consistently ranked among top predictors.

---

## Interpretation & Tradeoffs

Random Forest models captured complex interactions between economic conditions and policy responses but sacrificed interpretability. Linear regression offered clearer directional insights at the cost of explanatory power.

This comparison highlights a common real-world tradeoff in applied data science: **model flexibility vs. interpretability**, particularly in policy-relevant settings.

---

## Limitations

* Observational analysis; results do not imply causality
* Country-level aggregation may obscure within-country heterogeneity
* Results are sensitive to data availability and reporting quality
* Limited sample size constrains validation strategies

---

## Next Steps

* Segment countries by region or economic profile using clustering
* Reformulate recovery as a binary outcome (recovered vs. not recovered)
* Incorporate additional predictors such as healthcare capacity, digital infrastructure, and population density
* Explore rolling-window or scenario-based validation strategies

---

*Detailed methodology, tables, and references are available in the accompanying report and notebooks.*
