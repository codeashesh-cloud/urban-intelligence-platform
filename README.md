# urban-intelligence-platform
Urban Intelligence Platform
Urban Air Quality Forecasting Using Time-Series Machine Learning

Project Overview
Urban air pollution poses significant risks to public health and environmental sustainability.
This project focuses on analyzing and forecasting daily Carbon Monoxide (CO) concentrations using historical urban air-quality sensor data.
The objective is to:
- Understand temporal patterns in CO levels
- Engineer meaningful time-series features
- Compare baseline and advanced machine learning models for forecasting
- Build a clean, reusable pipeline suitable for real-world extensions
  
Dataset Description
The dataset is sourced from the UCI Air Quality Dataset, which contains hourly measurements collected from urban monitoring sensors.
Key variables include:
- Carbon Monoxide (CO)
- Nitrogen Oxides (NOx, NO₂)
- Hydrocarbons (NMHC, C₆H₆)
- Temperature, Relative Humidity, Absolute Humidity
- Multiple metal oxide sensor readings
  
Preprocessing details:
- Invalid sensor readings encoded as -200 were replaced with missing values
- Date and time fields were combined into a unified datetime index
- Hourly data was resampled to daily frequency for trend-focused forecasting
  
Methodology
1. Data Cleaning & Preprocessing
- Standardized column names
- Removed invalid sensor values
- Converted all measurements to numeric types
- Created a datetime index for time-series analysis
2. Exploratory Data Analysis (EDA)
- Time-series visualization of CO concentrations
- Distribution analysis (histograms, boxplots)
- Correlation heatmaps to identify multicollinearity
- Identification of volatility, skewness, and extreme pollution events
3. Feature Engineering
- Lag features (lag_1, lag_2, lag_3) to capture short-term persistence
- Rolling statistics:
* 7-day rolling mean
* 7-day rolling standard deviation
* 14-day rolling mean
- Removal of rows with missing values introduced by lagging and rolling windows

Modeling Approach
Two forecasting models were implemented and compared:
1. Baseline Model — Linear Regression
- Used lag-based features
- Provided an interpretable benchmark
- Captured general trends but struggled with sharp fluctuations
2. Enhanced Model — Random Forest Regressor
- Trained using lag and rolling statistical features
- Captured non-linear relationships and temporal interactions
- Demonstrated improved average predictive accuracy

Model Evaluation
Models were evaluated using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).
Model	                      MAE	     RMSE
Linear Regression	          0.51	   0.62
Random Forest	              0.48	   0.63

Key findings:
- Random Forest reduced average prediction error (lower MAE)
- Non-linear features improved responsiveness to temporal variability
- Extreme pollution spikes remain challenging for both models

Feature Importance Insights
Feature importance analysis from the Random Forest model revealed that:
- Recent CO values (lag_1) are the most influential predictors
- Rolling means capture short- and medium-term trends
- Rolling standard deviation provides useful information about volatility
- Older lag features have diminishing influence

These results confirm strong short-term temporal dependence in urban CO levels.
