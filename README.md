---

# Climate Change Analysis

This project explores global temperature anomalies over time, leveraging the 'Tables of Global and Hemispheric' dataset. By applying various statistical and machine learning models, such as ARIMA and SARIMAX, and visualising the results, this analysis aims to reveal long-term trends in global warming, predict future patterns, and highlight correlations across monthly and seasonal temperature data. The findings align with NASA's Global Climate Change data, providing additional support to the accuracy of our insights.

## Dataset Overview

The dataset encompasses global and hemispheric temperature anomalies from 1880 to 2024. It details temperature deviations from a long-term global average, presented in both monthly and seasonal terms, with seasons defined as follows:
- **Winter (DJF)**: December, January, February
- **Spring (MAM)**: March, April, May
- **Summer (JJA)**: June, July, August
- **Autumn (SON)**: September, October, November

As a point of comparison, NASA’s GISS Surface Temperature Analysis reveals a global temperature increase of approximately 1.1°C since the late 19th century, corroborating the general upward trend observed in this analysis. This consistent data serves as a foundation for interpreting temperature anomalies over time.

## Data Cleaning and Preprocessing

The initial dataset contained missing values, identified by examining a heatmap:
```python
plt.figure(figsize=(12, 6)) 
sns.heatmap(df.isnull(), cbar=False, cmap='Greens')
plt.title('Missing Data Heatmap')
plt.tight_layout()
plt.show()
```

To handle the missing values, we employed interpolation and median imputation:
```python
df_inter = df.interpolate()
df_inter['D-N'].fillna(df_inter['D-N'].median(), inplace=True)
df_inter['DJF'].fillna(df_inter['DJF'].median(), inplace=True)
```
This approach maintains the dataset’s integrity, preserving trends while reducing potential bias from outliers.

## Exploratory Data Analysis (EDA)

### 1. Decadal Temperature Trends
By calculating the average yearly temperature anomalies per decade, we can observe an overall increase over time:
```python
df_inter['Decade'] = (df_inter['Year'] // 10) * 10
decade_avg = df_inter.groupby('Decade')['J-D'].mean().reset_index()
```
The plot below showcases average temperature anomalies by decade:
```python
plt.figure(figsize=(8, 4))
sns.lineplot(x='Decade', y='J-D', data=decade_avg, marker='o', color='lightseagreen', label='Global')
plt.title('Average Yearly Temperature Anomaly by Decade')
plt.xlabel('Decade')
plt.ylabel('Temperature Anomaly (°C)')
plt.grid(True)
plt.tight_layout()
plt.show()
```

### 2. Monthly and Seasonal Temperature Anomalies
Monthly anomalies reveal that January, June, and December have shown significant increases, especially in recent decades:
```python
plt.figure(figsize=(10, 6))
plt.plot(df_inter['Year'], df_inter['Jan'], label='January', color='limegreen')
plt.title('January Temperature Anomaly (°C)')
plt.xlabel('Year')
plt.ylabel('Temperature Anomaly (°C)')
plt.axhline(0, color='red', linewidth=0.5, linestyle='--')
plt.legend()
plt.grid(True)
plt.show()
```
Similar plots for June, December, and seasonal data (Winter, Spring, Summer, Autumn) indicate significant rises across all months and seasons.

### 3. Correlation Analysis
A correlation matrix highlights relationships across months and seasons, showing high correlations between adjacent periods, which reflect a synchronised warming trend.
```python
plt.figure(figsize=(10, 6))
corr = df_temp.corr()
sns.heatmap(corr, annot=True, cmap='RdYlGn', linewidths=0.5)
plt.title('Correlation between the Months')
plt.tight_layout()
plt.show()
```

## Linking Historical Events to Temperature Anomalies

Historical milestones and temperature increases often coincide:
- **1926**: A major spike in temperature anomalies above the historical average coincided with severe flooding in British Malaya. Increased industrialisation and environmental changes contributed to this rise.
- **World War II (1939-1945)**: The war and post-war industrial boom led to an unprecedented spike in CO₂ emissions. This era saw heightened industrialisation and energy consumption, accelerating climate change.
- **1970s-1980s Oil Crisis**: Oil shortages triggered shifts towards alternative energy sources. However, emissions continued, leading to persistent temperature increases in subsequent years.

## Time Series Analysis

The time series modelling segment uses ARIMA and SARIMA models to understand temperature anomaly trends and project future changes.

### Stationarity Testing
```python
result = adfuller(global_series)
print('ADF Statistic:', result[0])
print('p-value:', result[1])
```
If the p-value is above 0.05, the series is non-stationary and requires differencing. Further differencing and seasonal decomposition are applied for seasonality and trend analysis.

### SARIMA Modelling
We used auto_arima for optimal parameters and fitted SARIMA models on global and winter anomalies, adjusting forecasts for continuity:
```python
model_JD = SARIMAX(global_series, order=(1, 0, 3), seasonal_order=(0, 0, 2, 12), trend='t')
result_JD = model_JD.fit()
forecast_JD = result_JD.get_forecast(steps=forecast_periods)
```

The forecasts, adjusted to align with observed trends, show that both global and winter temperature anomalies continue to rise. This aligns with NASA's projections of ongoing global warming.

### Forecast Visualisation
The final visualisation compares observed data with forecasted trends for both global and winter anomalies:
```python
plt.figure(figsize=(12, 8))
# Global (J-D) Plot
plt.subplot(2, 1, 1)
plt.plot(global_series.index.to_timestamp(), global_series, label='Observed (J-D)', color='orange')
plt.plot(forecast_index_JD, predicted_mean_JD, label='Forecast (J-D)', color='purple')
plt.fill_between(forecast_index_JD, conf_int_JD.iloc[:, 0], conf_int_JD.iloc[:, 1], color='moccasin', alpha=0.3)
plt.title('SARIMA Forecast for Global Temperature Anomalies (J-D)')
plt.xlabel('Year')
plt.ylabel('Temperature Anomaly (°C)')
plt.legend()
plt.grid()
plt.subplot(2, 1, 2)
plt.plot(global_series_winter.index.to_timestamp(), global_series_winter, label='Observed (D-N)', color='purple')
plt.plot(forecast_index_DN, predicted_mean_DN, label='Forecast (D-N)', color='orange')
plt.fill_between(forecast_index_DN, conf_int_DN.iloc[:, 0], conf_int_DN.iloc[:, 1], color='plum', alpha=0.3)
plt.title('SARIMA Forecast for Global Temperature Anomalies (D-N)')
plt.xlabel('Year')
plt.ylabel('Temperature Anomaly (°C)')
plt.legend()
plt.tight_layout()
plt.show()
```

## Conclusion

The analysis confirms a sustained increase in global temperature anomalies, with a pronounced warming trend across all months and seasons since 1880. Monthly and seasonal correlations demonstrate that warming is globally synchronised, affecting all parts of the year. The SARIMA forecasts indicate that this trend is likely to continue in the near future, underscoring the urgency for climate action. Historical events have contributed significantly to these trends, and future projections align with predictions by leading climate research organisations, such as NASA and the IPCC.

This project has successfully demonstrated the use of statistical and machine learning models in analysing climate change, contributing to the broader understanding of global warming and its long-term effects.
