# Tesla Stock Price Analysis & Moving Average Prediction

## Project Overview

This project analyzes historical Tesla (TSLA) stock price data and uses a 5-day moving average to predict closing prices. The project focuses on exploring stock price trends, visualizing the data, evaluating predictions, and understanding how data leakage can affect the accuracy of a time series model.

## Project Objectives

* Analyze historical Tesla stock price data
* Explore the distribution and trends of closing prices
* Create visualizations to better understand the data
* Build a 5-day moving average prediction model
* Identify and correct data leakage
* Compare actual and predicted closing prices
* Evaluate model performance using different metrics

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook / Google Colab

## Data Analysis

The dataset contains historical Tesla stock market data. The `Date` column was converted into datetime format and used as the index to make it easier to analyze changes in Tesla's stock price over time.

Exploratory analysis was performed using summary statistics and several visualizations, including:

* Historical closing price trends
* Closing price histogram
* Kernel Density Estimate (KDE)
* Cumulative Distribution Function (CDF)

These visualizations helped show how Tesla's closing price was distributed and how it changed throughout the dataset.

## Moving Average Prediction

A 5-day moving average was used as a simple method for predicting Tesla's closing price.

An important part of the project was identifying **data leakage**. If the current day's closing price is included when calculating its prediction, the model is using information that would not actually be available at prediction time.

To prevent this, the closing price was shifted by one day before calculating the moving average:

```python
df['5_day_MA_correct'] = df['Close'].shift(1).rolling(window=5).mean()
```

This means each prediction is calculated using only previous closing prices rather than information from the day being predicted.

## Model Evaluation

The predicted values were compared with the actual Tesla closing prices using several evaluation metrics:

* **R² (R-squared):** Measures how well the predicted values explain changes in the actual closing prices.
* **MAE (Mean Absolute Error):** Measures the average difference between the predicted and actual prices.
* **MAPE (Mean Absolute Percentage Error):** Measures the average prediction error as a percentage.
* **Bias:** Helps determine whether the predictions generally overestimate or underestimate the actual price.

A scatterplot of actual vs. predicted prices was also used to visually evaluate the model's performance.

## Key Takeaways

One of the biggest takeaways from this project was learning how important it is to prevent data leakage in time series analysis. A model may initially appear highly accurate when it uses information from the same day it is trying to predict.

By shifting the closing prices before calculating the moving average, the model provides a more realistic prediction based only on information that would have already been available.

This project also provided experience with data cleaning, time series analysis, visualization, prediction, and model evaluation using Python.

## Repository Structure

```text
tesla-stock-moving-average-analysis/
│
├── README.md
│
├── Tesla_Stock_Moving_Average_Analysis.ipynb
│
└── data/
    └── tesla_stock_data.csv
```

## Skills Demonstrated

* Python Programming
* Data Cleaning
* Exploratory Data Analysis
* Time Series Analysis
* Data Visualization
* Moving Averages
* Predictive Modeling
* Model Evaluation
* Data Leakage Prevention

## Author

**Sharah Ahmed**

B.S. Business Data Analytics
University of Connecticut
