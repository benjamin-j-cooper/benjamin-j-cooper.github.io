# Covid 19 Death and Vaccination EDA (Worldwide)
### 1/22/2020 - 2/15/2023

#### Lets take a look at the raw global data tables from Johns's Hopkins (Kaggle)




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>Province/State</th>
      <th>Lat</th>
      <th>Long</th>
      <th>1/22/20</th>
      <th>1/23/20</th>
      <th>1/24/20</th>
      <th>1/25/20</th>
      <th>1/26/20</th>
      <th>1/27/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>NaN</td>
      <td>33.93911</td>
      <td>67.709953</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>NaN</td>
      <td>41.15330</td>
      <td>20.168300</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>NaN</td>
      <td>28.03390</td>
      <td>1.659600</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>NaN</td>
      <td>42.50630</td>
      <td>1.521800</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>NaN</td>
      <td>-11.20270</td>
      <td>17.873900</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1125 columns</p>
</div>



Each column is a country, but we can see by scrolling over that not all of them are countries. for example there is a "winter olympics 2022" column, so some of the columns are well known events. 

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 289 entries, 0 to 288
    Columns: 1125 entries, Country/Region to 2/15/23
    dtypes: float64(2), int64(1121), object(2)
    memory usage: 2.5+ MB


 - 1124 rows, each row is covid deaths reported for a country.  
 - 1121 of the columns are int64, so the death data is numeric, no need to convert it

### Taking a closer look at the province/state feature:

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

 - So it appears some of the data is in provincial format, some is not
 - lets remove the province/state columns - there is a lot of missing data there




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Lat</th>
      <th>Long</th>
      <th>1/22/20</th>
      <th>1/23/20</th>
      <th>1/24/20</th>
      <th>1/25/20</th>
      <th>1/26/20</th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
    <tr>
      <th>Country/Region</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan</th>
      <td>33.93911</td>
      <td>67.709953</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>Albania</th>
      <td>41.15330</td>
      <td>20.168300</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>Algeria</th>
      <td>28.03390</td>
      <td>1.659600</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>Andorra</th>
      <td>42.50630</td>
      <td>1.521800</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
    </tr>
    <tr>
      <th>Angola</th>
      <td>-11.20270</td>
      <td>17.873900</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1123 columns</p>
</div>



 - If we scroll to the right, we can see that the count is cumulative. to get the deaths per day, we would need to substract day from final day
 - We need to drop that most recent day since we cant calculate a value form the cumulative sum for that day




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>1/30/20</th>
      <th>1/31/20</th>
      <th>2/1/20</th>
      <th>2/2/20</th>
      <th>2/3/20</th>
      <th>2/4/20</th>
      <th>2/5/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1116 columns</p>
</div>






<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>1/30/20</th>
      <th>1/31/20</th>
      <th>2/1/20</th>
      <th>2/2/20</th>
      <th>2/3/20</th>
      <th>2/4/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>total_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>165</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1117 columns</p>
</div>



 - We can also see there are at least two "events" (the olympics):



<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>total_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>76</th>
      <td>Holy See</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Antarctica</td>
      <td>0</td>
    </tr>
    <tr>
      <th>185</th>
      <td>Tuvalu</td>
      <td>0</td>
    </tr>
    <tr>
      <th>197</th>
      <td>Winter Olympics 2022</td>
      <td>0</td>
    </tr>
    <tr>
      <th>170</th>
      <td>Summer Olympics 2020</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



 - We will leave them in for now. 


### Plotting distribution of death counts per day

    

![png](assets/images/tsa_files/Covid19_analysis_35_0.png)
    

 - Lets adjsut the number of bins and plot again...

    
![png](assets/images/tsa_files/Covid19_analysis_36_0.png)
    

### Plotting total deaths by country for top 10 counties with highest official death counts


  
![png](assets/images/tsa_files/Covid19_analysis_33_0.png)
    

 - lets adjsut this plot, turning it horizontally and coloring the country feature... 

    
![png](assets/images/tsa_files/Covid19_analysis_37_0.png)
    

### Plotting daily deaths for top 10 counties over time

    

![png](assets/images/tsa_files/Covid19_analysis_40_0.png)
    

### Correlation in death rates plotted as a heat map

    

![png](assets/images/tsa_files/Covid19_analysis_41_1.png)
    

 - Interestingly, we can see there is correlation between some countries in the top 10!
 - Countries in Europe (UK, Italy, Germany, France) are moderately correlated
 - US is moderately correlated with European countries
 - This is very interesting suggests we may want to look deeper into some of these trends we are observing:
 - Are countries with correlated death rates: closer in proximity? On the same continent? Share language? Have trade or diplomatic status? Frequent tourism?

# lets just look at the US data

### Questions to explore: 
 - What is the total number of deaths from covid in the US?
 - What is the Distribution of the daily death counts? 
 - What is the mean and standard deviation of number of daily deaths from covid in the US?
 - What is the trend in deaths in the US from covid like over the duration of the pandemic?
 




### First lets plot the distribution of deaths in the US:



![png](assets/images/tsa_files/Covid19_analysis_45_1.png)




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>daily_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1115</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>851</td>
    </tr>
    <tr>
      <th>top</th>
      <td>0</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>34</td>
    </tr>
  </tbody>
</table>
</div>






 - The distribution of daily deaths in the US is right skewed.   
 - Lets check the trend in the US Covid death rate by plotting number of deaths over time

### Plotting daily deaths in US from 1/22/2020 - 2/15/2023

 - Important public health events indicated with verticle red dashed lines
 - first line is lock down
 - other lines are releases of vaccines/booster authorizations
    
![png](assets/images/tsa_files/Covid19_analysis_52_0.png)
    
## To be continued...
