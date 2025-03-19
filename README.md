# wise-fintech

## Project Objective

This project aims to create a comprehensive machine learning platform to assist the FP&A team in forecasting key financial metrics at a cross-border payments company like Wise. In particular, I hope that this model aids in scenario planning, "what-if" analyses and sensitivity analyses based on previous years' revenue, expenses, cash flow, margins, etc. Beyond strategic decision making, this model aims to aid operational efficiency by delving into unit economics optimisation, incl. LTV:CAC ratios, churn rates, adoption rates, etc. Furthermore, given Wise's moat in facilitating instant transfers at a low cost through its unique P2P pooled bank account network as opposed to traditional reliance on the SWIFT system, this model aims to explore corridor-specific insights, FX spread efficiencies as well as the % of sub-20s transactions to guide expansion. Finally, the model provides transparency into forecast drivers through feature importance analysis and confidence intervals.

## Tech Stack

* Python: Core forecasting engine with scikit-learn, statsmodels, and XGBoost
* Pandas/NumPy: Data manipulation and preprocessing
* React.js: Interactive dashboard with Recharts for visualization
* Tailwind CSS: Dashboard styling and responsive design
* CSV Data Pipeline: For loading and processing historical data
  
Time Series Algorithms:

* ARIMA/SARIMA for traditional time series forecasting
* Random Forest for multivariate prediction
* XGBoost for complex feature interactions
* Exponential Smoothing for trend/seasonality handling

## Key Features

* __Algorithm Competition__: Automatic selection of the best forecasting method for each metric
* __Monte Carlo Simulations__: Probabilistic forecasts with confidence intervals
* __Scenario Analysis__: Base, optimistic, and pessimistic projections.
* __Feature Importance Visualization__: Identification of key revenue drivers
* __Corridor Analysis__: Currency-pair specific volume forecasting
* __Unit Economics Projections__: LTV:CAC ratio forecasting
* __Interactive Dashboard__: Executive-friendly visualization and filtering. 

## Feature Importance Determination

The feature importance is calculated using a combination of methods:

* __Tree-based Feature Importance__: For Random Forest and XGBoost models, we extract the native feature importance scores, which measure how frequently each feature is used in decision splits, weighted by the improvement in the split criterion.
* __Permutation Importance__: For all models, we implement permutation importance where each feature's values are randomly shuffled and the resulting decrease in model accuracy is measured. Larger decreases indicate more important features.
* __SHAP Values__: For complex interactions, Shapley Additive Explanations help understand the contribution of each feature to individual predictions and overall model behavior.

The dashboard visualizes these importance scores to help stakeholders understand which factors most strongly influence financial outcomes, such as transaction volume, marketing spend, and seasonal patterns.

## Forecasting Methodology
The system employs a two-stage process:

* __Model Competition__: Multiple algorithms are trained and evaluated on historical data
* __Ensemble Approach__: The best-performing models are combined for different metrics
* __Feature Engineering__: Time-based features, lag variables, and moving averages enhance accuracy
* __Confidence Calculation__: Bootstrap resampling generates prediction intervals

## Unit Economics Modeling
The LTV calculation incorporates:

* Cohort-based retention curves
* Time-discounted revenue projections
* Customer lifecycle modeling
* Acquisition channel efficiency

## Getting Started
To use this platform:

1. Install required dependencies (pandas, scikit-learn, statsmodels, xgboost)
2. Load your financial data as CSV (minimum requirements: date column, revenue metrics)
3. Initialize the forecaster: `forecaster = FinTechForecaster()`
4. Train models: `forecaster.forecasting_competition("Revenue")`
5. Generate forecasts: `future_revenue = forecaster.forecast_future("Revenue", periods=12)`

## File Descriptions

## 1. fintech-forecaster

* Created a Python class-based forecasting system (fintech-forecaster) for predicting financial metrics
* Implemented multiple algorithms: ARIMA, SARIMA, Random Forest, XGBoost, and Exponential Smoothing
* Built automatic model competition to select the most accurate algorithm for each metric
* Added Monte Carlo simulations for risk assessment and confidence intervals
* Implemented scenario analysis (base, optimistic, pessimistic cases)

## 2. wise-metrics-adapter

* Developed a specialized adapter (wise-metrics-adapter) for cross-border payment metrics
* Added support for currency corridor volume forecasting
* Implemented take rate and transfer margin projections
* Added multi-currency account and interest income modeling
* Created comprehensive unit economics analytics (LTV:CAC ratio)

## 3. sample-data-csv

* Generated realistic fintech data covering 2020-2023 (48 months)
* Created CSV data with 40+ financial metrics
* Included realistic patterns like declining fee percentages, improving unit economics, and seasonal patterns
* Generated sample forecast data with confidence intervals

## 4. metrics-dashboard

* Built a React-based strategic dashboard for visualizing forecasts
* Included ML model insights showing feature importance and model accuracy
* Added scenario analysis visualization with toggleable confidence intervals
* Created interactive controls for different time ranges and forecast scenarios
* Implemented five view modes: Overview, Forecasts, ML Insights, Customers, and Unit Economics


###### The system is designed to load either generated sample data or your own CSV data with minimal formatting requirements. The forecasting models handle seasonality, trend detection, and provide probabilistic outputs for business planning.
