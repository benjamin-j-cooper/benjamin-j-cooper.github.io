# Forecasting Global Temperatures


The objective of this problem is to build a time series model that can forecast the mean global temperature.




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>dt</th>
      <th>LandAverageTemperature</th>
      <th>LandAverageTemperatureUncertainty</th>
      <th>LandMaxTemperature</th>
      <th>LandMaxTemperatureUncertainty</th>
      <th>LandMinTemperature</th>
      <th>LandMinTemperatureUncertainty</th>
      <th>LandAndOceanAverageTemperature</th>
      <th>LandAndOceanAverageTemperatureUncertainty</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1750-01-01</td>
      <td>3.034</td>
      <td>3.574</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1750-02-01</td>
      <td>3.083</td>
      <td>3.702</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1750-03-01</td>
      <td>5.626</td>
      <td>3.076</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1750-04-01</td>
      <td>8.490</td>
      <td>2.451</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1750-05-01</td>
      <td>11.573</td>
      <td>2.072</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3187</th>
      <td>2015-08-01</td>
      <td>14.755</td>
      <td>0.072</td>
      <td>20.699</td>
      <td>0.110</td>
      <td>9.005</td>
      <td>0.170</td>
      <td>17.589</td>
      <td>0.057</td>
    </tr>
    <tr>
      <th>3188</th>
      <td>2015-09-01</td>
      <td>12.999</td>
      <td>0.079</td>
      <td>18.845</td>
      <td>0.088</td>
      <td>7.199</td>
      <td>0.229</td>
      <td>17.049</td>
      <td>0.058</td>
    </tr>
    <tr>
      <th>3189</th>
      <td>2015-10-01</td>
      <td>10.801</td>
      <td>0.102</td>
      <td>16.450</td>
      <td>0.059</td>
      <td>5.232</td>
      <td>0.115</td>
      <td>16.290</td>
      <td>0.062</td>
    </tr>
    <tr>
      <th>3190</th>
      <td>2015-11-01</td>
      <td>7.433</td>
      <td>0.119</td>
      <td>12.892</td>
      <td>0.093</td>
      <td>2.157</td>
      <td>0.106</td>
      <td>15.252</td>
      <td>0.063</td>
    </tr>
    <tr>
      <th>3191</th>
      <td>2015-12-01</td>
      <td>5.518</td>
      <td>0.100</td>
      <td>10.725</td>
      <td>0.154</td>
      <td>0.287</td>
      <td>0.099</td>
      <td>14.774</td>
      <td>0.062</td>
    </tr>
  </tbody>
</table>
<p>3192 rows × 9 columns</p>
</div>



We can see that the data set has monthly land temps from 1759 through 2015. There is also an uncertainty feature, and other features realting to min/max and ocean temps. We will only use the first feature, 'LandAverageTemp', but the 'landaveragetempuncertainty' may be useful if we want to drop older data that has a high degree of uncertainty. Also, we can make the 'dt' (date) column the index. We will take care of this, but first...

Since there does seem to be a degree of uncertainty in the older data, lets plot the uncertainty and determine if there is a reasonable cutoff to drop uncertain data before


    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_7_0.png)
    


in the plot, we can see that uncertainty in the data levels off somewhere between the late 1800's and early 1900's. I will arbitrarily choose 1850 as the threshold (where the verticle dashed line is) because this is where uncertainty dips below .5

### Define time series analysis class


    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_13_0.png)
    



    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_14_0.png)
    


    Dickey-Fuller Test: 
    Test Statistic           -0.090310
    p-value                   0.950395
    Lags Used                 3.000000
    No. of Observations     132.000000
    Critical Value (1%)      -3.480888
    Critical Value (5%)      -2.883697
    Critical Value (10%)     -2.578586
    dtype: float64


    Dickey-Fuller Test: 
    Test Statistic         -7.989453e+00
    p-value                 2.497164e-12
    Lags Used               3.000000e+00
    No. of Observations     9.600000e+01
    Critical Value (1%)    -3.500379e+00
    Critical Value (5%)    -2.892152e+00
    Critical Value (10%)   -2.583100e+00
    dtype: float64



    <Figure size 800x400 with 0 Axes>



    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_18_1.png)
    



    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_18_2.png)
    


    Performing stepwise search to minimize aic
     ARIMA(2,0,2)(0,0,0)[0] intercept   : AIC=-58.481, Time=0.17 sec
     ARIMA(0,0,0)(0,0,0)[0] intercept   : AIC=33.231, Time=0.03 sec
     ARIMA(1,0,0)(0,0,0)[0] intercept   : AIC=-42.986, Time=0.07 sec
     ARIMA(0,0,1)(0,0,0)[0] intercept   : AIC=-1.598, Time=0.03 sec
     ARIMA(0,0,0)(0,0,0)[0]             : AIC=719.981, Time=0.01 sec
     ARIMA(1,0,2)(0,0,0)[0] intercept   : AIC=-57.783, Time=0.18 sec
     ARIMA(2,0,1)(0,0,0)[0] intercept   : AIC=-57.537, Time=0.18 sec
     ARIMA(3,0,2)(0,0,0)[0] intercept   : AIC=-60.385, Time=0.25 sec
     ARIMA(3,0,1)(0,0,0)[0] intercept   : AIC=-52.392, Time=0.20 sec
     ARIMA(4,0,2)(0,0,0)[0] intercept   : AIC=-61.661, Time=0.27 sec
     ARIMA(4,0,1)(0,0,0)[0] intercept   : AIC=-63.557, Time=0.23 sec
     ARIMA(4,0,0)(0,0,0)[0] intercept   : AIC=-63.915, Time=0.15 sec
     ARIMA(3,0,0)(0,0,0)[0] intercept   : AIC=-52.008, Time=0.14 sec
     ARIMA(5,0,0)(0,0,0)[0] intercept   : AIC=-63.214, Time=0.20 sec
     ARIMA(5,0,1)(0,0,0)[0] intercept   : AIC=-60.946, Time=0.22 sec
     ARIMA(4,0,0)(0,0,0)[0]             : AIC=inf, Time=0.13 sec
    
    Best model:  ARIMA(4,0,0)(0,0,0)[0] intercept
    Total fit time: 2.471 seconds



    
![png](assets/images/tsa2_files/global_temp_timeseries_v04_19_1.png)
    
