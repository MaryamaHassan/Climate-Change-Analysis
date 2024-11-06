---
<img src="https://github.com/user-attachments/assets/46619cdf-c036-4fe2-ae56-a0b09e7617bd" alt="image" width="900" height="250"/>

---
1. **Overview**:
   - Global temperature anomalies analysis (1880-2024).
   - Utilizes ARIMA and SARIMA models to explore past patterns and predict future trends.
   - Highlights the influence of industrialization, conflicts, and policies on temperature changes.
   - Forecasts suggest ongoing warming without significant intervention.

2. **Data Collection and Cleaning**:
   - Dataset from "Tables of Global and Hemispheric Anomalies" containing monthly anomalies.
   - Missing values filled using interpolation, preserving natural variability.
   - Data standardized for improved model performance.

3. **Time Series Decomposition and Differencing**:
   - Time series decomposition into trend, seasonal, and residual components.
   - Differencing applied to stabilize the mean and eliminate trends, enhancing model accuracy.

4. **ACF and PACF Analysis Before and After Differencing**:
   - **Before differencing**: Non-stationary series with persistent trends.
   - **After differencing**: Stationary series with reduced long-term dependencies, suitable for ARIMA/SARIMA models.

5. **Monthly Temperature Anomalies**:
   - Significant warming across all months, especially in June and December.
   - Indicates intensifying summer heat and milder winters.

6. **Seasonal Temperature Trends**:
   - Notable warming in winter and summer months.
   - Winter warming linked to Arctic amplification, affecting snow cover and ice.
   - Summer warming may lead to more extreme heat waves and droughts.

7. **Correlation with Historical Events**:
   - Key periods: Industrial Revolution, World Wars, Post-War Boom, Environmental Policies.
   - Historical events show a strong correlation with rising temperatures due to increased emissions.

8. **Forecasting Future Trends**:
   - SARIMA and ARIMA models predict continued global temperature rise.
   - Projections emphasize the need for urgent climate action to avoid more severe weather events and ecological disruptions.
---
