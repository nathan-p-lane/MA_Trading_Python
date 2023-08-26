# Moving Average Trading Strategy Analysis
## Introduction
This repository contains a Python script that demonstrates the implementation and analysis of a simple moving average trading strategy using historical stock price data. The strategy aims to exploit trends in stock prices and make buy/sell decisions based on the relationship between the closing price and the moving average. The moral of the story is, well, I'm just glad I didn't try this with real money.

## Loading and Preprocessing Data
Firstly, I loaded in Johnson & Johnson historical stock data from NASDAQ over a 5 year period using Pandas. Then, I perform various preprocessing steps to clean and format the data. Dates are converted to the datetime format, columns are renamed, and unnecessary characters (dollar signs) are removed from numeric columns.

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/5610465b-4466-41b7-b32a-56826e04ca7f)


## Defining Moving Average Range and Strategy Implementation
The range of moving averages to be calibrated is defined, ranging from a 5-day MA to a 100-day MA. These values are stored in another DataFrame called 'Calib'. We are calibrating the range of moving average because we want to know the moving average window that maximizes Sharpe Ratio (SR). The idea is that, if we choose a moving average that maximizes SR, then typically we should expect more attractive returns given the risk. My goal here was to implement a trading strategy that would outperform just buying and holding JNJ positions. 

The script iterates through each parameter value (MA window) in the 'Calib' DataFrame. For each value, I calculate the moving average, identify buy/sell signals based on the relationship between closing price and moving average, and simulate trades accordingly. The portfolio's performance metrics are also calculated and recorded in the 'Calib' DataFrame. Namely, the mean, standard deviation, Sharpe ratio, and annualized Sharpe ratio of daily profit or loss.

## Concluding Remarks
This script demonstrates the implementation and analysis of a moving average trading strategy using historical stock price data. By following the step-by-step process and analyzing the provided visualizations, you can gain insights into how the strategy performs and compare it to a simple buy-and-hold strategy. 
