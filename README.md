Stock Price Prediction Engine

📈A machine learning-based forecasting tool designed to predict next-day stock prices by modeling the relationship between independent data metrics and market movements. 
This project was developed as part of the Python Developer Intern (II) 2026 assessment.

📌 Project OverviewThe objective is to forecast $Price_{t+1}$ using data available at $Time_{t}$.
The core architecture relies on the assumption that stock price volatility is primarily driven by the day-over-day change (Delta) in specific independent variables rather than their absolute values.
Core AssumptionsPrimary Influence: Next-day stock prices are modeled as a function of the previous day's data delta.Scope: Focused exclusively on the provided datasets, ignoring external macroeconomic factors to isolate the relationship between the given variables.

🛠️ Technical StackLanguage: Python 3.13
Data Manipulation: Pandas, NumPy
Machine Learning: XGBoost (Gradient Boosted Decision Trees)
Preprocessing: Scikit-Learn (StandardScaler, TimeSeriesSplit)
API Testing: Postman (for RESTful endpoint validation)

🏗️ Model Architecture & Workflow1.
Feature EngineeringFollowing the assignment’s core requirements, the following features were engineered:
  Data Delta ($\Delta$): Calculated as $Data_{t} - Data_{t-1}$ to capture momentum.
  Lagged Price: Included the current day's price to provide the model with a baseline for $t+1$ predictions.
  Target Alignment: Shifted the Price column by $-1$ to align features at $T$ with the label at $T+1$.2. 
  Preprocessing & ScalingTo resolve issues with non-stationary data and varied scales (which initially caused high RMSE):Standardization: Applied StandardScaler to both features ($X$)    and the target ($y$).
  
  This ensures the XGBoost optimizer treats the variance in data delta and absolute price with appropriate weight.3. 
  Training StrategyValidation: Employed TimeSeriesSplit with 5 folds.
  This is critical for financial data to prevent Data Leakage, ensuring the model never "sees" the future during the training phase.
  Algorithm: Selected XGBRegressor for its ability to capture non-linear relationships and its robustness against outliers.

📊 Evaluation Results
The model is evaluated based on its ability to minimize the error between the predicted and actual price.
