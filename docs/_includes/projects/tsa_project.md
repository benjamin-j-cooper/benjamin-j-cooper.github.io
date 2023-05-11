# Forecasting US deaths per-day from Covid-19

Time Series are a common task in data science. The possibilities for applying time series analysis to real world situations are endless. Think of all the different aspects of your life or business and the chances are if you think of them in terms of time, or occuring over a period of time, that they could be turned into data and analyzed with a time series analysis. Time series analysis, however can be challenging: making predictings into the future is difficult because no one can exactly predict the future. For one, unforeseen events or events with unpredictable outcomes may occur that could effect the dependent variable we are intersted in predicting. <br><br>

Another way we can look at this is to ask, "what would have happened if X did not take place?". One such example of this in the real world involves the novel Covid-19 virus. With the fairly comprehensive amount of testing and hospital record collection that ocurred in the United States through the early stages of the pandemic, we have a high quality dataset with which to ask questions about the pandemic in the US and abroad. Here, I perform an exploratory data analysis of the global covid-19 daily death count data, and then conduct a time series analysis on the daily death count data in the US. The goal of the analysis is to forecast daily death counts if the mRNA vaccines and boosters had not been administered.<br><br>

The approach I took was to break the US data into logical segments and analyze each segment independently. For example, the first segment I delineated, spanned the time from the first recorded covid case to the release of the first booster. With the first segment, the training and testing data were split on the date of the realease of the first vaccine. I then forecasted daily death rates for the testing dataset based on the training data (the data before the vaccine was released) so the model would not take into account the impact of the vaccine on death rates. I repeated this process for the booster.<br><br>

Time series analysis has a number of components that are somewhat unique to time series data. These are: trend and seasonality. There is also a concept called 'stationarity' which basically means the data is free of the trend and seasonality. The steps for performing time series analysis are first to preprocess the data, perform exploratory data analysis, split the data into train and test sets, check for stationarity (Augmented Dickey-Fuller Test), remove stationarity (differencing, detrending, deseasoning and or log transformation), build models (AR, MA, ARMA, ARIMA), and forecast.<br><br>

After download the John's Hopkins global Covid-19 death count dataset from kaggle (https://www.kaggle.com/datasets/antgoldbloom/covid19-data-from-john-hopkins-university), I began by checking for missing data. 



    --------number of single country records, and number of provincial records---------
    False    201
    True      88
    dtype: int64
    --------number of records per country---------
    Country/Region
    Australia          8
    Canada            16
    China             34
    Denmark            3
    France            12
    Netherlands        5
    New Zealand        3
    United Kingdom    15
    dtype: int64



What is clear from the table above is that the data recorded for some countries has state/province information, but for other countries there is none. I am not interested in the states provincial feature at this time so I will drop it. Next I group the data by country using the pandas dataframe groupby() method and plot a correlation heatmap of death counts for the top 20 countries with the highest death counts.



    
![png](assets/images/tsa_files/covid19_analysis_clean_13_1.png)
    

One important thing to note about the covid 19 data is that not all countries followed the same reporting standards for infections or deaths. Therefor it is important to keep in mind that some countries that may not be in the top 20 in this dataset may have had underinflated death count data. Interestingly, int he correlation heatmap we can see that there are some lighter groups of blocks indicating correlation between the daily death counts between some countries. For example Brazil and India, or Columbia, and Argentina,a nd finally the UK, Italy, Germany, and France. The latter two groups make perfect sense as these countries are geographically, culturally, and economically more closely related. Next, I extracted the US data from the global dataset. The remainder of the analysis will focus just on the US dataset.


### US Covid 19 daily death rate analysis


plotting the cummulative US death counts from the start of the pandemic, we can see there are changes in the death rate over time:
    
![png](assets/images/tsa_files/covid19_analysis_clean_17_0.png)
    

To get a better picture of the these changes in death rate, I transformed the data into non-cumulative data using the built in pandas shift() method to the subtract the previous day from each days death count. 

### convert US to non-cummulative daily death counts

Here is the resulting non-cumulative data plotted from the start of the pandemic, with significant vaccination developments included as vertical dashed lines:

    
![png](assets/images/tsa_files/covid19_analysis_clean_21_1.png)
    

The vaccination events appear to be correlated with unpredictable drops in the covid death rate. To explore this further, I break the dataset into smaller windows of analysis. The first window is from the start of the pandemic to the release of the 1st booster. The training and testing data are split based on the date of the release of the 1st vaccines. I will then forecast the predicted death rate of the testing dataset with an ARIMA model. 

### Forecasting the predicted covid deaths 'hypothetically without first vaccine'

First, lets take a look at the trend and seasonlity of the training set...
    
![png](assets/images/tsa_files/covid19_analysis_clean_29_0.png)
    


    
![png](assets/images/tsa_files/covid19_analysis_clean_29_2.png)
    



    
![png](assets/images/tsa_files/covid19_analysis_clean_29_3.png)
    


    Dickey-Fuller Test: 
    Test Statistic           -3.232943
    p-value                   0.018155
    Lags Used                13.000000
    No. of Observations     294.000000
    Critical Value (1%)      -3.452790
    Critical Value (5%)      -2.871422
    Critical Value (10%)     -2.572035
    dtype: float64


    Performing stepwise search to minimize aic
     ARIMA(2,1,2)(0,0,0)[0] intercept   : AIC=4823.159, Time=0.43 sec
     ARIMA(0,1,0)(0,0,0)[0] intercept   : AIC=5005.576, Time=0.01 sec
     ARIMA(1,1,0)(0,0,0)[0] intercept   : AIC=5003.219, Time=0.02 sec
     ARIMA(0,1,1)(0,0,0)[0] intercept   : AIC=4996.994, Time=0.07 sec
     ARIMA(0,1,0)(0,0,0)[0]             : AIC=5003.693, Time=0.01 sec
     ARIMA(1,1,2)(0,0,0)[0] intercept   : AIC=4921.755, Time=0.29 sec
     ARIMA(2,1,1)(0,0,0)[0] intercept   : AIC=4893.048, Time=0.19 sec
     ARIMA(3,1,2)(0,0,0)[0] intercept   : AIC=inf, Time=0.38 sec
     ARIMA(2,1,3)(0,0,0)[0] intercept   : AIC=4801.726, Time=0.42 sec
     ARIMA(1,1,3)(0,0,0)[0] intercept   : AIC=4910.872, Time=0.33 sec
     ARIMA(3,1,3)(0,0,0)[0] intercept   : AIC=4825.775, Time=0.46 sec
     ARIMA(2,1,4)(0,0,0)[0] intercept   : AIC=4803.279, Time=0.51 sec
     ARIMA(1,1,4)(0,0,0)[0] intercept   : AIC=4865.388, Time=0.40 sec
     ARIMA(3,1,4)(0,0,0)[0] intercept   : AIC=4799.294, Time=0.50 sec
     ARIMA(4,1,4)(0,0,0)[0] intercept   : AIC=4686.396, Time=0.60 sec
     ARIMA(4,1,3)(0,0,0)[0] intercept   : AIC=4741.888, Time=0.49 sec
     ARIMA(5,1,4)(0,0,0)[0] intercept   : AIC=4662.236, Time=0.63 sec
     ARIMA(5,1,3)(0,0,0)[0] intercept   : AIC=4716.051, Time=0.61 sec
     ARIMA(5,1,5)(0,0,0)[0] intercept   : AIC=4660.664, Time=0.79 sec
     ARIMA(4,1,5)(0,0,0)[0] intercept   : AIC=4660.880, Time=0.74 sec
     ARIMA(5,1,5)(0,0,0)[0]             : AIC=4662.059, Time=0.57 sec
    
    Best model:  ARIMA(5,1,5)(0,0,0)[0] intercept
    Total fit time: 8.480 seconds


    RMSE:  2847.6034508083358



    
![png](assets/images/tsa_files/covid19_analysis_clean_32_0.png)
    


### Forecasting Covid deaths without Booster


    
![png](assets/images/tsa_files/covid19_analysis_clean_36_0.png)
    



    <Figure size 800x400 with 0 Axes>



    
![png](assets/images/tsa_files/covid19_analysis_clean_36_2.png)
    



    
![png](assets/images/tsa_files/covid19_analysis_clean_36_3.png)
    


    Dickey-Fuller Test: 
    Test Statistic           -2.207014
    p-value                   0.203710
    Lags Used                14.000000
    No. of Observations     137.000000
    Critical Value (1%)      -3.479007
    Critical Value (5%)      -2.882878
    Critical Value (10%)     -2.578149
    dtype: float64


    Performing stepwise search to minimize aic
     ARIMA(2,1,2)(0,0,0)[0] intercept   : AIC=2218.858, Time=0.29 sec
     ARIMA(0,1,0)(0,0,0)[0] intercept   : AIC=2346.095, Time=0.01 sec
     ARIMA(1,1,0)(0,0,0)[0] intercept   : AIC=2347.271, Time=0.02 sec
     ARIMA(0,1,1)(0,0,0)[0] intercept   : AIC=2345.702, Time=0.05 sec
     ARIMA(0,1,0)(0,0,0)[0]             : AIC=2344.170, Time=0.01 sec
     ARIMA(1,1,2)(0,0,0)[0] intercept   : AIC=2292.997, Time=0.20 sec
     ARIMA(2,1,1)(0,0,0)[0] intercept   : AIC=2277.113, Time=0.13 sec
     ARIMA(3,1,2)(0,0,0)[0] intercept   : AIC=inf, Time=0.26 sec
     ARIMA(2,1,3)(0,0,0)[0] intercept   : AIC=2222.894, Time=0.31 sec
     ARIMA(1,1,1)(0,0,0)[0] intercept   : AIC=2316.023, Time=0.11 sec
     ARIMA(1,1,3)(0,0,0)[0] intercept   : AIC=inf, Time=0.23 sec
     ARIMA(3,1,1)(0,0,0)[0] intercept   : AIC=2272.479, Time=0.17 sec
     ARIMA(3,1,3)(0,0,0)[0] intercept   : AIC=2231.633, Time=0.39 sec
     ARIMA(2,1,2)(0,0,0)[0]             : AIC=2219.060, Time=0.14 sec
    
    Best model:  ARIMA(2,1,2)(0,0,0)[0] intercept
    Total fit time: 2.324 seconds


    RMSE:  1468.883292091439



    
![png](assets/images/tsa_files/covid19_analysis_clean_39_0.png)
    

