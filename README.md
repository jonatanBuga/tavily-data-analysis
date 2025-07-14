# tavily-data-analysis

This repository contains two main parts:

---

## Part A: Time Series Analysis & Anomaly Detection  
Location: [part A folder](https://github.com/jonatanBuga/tavily-data-analysis/part A)

1. **EDA (`EDA.ipynb`)**  
   - Load & clean the time-series data (requests per hour, avg response time)  
   - Visualize distributions, trends & correlations  

2. **Anomaly Detection (`Anomaly_Detection.ipynb`)**  
   - Feature engineering: rolling mean/std, z-score, resp_per_logreq  
   - Identify and mark anomalies via static thresholds & z-score  
   - Plot raw vs. rolling stats with anomaly markers  

3. **Forecasting & 2× Load Simulation (`Predicting_resp_time_under_U_growth.ipynb`)**  
   - Train a LinearRegression model with exogenous load (`log_VOLUME`) and time regressors  
   - Forecast future response times on the test set  
   - **Simulate doubled traffic** (2× `VOLUME`) to predict Avg Response under 2× load  
   - Evaluate using R^2, RMSE  
   - Visualize Actual vs. Forecast, distribution under 2× load, and residuals  

4. **Model Comparison (`Comparing_t_s_forecasting_models.ipynb`)**  
   - Build and tune SARIMA and XGBoost regressors  
   - Feature engineering for XGBoost: lags, rolling stats, temporal features  
   - Compare performance (MAE, RMSE, MAPE) side-by-side  
   - Conclude XGBoost outperforms SARIMA on this dataset  

---
## Part B: Usage Dashboard & Insights  
Location: `part B/dashboard_analysis.ipynb`

- **Data Cleaning & KPIs**  
  - Total Crawls, Avg. Response Time, Active API Keys, Error Rate  
  - Time dimensions: day/week/month  

- **Key Visualizations**  
  1. **Weekly Crawls by Extract Depth** – trend of basic vs. advanced usage  
  2. **Avg Response Time (Top Categories)** – monthly lines for top 8 categories  
  3. **Error Rate Analysis**  
     - Daily error-rate time series  
     - Hourly average error-rate bar chart  

- **Main Insights**  
  1. Rapid growth in basic usage, stable but sparse advanced usage  
  2. Sharp response-time spikes in E-Commerce & product/review categories  
  3. Point-in-time error outbreaks mid-April and mid-May  

- **Next Steps**  
  - **Scaling & Caching** for high-load basic crawls  
  - **Performance tuning** for heavy categories  
  - **Alerting** on error-rate thresholds  

---

### How to Explore

1. **Clone the repo**  
   ```bash
   git clone https://github.com/jonatanBuga/tavily-data-analysis.git
   cd tavily-data-analysis
   ׳׳׳
2. Part A
    Open and run each notebook in part A/ in order:

    EDA → 2. Anomaly Detection → 3. Forecasting & 2× Load Simulation → 4. Model Comparison
3. Part B
    Open part B/dashboard_analysis.ipynb to see dashboard creation, KPIs, charts, and insights