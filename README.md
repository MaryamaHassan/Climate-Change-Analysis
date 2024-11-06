---
<img src="https://github.com/user-attachments/assets/46619cdf-c036-4fe2-ae56-a0b09e7617bd" alt="image" width="900" height="250"/>

# Climate Change Temperature Anomaly Analysis

## Overview
This project presents a comprehensive analysis of global temperature anomalies spanning from 1880 to 2024. By examining monthly, seasonal, and annual trends, the study applies statistical models (ARIMA, SARIMA) to explore historical patterns and forecast future temperature shifts. Analyzing these trends alongside historical events reveals how industrialization, conflicts, and policy changes have impacted global temperatures over time. This analysis underscores the continued rise in temperatures driven by greenhouse gas emissions, with projections suggesting further increases without substantial intervention.

## Table of Contents
- [Overview](#overview)
- [Data Collection and Cleaning](#data-collection-and-cleaning)
- [Time Series Decomposition and Differencing](#time-series-decomposition-and-differencing)
- [ACF and PACF Analysis](#acf-and-pacf-analysis-before-and-after-differencing)
- [Monthly Temperature Anomalies](#monthly-temperature-anomalies)
- [Seasonal Temperature Trends](#seasonal-temperature-trends)
- [Correlation with Historical Events](#correlation-with-historical-events)
- [Forecasting Future Trends](#forecasting-future-trends)

## Data Collection and Cleaning
The dataset used in this project originates from the "Tables of Global and Hemispheric Anomalies," containing monthly temperature anomalies from 1880 to the present day. To maintain data accuracy:
- **Missing Values**: Missing values were filled through interpolation based on nearby years rather than default constants, allowing for natural variability.
- **Standardization**: The data was standardized to improve model performance, particularly for time series forecasting.

The resulting cleaned dataset offers a robust foundation for analysis, providing reliable monthly, seasonal, and annual insights into temperature changes.

## Time Series Decomposition and Differencing
To understand the underlying patterns in temperature anomalies, we performed a time series decomposition, breaking down the series into:
- **Trend**: Shows the long-term increase in global temperatures.
- **Seasonal**: Highlights the predictable fluctuations within each year.
- **Residual**: Represents the random noise in the data.

This decomposition reveals a consistent upward trend and cyclical seasonal patterns, underscoring systematic warming over time.

Differencing was applied to stabilize the mean, making the series more stationary. By removing these trends and seasonal effects, the model effectively captures short-term dependencies, enhancing the accuracy of forecasts.

## ACF and PACF Analysis Before and After Differencing
Autocorrelation (ACF) and Partial Autocorrelation (PACF) analyses were conducted both before and after differencing to evaluate temporal dependencies.

- **Before Differencing**:
  - **ACF**: Showed a gradual decline as lag increased, indicating a non-stationary time series with a persistent trend.
  - **PACF**: Displayed significant spikes at early lags, further supporting the presence of a strong trend.
  
  This analysis confirmed that differencing was needed to stabilize the series for effective model fitting.

- **After Differencing**:
  - **ACF**: Displayed a sharp cutoff after a few lags, indicating reduced long-term dependencies and a more stationary series.
  - **PACF**: Showed a quick drop-off, suggesting the data was now suitable for ARIMA and SARIMA modeling.

This differencing step was crucial for improving the interpretability and predictive accuracy of the models.

## Monthly Temperature Anomalies
Monthly anomaly analysis highlights a significant upward trend across all months, with June and December showing notable increases. These findings suggest that summer and winter months are especially affected by climate change:
- **June**: Shows intensifying heat, suggesting that summers are getting hotter.
- **December**: Shows a steady warming, potentially diminishing the traditional seasonal contrasts and resulting in milder winters.

Such monthly patterns reflect the broader impact of global warming, with specific seasonal shifts aligning with long-term climate change trends.

## Seasonal Temperature Trends
The seasonal analysis underscores marked warming in summer and winter, where the temperature anomalies are most pronounced. Winter months show the steepest increase in anomalies, reflecting how the coldest months are warming faster than the rest of the year. This phenomenon is often linked to **Arctic amplification**—the accelerated warming in polar regions. These findings suggest that:
- **Winter warming** could lead to reduced snow cover and ice, impacting habitats and weather patterns.
- **Summer warming** could intensify heat waves and droughts, affecting ecosystems and agriculture.

## Correlation with Historical Events
Historical analysis reveals how industrial activities and global conflicts contributed to rising temperatures:
- **Industrial Revolution (late 1800s - early 1900s)**: Marked the start of significant temperature rises due to fossil fuel use.
- **World War I (1914-1918)**: Brought increased industrial output, introducing more pollutants and contributing to a warming trend.
- **World War II (1939-1945)** and **Post-War Boom**: This period saw heightened emissions as economies rebuilt, spurring substantial industrial growth.
- **Environmental Policies (1970s-present)**: In response to rising pollution and warming, policies emerged to curb emissions. However, data shows that global temperatures have continued to rise, indicating the cumulative impact of past emissions and ongoing challenges in achieving climate stability.

These insights emphasize the long-term consequences of human activity on the climate and underscore the necessity of further action to mitigate emissions.

## Forecasting Future Trends
SARIMA and ARIMA models were employed to forecast future temperature anomalies. Although initial SARIMA models suggested a potential dip, adjustments were made to ensure a continuous upward trend from the last observed data point. Key findings from the forecast:
- **Temperature Rise Continuity**: Forecasts indicate a sustained increase in global temperatures, aligning with scientific reports warning of heightened climate impacts.
- **Urgency for Climate Action**: These projections stress the need for significant climate policies to address the drivers of global warming.

This forecast aligns with warnings from climate science, highlighting the potential for more extreme weather events and ecological disruptions if emissions remain unchecked.

---
