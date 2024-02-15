<p align="center">
    <h1 align="center">Stock Price Forecasting and Model Comparison</h1>
</p>
<p align="center">
    <em><code>Trading today with tomorrow's signals</code></em>
</p>
<p align="center">
	<img src="https://img.shields.io/github/last-commit/smruthig/Stock-Price-Forecasting-and-Model-Comparison?style=flat&logo=git&logoColor=white&color=0080ff" alt="last-commit">
	<img src="https://img.shields.io/github/languages/top/smruthig/Stock-Price-Forecasting-and-Model-Comparison?style=flat&color=0080ff" alt="repo-top-language">
	<img src="https://img.shields.io/github/languages/count/smruthig/Stock-Price-Forecasting-and-Model-Comparison?style=flat&color=0080ff" alt="repo-language-count">
<p>
<p align="center">
		<em>Developed with the software and tools below.</em>
</p>
<p align="center">
	<img src="https://img.shields.io/badge/scikitlearn-F7931E.svg?style=flat&logo=scikit-learn&logoColor=white" alt="scikitlearn">
	<img src="https://img.shields.io/badge/Jupyter-F37626.svg?style=flat&logo=Jupyter&logoColor=white" alt="Jupyter">
	<img src="https://img.shields.io/badge/SciPy-8CAAE6.svg?style=flat&logo=SciPy&logoColor=white" alt="SciPy">
	<img src="https://img.shields.io/badge/pandas-150458.svg?style=flat&logo=pandas&logoColor=white" alt="pandas">
	<img src="https://img.shields.io/badge/NumPy-013243.svg?style=flat&logo=NumPy&logoColor=white" alt="NumPy">
</p>
<hr>

##  Quick Links

> - [ Overview](#overview)
> - [ Results](#results)
> - [ Analysis](#analysis)
> - [ Repository Structure](#repository-structure)

---

##  Overview

The goal of this project was to predict the closing stock price of the fictional company Waystar Royco (WAYA US) from July 30, 2021, to September 10, 2021. Historical stock price data from August 14, 2015, to July 29, 2021, was provided, including opening price, high price, low price, closing price, and trading volume for each day.

The task was to use regression and time series modeling techniques to make predictions, compare the models, and determine which is best suited for this type of stock price forecasting. Disclaimer that Waystar Royco is a fictional company, so external factors beyond the provided data should not be considered.

Original Data for the project:
[https://www.kaggle.com/competitions/ue19cs312-assignment/data](https://www.kaggle.com/competitions/ue19cs312-assignment/data)


---

## Results

- Data exploration showed no null values or significant outliers. Features were highly correlated.
- Tried PCA for dimensionality reduction but 2 components explained all variability so it was not needed.
- Scaled and normalized data before modeling.
- Regression models tried: Linear Regression, Ridge, Lasso, Kernel Ridge, KNN. Linear Regression performed best.
- Time series models tried: ARIMA, SARIMAX, Holt-Winters. SARIMAX gave the lowest RMSE.
- Best SARIMAX parameters were (2,1,1)(2,1,1) with m=52 based on seasonal period.
- Regression beat time series overall in terms of performance metrics.

---

# Analysis

The linear regression model was simpler, avoided overfitting the seasonal patterns, and handled the fluctuations better than time series models. It had an RMSE of around 160 on the test set while SARIMAX achieved RMSE of 165.

Even after tuning SARIMAX, the regression model was more robust. This indicates that classical regression is well-suited for this type of stock price forecasting problem, where a linear combination of the open, high, low prices and volume provides a good fit.

Time series should not be ruled out though, as they can capture seasonality and cyclic trends. With more complex data or longer time spans, SARIMAX may start to outperform regression. Overall the analysis shows regression as the better approach for now, but both should be considered depending on the structure of stock data.

---

##  Repository Structure

```sh
└── Stock-Price-Forecasting-and-Model-Comparison/
    ├── README.md
    ├── data
    │   ├── test.csv
    │   └── train.csv
    ├── gridsearch_results.txt
    ├── notebooks
    │   ├── gridsearch_cv_script.ipynb
    │   └── submission.ipynb
    ├── requirements.txt
    └── submission.csv
```

---
