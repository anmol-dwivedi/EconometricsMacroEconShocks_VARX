# Macroeconomic Shock Impact Analysis Using VARX

This project models and evaluates the effects of major global shocks—namely the COVID-19 pandemic and the Russia-Ukraine conflict—on key U.S. macroeconomic indicators using a VARX (Vector Autoregression with Exogenous Variables) model.

---

## 📥 1. Data Collection

- **Source:** Publicly available macroeconomic datasets from sources such as FRED, Yahoo Finance, World Bank, IMF, and U.S. Census.
- **Frequency:** Monthly
- **Timeframe:** March 2013 – August 2024
- **Shock Indicators Added:**
  - `Covid_Flag`: 1 for months from March 2020 onward
  - `Russia_Ukraine_Date_Flag`: 1 for months from February 2022 onward

---

## 🧾 2. Data Dictionary

| Variable Name                                | Description                                         |
|---------------------------------------------|-----------------------------------------------------|
| `Trade_Volume_Pct_Change_Index_Value`        | Monthly % change in trade index                    |
| `US_Crude_Oil_Prices_Dollar_Per_Barrel`      | Crude oil prices (USD/barrel)                      |
| `Federal_Rates_Monthly`                      | Effective federal funds rate                       |
| `Nominal_Broad_US_Dollar_Index`              | Nominal broad dollar index                         |
| `Adjusted_Closing_Price`                     | S&P 500 (adjusted)                                 |
| `US_Export_to_Russia`                        | Monthly U.S. exports to Russia                     |
| `US_Unemployment_Rate`                       | U.S. unemployment rate (%)                         |
| `US_Consumer_Sentiment`                      | Michigan consumer sentiment index                  |
| `Price`                                      | CPI proxy                                          |
| `US_Mean_Monthly_Market_Volatility`          | VIX or similar volatility index                    |
| `Average_Hourly_Earning`                     | Avg. hourly earnings in USD                        |
| `CPI_Value_Inflation`                        | Consumer Price Index (Inflation)                   |
| `producer_price_index_all_commodities`       | PPI across commodities                             |
| `Covid_Flag`, `Russia_Ukraine_Date_Flag`     | Binary event dummies (exogenous variables)         |

---

## 📊 3. Exploratory Data Analysis (EDA)

- Time plots and seasonal decomposition to visualize patterns and shocks
- ADF Tests conducted: All variables differenced to ensure stationarity
- Visualization of first/second differencing to confirm transformation adequacy
- Correlation and VIF analysis to detect multicollinearity

---

## 🧠 4. Modeling Steps

### VARX(1) Model
- **Endogenous Variables (13):** Key macroeconomic indicators
- **Exogenous Variables (2):** Pandemic and war dummy flags
- **Lag Order:** Selected using AIC/HQIC → VARX(1)

### Diagnostics Conducted
- Residual Plots
- Ljung-Box Test: Residual autocorrelation
- Jarque-Bera: Normality test on residuals
- ARCH Test: Heteroskedasticity detection
- VIF Scores: All VIF < 2.5 → Multicollinearity not critical

---

## 📈 5. Post-Modeling Analysis

### Impulse Response Analysis
- Traces dynamic response of each macro variable to an exogenous unit shock
- Key finding: COVID has broad systemic effects (esp. on unemployment, trade, stock market)

### Variance Decomposition
- Quantifies each variable’s forecast error explained by itself vs others
- Trade volume, unemployment, inflation mainly explained by their own past values

### Historical Decomposition
- Breaks down variable trajectories into cumulative shocks
- Aligned event overlays show exact COVID and Russia-Ukraine shock impact periods

### Counterfactual Simulation
- Compared actual vs. model-predicted (no-shock) trajectories
- Pandemic introduced sharper deviations than the war, especially in labor and volatility

### Sensitivity Analysis
- Stress-tested the shock intensities (+30%) and reductions (-50%)
- COVID shock shows exponential ripple in unemployment, oil, volatility

---

## 🌍 6. Real-World Insights

- **COVID-19**: Caused demand collapse (lower trade, oil), job losses, and high volatility
- **Russia-Ukraine**: More supply-shock driven (exports, oil, inflation), gradual in impact
- **Policy signals**: Fed responded aggressively during COVID, less so during war
- **Inflation Metrics**: War → cost-push inflation | Pandemic → initial deflation → rebound

---

## ✅ 7. Captures Well

- Directional shifts from global events (trade, oil, unemployment)
- Timely spikes in volatility and inflation metrics
- Policy transmission via interest rate dynamics

## ❌ Not Captured Perfectly

- Stock price recovery dynamics (possibly non-linear rebound)
- Lagged labor market adjustments beyond 1-period lags
- Some residual non-normality and heteroskedasticity remains in PPI, CPI

---

## 🌍 Real-World Insights from the Model

The VARX model provides several critical macroeconomic insights:

1. **COVID-19 as a Dominant Shock**:
   - The impulse response and historical decomposition analysis reveal that COVID-19 introduced sharp volatility in crude oil prices, unemployment rate, and market volatility.
   - Several indicators (e.g., `US_Unemployment_Rate`, `US_Mean_Monthly_Market_Volatility`) show spikes around early 2020, followed by gradual recovery.

2. **Russia-Ukraine Conflict Effects**:
   - While less abrupt than COVID-19, the Russia-Ukraine conflict impacted global trade and crude prices. This is visible in trade volumes and export data.
   - Sensitivity analysis shows increasing shock impact from this conflict affects `Adjusted_Closing_Price` and `Nominal_Broad_US_Dollar_Index` more severely.

3. **Strong Endogenous Relationships**:
   - Lagged variables like `US_Crude_Oil_Prices_Dollar_Per_Barrel` and `Federal_Rates_Monthly` show significant predictive power on other indicators, indicating interconnected economic dynamics.

4. **Lag-Driven Impact**:
   - Lag-1 effects were strong for variables such as `CPI`, `Producer Price Index`, and `Average_Hourly_Earning`, suggesting short-term policy impacts.

5. **What the Model Captures Well**:
   - Direct economic responses to COVID and monetary policies are well modeled.
   - Structural shock response (as seen in impulse and variance decomposition) aligns with historical patterns.

6. **What the Model Misses**:
   - Some long-term dynamics and nonlinear shocks are underrepresented.
   - ARCH test shows heteroskedasticity in some residuals, suggesting potential gains from switching to a VAR-GARCH framework.

These insights are vital for economists, policymakers, and analysts to understand macroeconomic vulnerabilities and resilience to global shocks.

---

## 👨‍💻 Author
Anmol Dwivedi, MS in Business Analytics & AI – The University of Texas at Dallas