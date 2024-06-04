---
quickshare-date: 2024-05-28 00:02:43
quickshare-url: "https://noteshare.space/note/clwp7viyv2318101mwk2k0b3kd#m5w/CUiFUv26JfX7Gxx1vyHZOnQYI43DJRAwJIwopZU"
---
> _A time series is a sequence of data points collected or recorded at successive points in time, often at uniform intervals. It is used to analyze trends, patterns, and cycles over time in various fields like economics, weather forecasting, and signal processing._
![](https://i.imgur.com/UeyCbb7.png)
# I. Components
> _Components of time series data refer to the different factors that contribute to its overall structure, such as [[ #1 . Trend | trends]], [[#2. Seasonality | seasonality]], and [[ #4 . Irregular Components | irregular variations]], which distinguish it from other time-dependent data analyses._ ![](https://i.imgur.com/LgRDLTy.png)

By identifying these patterns in time series data, analysts can better understand the underlying structure and make more accurate forecasts.
## 1. Trend
> _A long-term upward or downward movement in the data, indicating a general increase or decrease over time._ ![](https://i.imgur.com/lI5UjoX.png)

- Represents the underlying structure of the data, capturing the direction and magnitude of change over a longer period. 
- Usually to model and remove the trend from the data to better understand the underlying patterns and make more accurate forecasts.
### Upward Trend
> _A trend that shows a general increase over time, where the values of the data tend to rise over time._
### Downward Trend
> _A trend that shows a general decrease over time, where the values of the data tend to decrease over time._
### Horizontal Trend
> _A trend that shows no significant change over time, where the values of the data remain constant over time._
### Non-linear Trend
> _A trend that shows a more complex pattern of change over time, including upward or downward trends that change direction or magnitude over time._
### Damped Trend
>_A trend that shows a gradual decline in the magnitude of change over time, where the rate of change slows down over time._
## 2. Seasonality
> _A repeating pattern in the data that occurs at regular intervals, such as daily, weekly, monthly, or yearly._ 
> ![](https://i.imgur.com/sOPU2hf.png)
### Additive Seasonality
-  $$y(t) = Mean + Trend + Seasonality + Noise$$
- The behavior is linear where changes over time are consistently made by the same amount, like a linear trend. 
- In this situation, the linear seasonality ***has the same amplitude and frequency.***
### Multiplicative Seasonality
-  $$y(t) = Mean * Trend * Seasonality * Noise$$
- Not linear, can be exponential or quadratic
- Has an increasing or decreasing amplitude and/or frequency over time.
### Additive or multiplicative?
> _We use **multiplicative** models when the magnitude of the seasonal pattern in the data depends on the magnitude of the data. On other hand, in the **additive** model, the magnitude of seasonality does not change in relation to time._
## 3. Stationarity
## 4. Cyclic Patterns
> _A pattern in the data that repeats itself after a specific number of observations, which is not necessarily related to seasonality._
### Business Cycles
### Economic Cycles
## 5. Irregular Components
> _Random fluctuations in the data that cannot be easily explained by trend, seasonality, or cycle._
### Outliers
### Noise
### Autocorrelation
# II. Method of Analysis
## 1. Descriptive Statistics
## 2. Decomposition
## 3. Smoothing Techniques
## 4. Autoregressive Models
## 5. Spectral Analysis
# III. Applications
## 1. Finace
## 2. Economics
## 3. Engineering
## 4. Environmental Science
# IV. Data Collection
## 1. Sampling Methods
## 2. Data Sources
## 3. Data Storage
# V. Visualization
## 1. Line Charts
## 2. Bar Charts
## 3. Heatmaps
## 4. Advanced Techniques
# VI. Software and Tools
## 1. Programming Languages
## 2. Libraries and Packages
## 3. Visualization Tools
# VII. Preprocesing
## 1. Normalization
## 2. Differencing
## 3. Transformation
# VIII. Model Evaluation
## 1. Error Metrics
## 2. Cross-validation
## 3. Residual Analysis
# IX. Advanced Topics
## 1. [[Machine learning]]
## 2. Transfer Learning
## 3. Hybrid Models