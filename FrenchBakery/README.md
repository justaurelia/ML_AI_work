# Project Name

French Bakery Sales Analysis

## Context

In the context of a retail bakery, the question to answer is 
What is the number of baguettes I will sold tomorrow ? 

## Overview

The goal of this project is to practice data analysis, visualizations and modelizations for the Capstone of the AI & Machine Learning course. 
Knowing the expected sales of baguettes can allow the bakery owner to produce the good number of baguettes, 
be ready for high demand or low demand, maximize his sales and minimize his lost (unsold baguettes).
If the question stays unanswered, the bakery owner can produce too much baguettes that I will have to discard at the end of the day, 
or he can have not enough and have unsatisfied customers.

## Data

This data comes from kaggle (https://www.kaggle.com/datasets/matthieugimbert/french-bakery-daily-sales/data).
The dataset belongs to a French bakery. The dataset provides the daily transaction details of customers from 2021-01-01 to 2022-09-30.
I computed an other file to map article (item) and a logical category.
I also got temperature levels online for these dates (1=freezing, 2=very cold, ..., 7=sweltering) and holidays in Guerande (France).

### Data Description

The attributes of this data set include:
- date: date order
- time: time order
- ticket number: identifier for every single transaction
- article: name of the product sold (in French)
- quantity: quantity sold
- unit_price: price per product
At which I added :
- category : category of the item
- temperature : level of temperature (1-7)
- holiday : regular day, school break or holiday

## Data prepocessing and cleaning

Here are the operations I made on the data to get a cleaned and usable dataset:
- Transformation of the types (date and time, unit_price)
- Deletion of duplicates and null price
- Isolation of refunds (negative transactions) and their associated initial transactions
- Add category, weekday, month and total_price
- Add temperature and holidays

## Notebooks

- [Jupyter Notebook](./main_notebook_Capstone.ipynb): A detailed exploration and analysis of the data to answer the question : How many baguette will be sold?
- [Jupyter Notebook](./main_notebook_Global.ipynb): A Global exploration and analysis of the data containing more vizualisations.

## Summary of Findings for global exploration

### Baguettes sold per weekday and type of day
![Baguettes sold per weekday and type of day](/images/baguetteByWeekdayProfile.png)
We can observe a clear increase of sales of baguettes during holiday and school break whatever weekday it is.
There is also more sales during the weekend than the middle of the week.

### Baguettes sold per temperature and type of day
![Baguettes sold per temperature and type of day](/images/baguetteByTemperatureProfile.png)
We can observe a clear increase of sales of baguettes during holiday and school break.
The base for a regular day is flat whatever temperature is outside, expect for the Freezing day which have less sales.

## Analysis
### Decomposition 
Using standard decomposition, and MSTL, we can observe a seasonality of 7 days.
We can also see how is the trend increasing during the summer months when it's school break.

### Stationarity
With AdFuller we can check that the data is stationary

### ARIMA model
Because we can't use a gridSearch with a time analysis modelization such as ARIMA, we produced an evaluation method and tried with multiple values of p,d,q.
The best MSE was 80.370 for the order (4, 2, 1). This is not a good MSE.

### SARIMAX model
In order to include other features (holiday, temperature) in the modelization, we used SARIMAX and an other evaluation method and tried with multiple values of orders.
The best MSE was 8.344 for the order ((6, 1, 0), (0, 0, 2, 7)). This is better than the best one for ARIMA, but still not good to have a precise forecast of the sales of baguettes.

### Linear Regression Approach
I was wondering if we ignore the time series analysis and consider only the weekday and month with the others features and a linear regression, what would be the mse.
The results are :
 - Best parameters: {'regressor__fit_intercept': False, 'regressor__positive': False, 'scaler__with_mean': False, 'scaler__with_std': True}
 - Best cross-validation score: -0.50
 - Test MSE: 144.84
Which is not good at all. ;)

### Final thoughts
Getting more data would increase the accuracy of the modelization. 
Temperature and Holidays features definetely increased the score.
The first action for the bakery owner can be to pay attention to holidays and school breaks and increase their production of baguettes for these days.
But it will complicated to have a precise estimation of the number of baguettes sold for the following day.



## Summary of Findings for global exploration
![Global analysis](/images/thumbnail.png)
### profile during time of day
- No sales between 2:30pm and 3:30pm. Maybe the bakery is closed during this time.
- Most of the sales are done during the morning or between 4:30pm-6:30pm
- We can observe trends according to the categories of sold items

### profile during week of day
- Obviously more sales during the weekend
- Bigger increase for the cakes, tarts and pastry during the weekend too

### profile during months of the year
- We can observe a bigger revenue during the summer months (July and August). These months are the vacations months for French people. Like any non working day, French people are eating more bakery items during the summer days. But the bakery may be also open while others in the same neighborhood are closed so they may take part of their revenue.

### revenue distribution per category
- Baguette represents 38% of the global revenue in that bakery

### bill analysis
- The average bill is 2.6 items for 4 euros which is relatively cheap compared to the price in USA where only 1 baguette costs $4 !
- The max total price is 199.70 euros and the max number of items in one purchase is 87.

## More to come
An analysis on the refunds is possible
