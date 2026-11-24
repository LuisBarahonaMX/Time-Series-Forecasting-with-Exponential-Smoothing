# Time Series Forecasting | Moving Averages and Holt-Winters

### Statistical Forecasting, Exponential Smoothing, and Seasonal Time Series Analysis with Python

**Project Type:** Academic Time Series Forecasting Project  
**Field:** Data Science | Statistical Modeling | Predictive Analytics  
**Programming Language:** Python  
**Environment:** Google Colab | Jupyter Notebook  
**Author:** Data Engineer Luis Barahona

---

## 1. Project Overview

This project explores statistical techniques for analyzing and forecasting time series using Python.

The notebook focuses on understanding how historical observations can be used to estimate future values through moving averages, simple exponential smoothing, and Holt-Winters seasonal forecasting.

Several datasets are examined, including historical sunspot observations, crude oil prices, monthly temperatures, and airline passenger counts.

The final experiment compares additive and multiplicative Holt-Winters models using historical airline passenger data, evaluating their forecasting accuracy on observations from 1960.

The project combines mathematical explanations, practical implementations, statistical visualizations, and quantitative model evaluation.

---

## 2. Project Objectives

- Understand the fundamentals of time series forecasting.
- Apply moving averages to historical observations.
- Explore the influence of moving-average window sizes.
- Implement simple exponential smoothing.
- Analyze how exponential smoothing assigns weights to historical data.
- Identify seasonal patterns in time series.
- Implement Holt-Winters forecasting models.
- Compare additive and multiplicative seasonality.
- Separate historical observations into training and testing periods.
- Evaluate forecast accuracy using MAE and MAPE.
- Visualize actual observations and predicted values.

---

## 3. Forecasting Techniques

### 3.1 Moving Average

The moving average method estimates a future value using the arithmetic mean of the most recent observations.

For a moving average of order k:

```text
Forecast = (x[t] + x[t-1] + ... + x[t-k+1]) / k
```

The notebook introduces this technique through a simple numerical example.

It subsequently applies an 11-observation moving average to historical sunspot data.

The objective is to understand how averaging recent observations can smooth short-term fluctuations.

### 3.2 Simple Exponential Smoothing

Simple Exponential Smoothing assigns progressively smaller weights to older observations.

The method uses a smoothing parameter, alpha, to control how strongly recent observations influence the estimated level.

The notebook explores:

- Exponential weighting.
- Historical observation smoothing.
- Model fitting with Statsmodels.
- Comparison with moving averages.
- Visualization of exponentially decreasing weights.

An example using crude oil prices illustrates the method.

### 3.3 Holt-Winters Exponential Smoothing

Holt-Winters extends exponential smoothing to model seasonal behavior.

The notebook explores seasonal forecasting through monthly temperature observations and airline passenger data.

Two seasonal configurations are considered:

**Additive seasonality**

Appropriate for exploring seasonal fluctuations whose absolute magnitude remains relatively stable.

**Multiplicative seasonality**

Appropriate for exploring seasonal fluctuations whose magnitude changes with the overall level of the series.

Both approaches are evaluated experimentally.

---

## 4. Datasets

The notebook uses several time series.

| Dataset | Description | Application |
|:---|:---|:---|
| Numerical example | Five observations | Moving-average introduction |
| Sunspots | Historical sunspot activity | Moving-average forecasting |
| Crude oil | Historical crude oil prices | Simple exponential smoothing |
| DFW temperatures | Monthly temperature observations | Holt-Winters forecasting |
| AirPassengers | Monthly international airline passengers | Seasonal forecasting comparison |

### External CSV Files

The notebook loads three local datasets:

- `sunspot2.0.csv`
- `wtcrude.csv`
- `dfw_mon.csv`

These files must be available in the execution environment.

The AirPassengers dataset is retrieved through Statsmodels using `get_rdataset()`.

---

## 5. Methodology

### Step 1 — Environment Preparation

The notebook imports the main libraries used for numerical processing and visualization.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

Additional forecasting functions are imported from Statsmodels when required.

### Step 2 — Moving-Average Introduction

A numerical sequence is used to demonstrate how a future observation can be estimated using the mean of recent values.

The example provides a foundation for understanding moving-average forecasts.

### Step 3 — Sunspot Time Series

Historical sunspot observations are loaded from a CSV file.

The notebook:

1. Creates a date index.
2. Visualizes the historical series.
3. Filters observations from 1990 onward.
4. Calculates an 11-observation moving average.
5. Generates a constant forecast based on recent observations.
6. Compares the moving average with historical values.

This experiment illustrates the smoothing effect of the method and its limitations when applied to cyclical time series.

### Step 4 — Exponential Smoothing

A crude oil time series is used to implement Simple Exponential Smoothing.

The model is fitted using Statsmodels.

The notebook compares its fitted values with a four-observation moving average.

### Step 5 — Exponential Weight Analysis

An additional experiment illustrates how the smoothing parameter influences the weight assigned to historical observations.

The example uses:

```python
alpha = 0.7
```

A graph is created to demonstrate the decline in historical weights.

### Step 6 — Seasonal Forecasting

Monthly temperature observations from Dallas–Fort Worth are analyzed.

A Holt-Winters model with additive seasonality and a 12-month seasonal period is fitted to the series.

The notebook generates a 12-month forecast and visualizes the estimated future values.

### Step 7 — Forecasting Model Comparison

The temperature series is divided into training and testing subsets.

The last 12 observations are reserved for testing.

Two forecasting methods are compared visually:

- Simple Exponential Smoothing
- Holt-Winters with additive seasonality

### Step 8 — AirPassengers Forecasting

The final exercise uses the historical AirPassengers dataset.

The data is divided chronologically:

**Training period:** 1949–1959

**Testing period:** 1960

Two Holt-Winters models are fitted using the training data:

1. Additive trend and multiplicative seasonality.
2. Additive trend and additive seasonality.

Both models generate predictions for the 12 months of 1960.

### Step 9 — Model Evaluation

The forecasts are compared with actual observations using:

- Mean Absolute Error (MAE)
- Mean Absolute Percentage Error (MAPE)

The notebook includes graphical comparisons between actual and predicted passenger counts.

---

## 6. Experimental Results

### AirPassengers Forecasting — 1960

The notebook contains the following saved evaluation results:

| Model | MAE | MAPE |
|:---|---:|---:|
| Holt-Winters Multiplicative | **10.30** | **2.21%** |
| Holt-Winters Additive | 13.38 | 2.80% |

### Interpretation

The multiplicative Holt-Winters model achieved lower forecasting errors than the additive model during the 1960 testing period.

Its lower MAE indicates smaller average absolute differences between predicted and observed passenger counts.

Its lower MAPE indicates smaller relative forecasting errors.

These results suggest that multiplicative seasonality better represented the seasonal variation of the AirPassengers series for this experiment.

However, this comparison evaluates a single 12-month test period and does not establish that the multiplicative approach will outperform additive seasonality on every dataset.

---

## 7. Technologies Used

| Technology | Purpose |
|:---|:---|
| Python | Programming language |
| Pandas | Time series manipulation |
| NumPy | Numerical calculations |
| Matplotlib | Data visualization |
| Statsmodels | Statistical forecasting models |
| SimpleExpSmoothing | Simple exponential smoothing |
| ExponentialSmoothing | Holt-Winters modeling |
| Google Colab | Cloud notebook environment |
| Jupyter Notebook | Interactive analysis |

---

## 8. How to Run

### Google Colab

Open the original notebook:

[Run the Time Series Forecasting Notebook](https://colab.research.google.com/drive/1mGyxUzfLW13QP5rHhxMSTMdekd0x0Os0)

### Execution Steps

1. Open the notebook in Google Colab.
2. Prepare the required CSV datasets.
3. Upload the files to the working directory.
4. Execute the notebook cells sequentially.
5. Review the moving-average examples.
6. Examine the exponential smoothing experiments.
7. Compare seasonal forecasts.
8. Review the final MAE and MAPE results.

### Local Execution

Install the required libraries:

```bash
pip install pandas numpy matplotlib statsmodels notebook
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and ensure that its external CSV files are available in the working directory.

The AirPassengers dataset retrieval may require internet access.

---

## 9. Key Findings

The experiments illustrate several important concepts:

**Moving averages**

Moving averages provide a straightforward forecasting approach, but may smooth out meaningful cyclical fluctuations.

**Exponential smoothing**

Simple Exponential Smoothing provides a flexible way to assign greater importance to recent observations.

**Seasonal forecasting**

Holt-Winters extends exponential smoothing by explicitly modeling recurring seasonal patterns.

**Model selection**

The final evaluation demonstrates why forecasting models should be compared using historical observations that were not used for training.

**Seasonality**

The multiplicative Holt-Winters model achieved lower errors than the additive model in the AirPassengers experiment.

---

## 10. Limitations

This project represents an educational application of statistical forecasting.

Important limitations include:

- Some examples require external CSV files.
- The notebook uses several independent datasets.
- The sunspot forecast uses a simple constant moving-average estimate.
- Some model comparisons are visual rather than quantitative.
- The temperature comparison does not include a complete evaluation table.
- The final AirPassengers evaluation covers one 12-month testing period.
- Model performance may vary under different validation periods.
- Advanced forecasting techniques such as SARIMA and Prophet are outside the scope of this notebook.

The reported results should be interpreted within the context of the specific experiments.

---

## 11. Potential Applications

The methods explored in this project can support:

- Sales and demand forecasting.
- Financial time series exploration.
- Temperature and environmental monitoring.
- Transportation demand analysis.
- Operational planning.
- Business intelligence.
- Forecasting model education.

These techniques provide a foundation for more advanced time series forecasting systems.

---

## 12. Future Improvements

Potential extensions include:

- Adding RMSE to the evaluation metrics.
- Implementing rolling-origin temporal validation.
- Comparing different moving-average windows.
- Evaluating alternative smoothing parameters.
- Adding Holt's trend method.
- Expanding the experiments with SARIMA and Prophet.
- Automating dataset loading.
- Creating a unified forecasting comparison dashboard.
- Testing models on additional real-world datasets.

---

## 13. Conclusion

This notebook demonstrates fundamental time series forecasting techniques through mathematical explanations, Python implementations, and practical examples.

The experiments show how moving averages, simple exponential smoothing, and Holt-Winters models can be applied to historical observations.

The final AirPassengers comparison indicates that the multiplicative Holt-Winters model produced lower errors than the additive model during the evaluated period.

Overall, the project provides a practical foundation for understanding statistical forecasting, seasonal patterns, and model evaluation in Data Science.

---

## 14. Project Resources

### Google Colab Notebook

[Open the Original Notebook](https://colab.research.google.com/drive/1mGyxUzfLW13QP5rHhxMSTMdekd0x0Os0)

### Statsmodels Documentation

[Statsmodels — Exponential Smoothing](https://www.statsmodels.org/stable/tsa.html)

### Educational Reference

[Towards Data Science — Time Series Forecasting Article](https://towardsdatascience.com/how-to-effectively-forecast-time-series-with-amazons-new-time-series-forecasting-model-9e04d4ccf67e)

The notebook includes educational explanations and references concerning time series forecasting.

---

## Author

**Data Engineer Luis Barahona**

Mexican Data Engineer and 2026 graduate of Universidad del Caribe, passionate about technology, Data Science, Artificial Intelligence, statistical modeling, and continuous professional development.

---

## Contact

| Platform | Contact |
|:---|:---|
| Email | [190300395@ucaribe.edu.mx](mailto:190300395@ucaribe.edu.mx) |
| GitHub | [github.com/LuisBarahonaMX](https://github.com/LuisBarahonaMX) |
| LinkedIn | [linkedin.com/in/luis-barahona-mx](https://www.linkedin.com/in/luis-barahona-mx/) |
| Instagram | [@luisbarahonamx](https://www.instagram.com/luisbarahonamx/) |
| X | [@luisbarahonaMX](https://x.com/luisbarahonaMX) |
| Website | [SIKO AI Platform](https://sikoai.web.app/) |
