# Wildfire Fuel Moisture Analysis

This project analyzes how **meteorological conditions and climate regimes** influence **1000-hour dead fuel moisture content (fm1000)**, a key driver of wildfire ignition risk and fire behavior.

Using a large-scale spatiotemporal wildfire dataset, the analysis examines how temperature, precipitation, vapor pressure deficit, solar radiation, wind speed, seasonal patterns, climate zones, and prior wildfire activity jointly affect fuel moisture levels prior to wildfire ignition.

---

## Motivation

Fuel moisture content responds slowly to environmental change and plays a critical role in determining wildfire spread, intensity, and suppression difficulty. Understanding the environmental drivers of long-term fuel moisture enables improved **early warning systems**, **risk assessment**, and **resource planning** for wildfire mitigation.

This project focuses on identifying both **direct effects** and **interaction effects** between meteorological variables and climate regimes to capture how fuel moisture dynamics vary across space and seasonality.

---

## Methods

### Exploratory Analysis
- Distributional analysis of fuel moisture and meteorological predictors
- Boxplots by climate zone and season
- Correlation and pairwise relationship analysis
- Identification of skewness, multicollinearity, and potential nonlinear effects

### Modeling
- Multiple linear regression with interaction terms
- Climate-specific effects for temperature and precipitation
- Seasonal interactions with solar radiation
- Nonlinear transformation of vapor pressure deficit
- Inclusion of prior wildfire activity as a historical disturbance factor

### Model Evaluation
- Residual diagnostics and assumption checking
- Comparison of preliminary and transformed models
- 10-fold cross-validation to assess generalization performance

---

## Final Model

The final model is specified as:
- m12 <- lm(log(fm1000) ~ (tmmn + tmmx + pr) * cli + srad * season + sqrt(vpd) + vs + p, data = wf_data_e)

This specification allows environmental drivers of fuel moisture to vary across climate regimes and seasonal conditions.

---

## Key Findings

- Temperature, vapor pressure deficit, and solar radiation are the strongest drivers of fuel moisture variability.
- Climate zones significantly modify the effects of temperature and precipitation on fm1000.
- Seasonal interactions with solar radiation capture meaningful temporal variation.
- The transformed model improves residual behavior and generalization compared to untransformed alternatives.


