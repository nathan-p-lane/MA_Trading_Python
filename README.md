# Moving Average Trading Strategy Analysis
## Introduction
This repository contains a Python script that demonstrates the implementation and analysis of a simple moving average trading strategy using historical stock price data. The strategy aims to exploit trends in stock prices and make buy/sell decisions based on the relationship between the closing price and the moving average. The moral of the story is, well, I'm just glad I didn't try this with real money.

## Loading and Preprocessing Data
Firstly, I loaded in Johnson & Johnson historical stock data from NASDAQ over a 5 year period using Pandas. Then, I perform various preprocessing steps to clean and format the data. Dates are converted to the datetime format, columns are renamed, and unnecessary characters (dollar signs) are removed from numeric columns.

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/2fa80651-5ecc-4280-99bf-12c9a81c699a)



## Defining Moving Average Range and Strategy Implementation
The range of moving averages to be calibrated is defined, ranging from a 5-day MA to a 100-day MA. These values are stored in another DataFrame called 'Calib'. We are calibrating the range of moving average because we want to know the moving average window that maximizes Sharpe Ratio (SR). The idea is that, if we choose a moving average that maximizes SR, then typically we should expect more attractive returns given the risk. My goal here was to implement a trading strategy that would outperform just buying and holding JNJ positions. 

The script iterates through each parameter value (MA window) in the 'Calib' DataFrame. For each value, I calculate the moving average, identify buy/sell signals based on the relationship between closing price and moving average, and simulate trades accordingly. The portfolio's performance metrics are also calculated and recorded in the 'Calib' DataFrame. Namely, the mean, standard deviation, Sharpe ratio, and annualized Sharpe ratio of daily profit or loss.

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/8a27e57c-3069-444e-b2c4-ada8171d966f)

## Visualizing Calibration Results
To visualize the calibration results and determine which MA window maximizes the annualized Sharpe Ratio, I used Matplotlib. There are three plots generated: mean, standard deviation, and annualized Sharpe Ratio for different moving average window sizes. 

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/0fd8c142-630b-40d0-9e99-1a4617e910aa)

Additionally, the following visualization summarizes when I make trades using a calibrated MA trading strategy and at what price: 

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/d670c4be-77ff-40b8-a79b-cf7c2bd9146f)

Lastly, here comes my epic failure when it comes to my trading strategy:

![image](https://github.com/nathan-p-lane/MA_trading_python/assets/141770222/72d8fbe0-3bed-4cfe-bbae-36ee54d5d839)

## Why Did I Fail?
The performance of our calibrated trading strategy (MA) was extremely poor, and lost tons more money than BnH. The performance of a moving average strategy is highly dependent on the market conditions during the time period being evaluated. If the market experiences long periods of trending behavior, then a moving average strategy can perform well. However, if the market experiences a lot of volatility or choppy trading, then a moving average strategy can result in many false signals, leading to poor performance. 

For the case of Johnson & Johnson, its 5-year historical data looks very volatile at first glance. This could be a reason why our MA strategy did so poorly compared to the BnH. Secondly, a shorter MA window size will produce more trading signals, but also more false signals, while a longer MA window size will produce fewer signals, but with more significant lag. If the MA window size is not optimized for the specific market conditions being evaluated, then the strategy may not perform well. The window size of 25 we chose for the 5-year data is relatively short, so there were probably tons of false signals which lead to poor performance. 


## Concluding Remarks
This script demonstrates the implementation and analysis of a moving average trading strategy using historical stock price data. By following the step-by-step process and analyzing the provided visualizations, you can gain insights into how the strategy performs and compare it to a simple buy-and-hold strategy. 
