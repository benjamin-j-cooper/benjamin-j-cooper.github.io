# Executive Summary

### *Problem Summary*
<font size="4">        With the advent of smartphones and the consumer economy, there has been a revolution in the ways that people consume products and content. At the same time, digital music and digital music distribution platforms have become some of the most widely accessible and highly consumed product markets in the world. Yet with this deluge of digital music content comes a challenge: how do users find new content that they enjoy, and how do digital music platforms enable music discovery by users? These challenges are exacerbated by the fact that in the modern fast-paced world, people are often time or attention limited, there are other platforms competing for user attention, and digital content-based company's revenue often relies on the time consumers spend on, or interact with, its platform. These companies need to be able to figure out what kind of content is needed to increase customer time spent on their platform, the amount of interaction had with their platform, and the overall satisfaction with a user’s experience on the platform. The key challenge for companies is in figuring out what kind of content their users are most likely to consume. Spotify is one such music content provider with a huge market base across the world. With the ever-increasing volume of streaming music becoming available, finding new music of interest has become a tedious task in and of itself. Spotify has grown significantly in the market because of its ability to make highly personalized music recommendations to every user of its’ platform based on a huge preference database gathered over time - millions of customers and billions of songs. This is done by using smart recommendation systems that can recommend songs based on users’ likes/dislikes, incorporating both content-based and latent features for song recommendations. However, the recommendation system used by Spotify and its hyperparameter settings have remained a proprietary, closely guarded secret. Here, I build a recommendation system to provide a top 10 of personalized song recommendations to a user that the user is most likely to enjoy/like/interact-with based on that users’ personal musical preferences.
</font>

### *Solution Summary*
<font size="4">       In total, I explored six recommendation systems using the 1 million songs dataset<sup>1</sup> as part of the solution design for this project: popularity-based, user-user collaborative filtering, item-item collaborative filtering, matrix factorization, cluster-based, and content-based. To evaluate the different models analyzed here, I relied on the F1_score, model predictions of user/song interactions, and the top 10 recommended songs by each model. These metrics clearly demonstrate a higher level of performance by three of the six models: matrix factorization (Singular Value Decomposition with default settings, with a 70% weight applied), user-user collaborative filtering (KNN basic algorithm with msd distance, max cluster size of 50, minimum cluster size of 9, and 30% weight applied), and the content-based model (tf-idf encoding and cosign-similarity distance on album title, artist name, and release year). Therefore, I propose a Hybrid-Based Recommendation System, built by combining these three models with the specified hyperparameters, be adopted for personalized recommendations of music with maximum user interaction potential. The proposed hybrid recommendation system boasts fast computational times, high prediction accuracy of user preferences, and a balanced recommendation of familiar and diverse new music for users. However, the model is subject to limitations such as a 'cold start' problem when making predictions for new users with few listens, and with the ever-increasing volume of songs becoming available and users adopting the platform this will lead to longer and longer computation times (and presumably less user satisfaction). Additionally, the model generally favors popular artists and songs, which could have an impact on the music industry by making it more difficult for new artists to break into the scene using this platform.<br>
       Importantly, to reduce the computational resources required to test, train, and evaluate the solution design for this project, it was necessary to reduce the size of the dataset to make it more computationally tractable. The resulting filtered dataset reduced the original '1 million songs' dataset (with 2 million records) to 121,900 records and increased the accuracy of predicted user interactions by reducing high degree of imbalance in the data from infrequent users and unpopular songs. While these results do not address the 'cold start' issue, they demonstrate the importance of a filtering step for making fast and relevant recommendations. Therefore, I suggest the application of a pre-recommendation filter as part of a production design. Additionally, the content-based part of the recommendation system could also be improved by incorporating further features such as genre, lyrics, danceability, and encoded recordings. With these additions to the content portion of the recommendation system, the weight of the content-based model in the final hybrid recommendation system might be increased in future versions of the product. I recommend that these limitations and proposals be considered in future releases of the recommendation system for improved user personalization and increased user satisfaction.
</font> 
==> NOTE <== <br>
For the full code check out the GitHub Link at the bottom of the page

### **The objective:**

Build a recommendation system to propose the top 10 songs for a user based on the likelihood of listening to those songs.

### **The key questions:**

- What is the structure of the dataset?
- What variables will be used to make the recommendation system?
- What is the distribution of the 'rating' variable?
- Which models will be used to build a recommendation system?
- How will models be evaluated?
- Based on criteria, which model is 'best'?
- Is this model good enough for production?

## **The Data**

The core data is the Taste Profile Subset released by the Echo Nest as part of the Million Song Dataset. There are two files in this dataset. The first file contains the details about the song id, titles, release, artist name, and the year of release. The second file contains the user id, song id, and the play count of users.

## **Data Source**
http://millionsongdataset.com/ (1)

The dataset is split into two .csv files I load here. The two dataframes and their features are:

__song_data__

- song_id - A unique id given to every song

- title - Title of the song

- Release - Name of the released album

- Artist_name - Name of the artist 

- year - Year of release

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>song_id</th>
      <th>play_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOAKIMP12A8C130995</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOBBMDR12A8C13253B</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOBXHDL12A81C204C0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOBYHAJ12A6701BF1D</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SODACBL12A8C13C273</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SODDNQT12A6D4F5F7E</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SODXRTY12AB0180F3B</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOFGUAY12AB017B0A8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOFRQTD12A81C233C0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>b80344d063b5ccb3212f76538f3d9e43d87dca9e</td>
      <td>SOHQWYZ12A6D4FA701</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>





__count_data__

- user _id - A unique id given to the user

- song_id - A unique id given to the song

- play_count - Number of times the song was played

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>song_id</th>
      <th>title</th>
      <th>release</th>
      <th>artist_name</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SOQMMHC12AB0180CB8</td>
      <td>Silent Night</td>
      <td>Monster Ballads X-Mas</td>
      <td>Faster Pussy cat</td>
      <td>2003</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SOVFVAK12A8C1350D9</td>
      <td>Tanssi vaan</td>
      <td>Karkuteillä</td>
      <td>Karkkiautomaatti</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SOGTUKN12AB017F4F1</td>
      <td>No One Could Ever</td>
      <td>Butter</td>
      <td>Hudson Mohawke</td>
      <td>2006</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SOBNYVR12A8C13558C</td>
      <td>Si Vos Querés</td>
      <td>De Culo</td>
      <td>Yerba Brava</td>
      <td>2003</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SOHSBXH12A8C13B0DF</td>
      <td>Tangle Of Aspens</td>
      <td>Rene Ablaze Presents Winter Sessions</td>
      <td>Der Mystic</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>SOZVAPQ12A8C13B63C</td>
      <td>Symphony No. 1 G minor "Sinfonie Serieuse"/All...</td>
      <td>Berwald: Symphonies Nos. 1/2/3/4</td>
      <td>David Montgomery</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>SOQVRHI12A6D4FB2D7</td>
      <td>We Have Got Love</td>
      <td>Strictly The Best Vol. 34</td>
      <td>Sasha / Turbulence</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>SOEYRFT12AB018936C</td>
      <td>2 Da Beat Ch'yall</td>
      <td>Da Bomb</td>
      <td>Kris Kross</td>
      <td>1993</td>
    </tr>
    <tr>
      <th>8</th>
      <td>SOPMIYT12A6D4F851E</td>
      <td>Goodbye</td>
      <td>Danny Boy</td>
      <td>Joseph Locke</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>SOJCFMH12A8C13B0C2</td>
      <td>Mama_ mama can't you see ?</td>
      <td>March to cadence with the US marines</td>
      <td>The Sun Harbor's Chorus-Documentary Recordings</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>


#### **Observations and Insights:**
- The Count dataset has 3 columns (user_id, song_id, and play_count)
- The Count dataset has 2,000,000 observations
- The Songs dataset has 5 columns (song_id,title,release,artist_name,year)
- The Songs dataset has 1,000,000 observations
- There are some missing titles and releases
- The primary/foreign key to merge these two datasets is song_id
- The user_id and song_id are encrypted and can be encoded. However, this could cause problems if we were working on a real life data science business problem where user_id and song_id might need to be retained, or if later on in this analysis we wanted to encorporate other features from the 1 million songs data set online. Therefore, I will not encode these. 
- As the data also contains users who have listened to very few songs and vice versa, filtering these records out of the data could 'get two birds with one stone' by decreasing the **cold start** problem, and decreasing the **computational resources** needed to analyze this large dataset.

==> NOTE <== <br>
- A dataset of size 2000000 rows x 7 columns can be quite large and may require a lot of computing resources to process. This can lead to long processing times and can make it difficult to train and evaluate your model efficiently.
In order to address this issue, I filtered the dataset to decrease its size and reduce the class imbalance, and then scaled the play_count feature.

### Exploratory Data Analysis (EDA):
Lets take a look at the distribution of 'play_count', the feature I use as a proxy for user 'rating':


    
![png](assets/images/rs_files/recommender_system_22_0.png)
    



From this distribution plot, we can see that the number of songs played by each user (lets call it user interactions) is heavily right skewed. There are many (thousands) users who have only listened to a few songs, so any matrix I build from this data will be extremely sparse. Next I reduce the skew in the play_counts by filtering out users who have less than a minimum (I settled on 90) number of total plays. These are users that there is very little preference data for. Plotting the distriution of 'play_count' after filtering:

    
![png](assets/images/rs_files/recommender_system_26_1.png)
    

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Column</th>
      <th>Non-Null</th>
      <th>Count</th>
      <th>Dtype</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>user_id</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>1</th>
      <td>song_id</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>2</th>
      <td>title</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>3</th>
      <td>release</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>4</th>
      <td>artist_name</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>5</th>
      <td>year</td>
      <td>1224498</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
    <tr>
      <th>6</th>
      <td>play_count</td>
      <<td>1224498</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
  </tbody>
</table>
</div>

Filtering out less active users has decreased the imbalance somewhat. The distribution is still heavily right skewed in the above plot, but the class imbalance has been reduced by a factor of 5 (y limit is 1200 instead of 7000). This has also decreased the size of the dataset to 1.2 million records down from 2 million. <br><br>
This is still not good enough, so I continue to decrease the sparcity and imbalance of the data by filtering out any user/song records that have a play count less than 6. There are many more songs that users have only listened to 1 or a few times. I want to recommend highly rated songs, so I am going to get rid of these songs with low interactions and assume they are uninteracted with 'not-liked'. 

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Column</th>
      <th>Non-Null</th>
      <th>Count</th>
      <th>Dtype</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>user_id</td>
      <td>185694</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>1</th>
      <td>song_id</td>
      <td>185694</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>2</th>
      <td>title</td>
      <td>185694</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>3</th>
      <td>release</td>
      <td>185694</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>4</th>
      <td>artist_name</td>
      <td>185694</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>5</th>
      <td>year</td>
      <td>185694</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
    <tr>
      <th>6</th>
      <td>play_count</td>
      <<td>185694</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
  </tbody>
</table>
</div>

This last filtering step dramatically reduced the size of the dataset by 85%, this will speed up processing times for the models and also make the predictions more accurate by reducing the class imbalance. Finally, I filter out all songs that have less than 20 user interactions:


    
![png](assets/images/rs_files/recommender_system_34_1.png)
    

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Column</th>
      <th>Non-Null</th>
      <th>Count</th>
      <th>Dtype</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>user_id</td>
      <td>124147</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>1</th>
      <td>song_id</td>
      <td>124147</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>2</th>
      <td>title</td>
      <td>124147</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>3</th>
      <td>release</td>
      <td>124147</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>4</th>
      <td>artist_name</td>
      <td>124147</td>
      <td>non-null </td>
      <td>object</td>
    </tr>
    <tr>
      <th>5</th>
      <td>year</td>
      <td>124147</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
    <tr>
      <th>6</th>
      <td>play_count</td>
      <<td>124147</td>
      <td>non-null </td>
      <td>int64</td>
    </tr>
  </tbody>
</table>
</div>

With these filtering steps, I have reduced the class imbalance, decreased the size of the dataset to make models and gridsearch more tracteable, and I have decreased the extreme sparcity of our resulting recommendations matrices. Now I am going to apply a threshhold limit to further reduce class imblance and the play_count range, and then apply a min max scalar to standardize the play_counts so I can effectively use them as a proxy for a 1-10 rating.

### Clipping and Scaling play_count:
Because there are very few users who have listened to a song more than 25 times, I will set a threshold at 25 plays. I dont want to drop records with more than 25 plays because this is important information on users likes, So I will clip anything > 25 to 25 and then apply a MinMaxScalar function from the sklearn package to scale the playcounts from 1-10.<br>
Distribution plot after filtering:

    
![png](assets/images/rs_files/recommender_system_41_1.png)
    


Distribution plot after scaling:


    
![png](assets/images/rs_files/recommender_system_42_1.png)
    


My final play_counts, filtered, clipped, and scaled look pretty good. The class imbalance between the left side of the X axis and the higher play_counts has been reduced, The play_counts are scaled from 1-10, and I have kept the records containing the highest ratings as 10's.




    (121900, 8)



The final dataset has 121,900 records. This is a much more maneagable number of records for training and testing models. After previous iterations of testing the filtering, I had dropped over 90% of the songs so the final recommendations that were being made were not diverse and nearly the same for every user. So Im going to continue EDA and take a look at the filtered dataset to make sure the user/song diversity is still good...

## **Exploratory Data Analysis Continued...**

### **Checking the total number of unique users, songs, artists in the data**

Total number of unique user id

    Number of unique USERS =  19212


Total number of unique song id

    Number of unique SONGS =  2210


Total number of unique artists

    Number of unique artists =  1194


#### **Observations and Insights:**
- There are 19212 unique users remaining in the dataset after filtering
- There are 2210 unique songs remaining in the dataset after filtering 
- There are 1194 Unique artists remaining in the dataset after filtering
- This looks like a great balance, we have filtered out rare users and songs but retained many different users and we have a diversity of songs and artists.

### **Let's find out about the most interacted songs and interacted users**

Most interacted songs




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>song_id</th>
      <th>play_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>138</th>
      <td>SOBONKR12A58A7A7E0</td>
      <td>1466</td>
    </tr>
    <tr>
      <th>80</th>
      <td>SOAUWYT12A81C206F1</td>
      <td>1445</td>
    </tr>
    <tr>
      <th>1624</th>
      <td>SOSXLTC12AF72A7F54</td>
      <td>1186</td>
    </tr>
    <tr>
      <th>478</th>
      <td>SOFRQTD12A81C233C0</td>
      <td>1133</td>
    </tr>
    <tr>
      <th>88</th>
      <td>SOAXGDH12A8C13F8A1</td>
      <td>1024</td>
    </tr>
    <tr>
      <th>357</th>
      <td>SOEGIYH12A6D4FC0E3</td>
      <td>993</td>
    </tr>
    <tr>
      <th>1188</th>
      <td>SONYKOW12AB01849C9</td>
      <td>831</td>
    </tr>
    <tr>
      <th>1901</th>
      <td>SOWCKVR12A8C142411</td>
      <td>748</td>
    </tr>
    <tr>
      <th>1343</th>
      <td>SOPUCYA12A8C13A694</td>
      <td>744</td>
    </tr>
    <tr>
      <th>647</th>
      <td>SOHTKMO12AB01843B0</td>
      <td>616</td>
    </tr>
  </tbody>
</table>
</div>



Most interacted users




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>play_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5683</th>
      <td>4be305e02f4e72dad1b8ac78e630403543bab994</td>
      <td>106</td>
    </tr>
    <tr>
      <th>766</th>
      <td>0a4c3c6999c74af7d8a44e96b44bf64e513c0f8b</td>
      <td>82</td>
    </tr>
    <tr>
      <th>827</th>
      <td>0b19fe0fad7ca85693846f7dad047c449784647e</td>
      <td>81</td>
    </tr>
    <tr>
      <th>8262</th>
      <td>6d625c6557df84b60d90426c0116138b617b9449</td>
      <td>74</td>
    </tr>
    <tr>
      <th>16334</th>
      <td>da3890400751de76f0f05ef0e93aa1cd898e7dbc</td>
      <td>69</td>
    </tr>
    <tr>
      <th>7930</th>
      <td>695179610d0b1fbb9d66267a3bd24946617af7fb</td>
      <td>67</td>
    </tr>
    <tr>
      <th>17477</th>
      <td>e9a7dba8248ced646ea192016660e3c9056c0d03</td>
      <td>66</td>
    </tr>
    <tr>
      <th>2996</th>
      <td>283882c3d18ff2ad0e17124002ec02b847d06e9a</td>
      <td>65</td>
    </tr>
    <tr>
      <th>5405</th>
      <td>48567d388c6a7dda0e9d0a7b6648bdb42440475c</td>
      <td>65</td>
    </tr>
    <tr>
      <th>10463</th>
      <td>8c78c69701072e204f4340ca4d6ee44fe39e40cc</td>
      <td>64</td>
    </tr>
  </tbody>
</table>
</div>



#### **Observations and Insights:**
- The most interacted song is 'SOBONKR12A58A7A7E0' which has been interacted with by 1466 different users
- The most active user is '4be305e02f4e72dad1b8ac78e630403543bab994', they have listened to 106 different songs

Songs played in a year




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>49</th>
      <th>48</th>
      <th>47</th>
      <th>46</th>
      <th>43</th>
      <th>45</th>
      <th>50</th>
      <th>41</th>
      <th>42</th>
      <th>...</th>
      <th>17</th>
      <th>21</th>
      <th>7</th>
      <th>6</th>
      <th>3</th>
      <th>5</th>
      <th>12</th>
      <th>1</th>
      <th>2</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>year</th>
      <td>0</td>
      <td>2009</td>
      <td>2008</td>
      <td>2007</td>
      <td>2006</td>
      <td>2003</td>
      <td>2005</td>
      <td>2010</td>
      <td>2001</td>
      <td>2002</td>
      <td>...</td>
      <td>1977</td>
      <td>1981</td>
      <td>1967</td>
      <td>1966</td>
      <td>1962</td>
      <td>1965</td>
      <td>1972</td>
      <td>1958</td>
      <td>1960</td>
      <td>1963</td>
    </tr>
    <tr>
      <th>play_count</th>
      <td>26580</td>
      <td>12782</td>
      <td>10616</td>
      <td>7499</td>
      <td>6693</td>
      <td>5718</td>
      <td>4861</td>
      <td>4617</td>
      <td>4316</td>
      <td>4147</td>
      <td>...</td>
      <td>151</td>
      <td>145</td>
      <td>137</td>
      <td>134</td>
      <td>113</td>
      <td>110</td>
      <td>77</td>
      <td>66</td>
      <td>62</td>
      <td>61</td>
    </tr>
  </tbody>
</table>
<p>2 rows × 51 columns</p>
</div>






    Text(0, 0.5, 'number of releases')




    
![png](assets/images/rs_files/recommender_system_63_1.png)
    


#### **Observations and Insights:** 
- It is not clear whether the 'year' feature is, but it is most likely the year a song/album was released.
- We can clearly see that there in an increasing trend from 1960-2008 in the number of songs released
- This makes sense as there are more people, more artists, and musical equiptment, recording equiptment, and streaming platforms have made it easier to produce music

Now I apply different algorithms to build a recommendation system.

### Building a baseline popularity-based recommendation system

In this basic recommendation system, I take the count and sum of play counts of the songs and build the popularity recommendation system based on the sum of play counts (For the full code check out the Github Link at the bottom of the page). The rank based recommender function is:




<script src="https://gist.github.com/benjamin-j-cooper/de5bd92f9523060ea8aeec70a712cce9.js"></script>




Here is the output after running the popularity-based RS on the filtered dataset:

<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>221</td>
      <td>keller williams</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Call It Off (Album Version)</td>
      <td>Tegan And Sara</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Clara meets Slope - Hard To Say</td>
      <td>Clara Hill</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kelma</td>
      <td>Rachid Taha</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Numb (Album Version)</td>
      <td>Disturbed</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Voices On A String (Album Version)</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <th>6</th>
      <td>What If I Do?</td>
      <td>Foo Fighters</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Encore Break</td>
      <td>Pearl Jam</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Reign Of The Tyrants</td>
      <td>Jag Panzer</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Dance_ Dance</td>
      <td>Fall Out Boy</td>
    </tr>
  </tbody>
</table>
</div>



### Collaborative Filtering, Matrix Factorization, and Clustering based recommendation sytems

Before running the following recommendation systems, I developed several functions for calculating metrics to evaluate the models. The metrics I used are Root Mean Squared Error, Mean Average Error, Precision, Recall, and F1.



<script src="https://gist.github.com/benjamin-j-cooper/3db000dfbf39f94b4afe5ea577e285f5.js"></script>


<script src="https://gist.github.com/benjamin-j-cooper/4750aaeaae7661f5a5ac16fe72216773.js"></script>


<script src="https://gist.github.com/benjamin-j-cooper/13375250f5ca58f79679578c2a9e9fe5.js"></script>


I then split the data into a train and test set (Link to full code is at the bottom of the page). Also, to build the user-user-similarity-based and subsequent models I used the "surprise" library from Python.

#### **User User Similarity-Based Collaborative Filtering Metrics**

The code for implementing the user-user similarity matrix with base settings is:


<script src="https://gist.github.com/benjamin-j-cooper/935e3549ec7134a9901a1836566800b6.js"></script>


Result:

    RMSE: 3.1852
    MAE:  2.5755
      algorithm      rmse       mae  precision  recall  f1_score  popularity
    0  KNNbasic  3.185239  2.575525      0.682   0.772     0.724        24.3


**Observations and Insights:**<br>
For the untuned User-user similarity-based model,
- The RMSE is 3.18
- The MAE is 2.57
- The f1 score is 0.72
- The average popularity of recommended songs is 24.3

predictions using knn.KNNBasic for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 3.97 
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 3.74 
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 3.45 

**Observations and Insights:**
- For the song the user has seen with a rating of 10, the model predicted a rating of 3.97
- For the song the user has seen with a rating of 1, the model predicted a rating of 3.74
- For the unheard songs by the user, the model predicted 3.45
- The user-user similarity-based collaborative filtering method has good RMSE, MAE and f1_score, but...
- The user-user model isnt predicting ratings very well
- All three songs have similar predicted 'ratings' for this user

Next, I tuned the model using GridSearchCV to try to improve the model performance. 


<script src="https://gist.github.com/benjamin-j-cooper/5e8fb02b0f847600d410fb56d0852b37.js"></script>


The metrics after tuning are:

    2.8805243519619927
    {'k': 50, 'min_k': 9, 'sim_options': {'name': 'msd', 'user_based': True}}

    RMSE: 2.8309
    MAE:  2.2550
            algorithm      rmse       mae  precision  recall  f1_score  popularity
    0        KNNbasic  3.185239  2.575525      0.682   0.772     0.724        24.3
    1  KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745        64.9


**Observations and Insights:**<br>
After tuning the user-user model,
- The RMSE has decreased over the untuned model
- The MAE has also decreased
- The f1 score has increased
- The popularity of recommended songs has increased


predictions using knn.KNNBasic tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 8.95
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 3.14
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 3.38


**Observations and Insights:**
- The model is predicting a rating of 8.95 for the song the user has heard and rated a 10, this is very good.
- The model is predicting a rating of 3.14 for the song the user has heard and rated a 1, this is not bad.
- The model is rating the unheard song 3.38.
- It seems that tuning the model has improved its ability to predict ratings

Finally, because more 'popular' songs are more likely to be 'liked', I adjust the tuned recommendations by using a custom script to weight recommendations by the number of plays. The final, weighted, recommednations from the User-User similarity-based recommendation system for user '6ccd111af9b4baa497aacd6d1863cbf5a141acc6' are:




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Clara meets Slope - Hard To Say</td>
      <td>Clara Hill</td>
      <td>89</td>
      <td>9.205088</td>
      <td>9.099088</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Numb (Album Version)</td>
      <td>Disturbed</td>
      <td>68</td>
      <td>8.825430</td>
      <td>8.704162</td>
    </tr>
    <tr>
      <th>2</th>
      <td>When You're Gone</td>
      <td>Avril Lavigne</td>
      <td>76</td>
      <td>8.568666</td>
      <td>8.453958</td>
    </tr>
    <tr>
      <th>3</th>
      <td>#40</td>
      <td>DAVE MATTHEWS BAND</td>
      <td>72</td>
      <td>8.503340</td>
      <td>8.385488</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Speechless (Album Version)</td>
      <td>The Veronicas</td>
      <td>45</td>
      <td>8.512847</td>
      <td>8.363776</td>
    </tr>
    <tr>
      <th>5</th>
      <td>XRDS</td>
      <td>Covenant</td>
      <td>51</td>
      <td>8.475145</td>
      <td>8.335117</td>
    </tr>
    <tr>
      <th>6</th>
      <td>(iii)</td>
      <td>The Gerbils</td>
      <td>88</td>
      <td>8.352223</td>
      <td>8.245623</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Modern world</td>
      <td>Modern Lovers</td>
      <td>51</td>
      <td>8.274458</td>
      <td>8.134430</td>
    </tr>
    <tr>
      <th>8</th>
      <td>The Memory Remains</td>
      <td>Metallica / Marianne Faithfull</td>
      <td>94</td>
      <td>8.209485</td>
      <td>8.106343</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Sunburn</td>
      <td>Muse</td>
      <td>15</td>
      <td>8.156890</td>
      <td>7.898691</td>
    </tr>
  </tbody>
</table>
</div>



**Observations and Insights:**
- I predicted 10 songs for the user '6d625c6557df84b60d90426c0116138b617b9449' with the user-user collaborative filtering method
- Some of the songs that are recommended to the user have a predicted rating close to 10, this is very good. 
- Evaluating the tuned and untuned models, the tuned model has improved performance based on the evaluation metrics I chose. 

### Item-Item Similarity-based collaborative filtering recommendation system

**Metrics of the item-item model compared to user-user**

    RMSE: 2.9990
    MAE:  2.2550
            algorithm      rmse       mae  precision  recall  f1_score  popularity
    0        KNNbasic  3.185239  2.575525      0.682   0.772     0.724        24.3
    1  KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745        64.9
    2   KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695        25.1


**Observations and Insights:**
- The RMSE for the item-item model is 2.99
- The item-item collaborative filtering model has nearly the the same MAE as the tuned user-user model
- the f1 score is 0.695
- The popularity of recommended songs is 25


predictions using knn.KNNBasic_item for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 4.40
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 4.44
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 4.72


**Observations and Insights:**
- The model is predicting 4.4 for the heard song that had rating of 10
- The model is predicting 4.44 for the heard song that had rating of 1
- The model is predicting 4.72 for the unheard song
- Overall, the prediction of ratings is poor compaired to the tuned user-user model

Next, I ran GridsearchCV to to search for the optimal hyperparameters to tune the item-item model with. The optimal hyperparameter settings after running GridSearch are:

    2.9243151529965794
    {'k': 50, 'min_k': 3, 'sim_options': {'name': 'cosine', 'user_based': False}}

**Model Metrics for item-item model after rerunning with the tuned paramters**

    RMSE: 2.9040
    MAE:  2.3017
                 algorithm      rmse       mae  precision  recall  f1_score  \
    0             KNNbasic  3.185239  2.575525      0.682   0.772     0.724   
    1       KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745   
    2        KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695   
    3  KNNbasic_item_tuned  2.903997  2.301706      0.688   0.785     0.733   
    



predictions using knn.KNNBasic_item tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 4.61
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 4.44
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 4.72



**Observations and Insights:**
- The RMSE decreased slightly after tuning
- The MAE has increased slightly
- The f1 score increased  
- The popularity is the same
- similar to the untuned item-item model, our predictions are rather poor
- In general, the predicted ratings of all the songs are about the same as the untuned model
- Given that all of these songs are quite different, these predictions may not reflect the users actually taste. 


The final, weighted, recommendations from the Item-Item similarity-based recommendation system for user '6ccd111af9b4baa497aacd6d1863cbf5a141acc6' are:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ni Tú Ni Nadie (Versión Demo)</td>
      <td>Alaska Y Dinarama</td>
      <td>31</td>
      <td>10.000000</td>
      <td>9.820395</td>
    </tr>
    <tr>
      <th>1</th>
      <td>My Perfect Cousin</td>
      <td>The Undertones</td>
      <td>21</td>
      <td>9.842105</td>
      <td>9.623887</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Walk On Water Or Drown (Album)</td>
      <td>Mayday Parade</td>
      <td>24</td>
      <td>9.684211</td>
      <td>9.480086</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Docking Bay 94</td>
      <td>The Alter Boys</td>
      <td>25</td>
      <td>9.661287</td>
      <td>9.461287</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Waters Of Nazareth (album version)</td>
      <td>Justice</td>
      <td>29</td>
      <td>9.210526</td>
      <td>9.024831</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Valentine</td>
      <td>Justice</td>
      <td>24</td>
      <td>8.934211</td>
      <td>8.730086</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Please_ Before I Go</td>
      <td>Derek Webb</td>
      <td>32</td>
      <td>8.905551</td>
      <td>8.728775</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Hitsville U.K.</td>
      <td>The Clash</td>
      <td>25</td>
      <td>8.421053</td>
      <td>8.221053</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Go Places</td>
      <td>The New Pornographers</td>
      <td>20</td>
      <td>8.342105</td>
      <td>8.118498</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Uptown</td>
      <td>Drake / Bun B / Lil Wayne</td>
      <td>24</td>
      <td>8.061607</td>
      <td>7.857483</td>
    </tr>
  </tbody>
</table>
</div>



**Observations and Insights:**
- Interestingly, the item-item model recommends a completely different top 10 songs than the user-user model

### Model Based Collaborative Filtering - Matrix Factorization

Model-based Collaborative Filtering is a **personalized recommendation system**, the recommendations are based on the past behavior of the user and it is not dependent on any additional information. It uses **latent features** to find recommendations for each user. Here I am using Singular Value Decomposition (SVD) method from the Suprise library, and calculate the metrics after running the base model with default settings:

    RMSE: 2.7215
    MAE:  2.1682
                 algorithm      rmse       mae  precision  recall  f1_score  \
    0             KNNbasic  3.185239  2.575525      0.682   0.772     0.724   
    1       KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745   
    2        KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695   
    3  KNNbasic_item_tuned  2.903997  2.301706      0.688   0.785     0.733   
    4                  SVD  2.721453  2.168153      0.696   0.798     0.744   
    



predictions using SVD tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 8.95
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 2.06
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 5.39


**Observations and Insights:**
- The SVD model has the best RMSE and MAE of any models yet
- The f1 score is higher than any other untuned models
- The popularity of recommended songs is far higher than the other models
- The predictions for the heard song with rating 10 is 8.95
- The predictions for the heard song with rating 1 is 2.06
- The prediciton for the unheard song is 5.39
- These are the most accurate predictions yet of any of the models

#### Improving matrix factorization based recommendation system by tuning its hyperhyperparameters

To tune the SVD model, first I run a factor checking function that plots the RMSE based on a range of latent features. 


<script src="https://gist.github.com/benjamin-j-cooper/d0533b9031797192afcdd43261b8829c.js"></script>


Here is the plot for this data run for 100 features:


    
![png](assets/images/rs_files/recommender_system_129_0.png)
    


According to the figure, there is a decreasing trend of better performance with higher k. The lowest RMSE is achieved when k is 80. However, it is worth mentioning that k = 52 and >84 are also good. The result suggests a range of values which can be used in GridSearchCV()for hyperparameter tunning. Next I ran GridSearchCV to find the optimal hyperparameter settings. The hyperparameter settings for the model that reduced RMSE the most are:

    2.7097656150739744
    {'n_epochs': 30, 'lr_all': 0.01, 'reg_all': 0.4, 'n_factors': 80}

**Model Metrics for Matrix Factorization (SVD) method after rerunning with the tuned paramters**

    RMSE: 2.6736
    MAE:  2.1434
                 algorithm      rmse       mae  precision  recall  f1_score  \
    0             KNNbasic  3.185239  2.575525      0.682   0.772     0.724   
    1       KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745   
    2        KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695   
    3  KNNbasic_item_tuned  2.903997  2.301706      0.688   0.785     0.733   
    4                  SVD  2.721453  2.168153      0.696   0.798     0.744   
    5            SVD_tuned  2.673590  2.143426      0.694   0.799     0.743   



predictions using SVD tuned tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 8.22
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 4.71
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 5.13


**Observations and Insights:**
- The tuned SVD model has a slightly lower RMSE and MAE than the base SVD model
- the f1_score of the the tuned SVD model increased .01
- The popularity of the tuned model dropped significantly
- The popularity of the base model may have been affected by a single highly rated song.
- The predictions for the heard song with rating 10 is about the same as the untuned model
- the prediction for the heard song with rating 1 came up a bit to 2
- In general the predicted ratings are much better than the non matrix factorization models, but tuning the SVD model did not improve performance much if at all.


Since the untuned SVD model had predictions that were the closest to the users actually play counts, Im going to look at the weighted recommendations for both the default and tuned SVD algorithms. The final, weighted, recommendations from default SVD matrix factorization algorithm for user '6ccd111af9b4baa497aacd6d1863cbf5a141acc6' are:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Catch You Baby (Steve Pitron &amp; Max Sanna Radio...</td>
      <td>Lonnie Gordon</td>
      <td>616</td>
      <td>10.000000</td>
      <td>9.959709</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Clara meets Slope - Hard To Say</td>
      <td>Clara Hill</td>
      <td>89</td>
      <td>9.879379</td>
      <td>9.773379</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Make Her Say</td>
      <td>Kid Cudi / Kanye West / Common</td>
      <td>156</td>
      <td>9.186673</td>
      <td>9.106609</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Something (Album Version)</td>
      <td>Jaci Velasquez</td>
      <td>95</td>
      <td>8.532769</td>
      <td>8.430171</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Electric Feel</td>
      <td>MGMT</td>
      <td>179</td>
      <td>8.380396</td>
      <td>8.305653</td>
    </tr>
    <tr>
      <th>5</th>
      <td>He's A Pirate</td>
      <td>Klaus Badelt</td>
      <td>20</td>
      <td>8.514556</td>
      <td>8.290949</td>
    </tr>
    <tr>
      <th>6</th>
      <td>221</td>
      <td>keller williams</td>
      <td>51</td>
      <td>8.379492</td>
      <td>8.239464</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Gunn Clapp</td>
      <td>O.G.C.</td>
      <td>86</td>
      <td>8.313128</td>
      <td>8.205295</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Call It Off (Album Version)</td>
      <td>Tegan And Sara</td>
      <td>66</td>
      <td>8.098702</td>
      <td>7.975610</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Girls</td>
      <td>Death In Vegas</td>
      <td>25</td>
      <td>8.072738</td>
      <td>7.872738</td>
    </tr>
  </tbody>
</table>
</div>



And the Tuned recommendations:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False Pretense</td>
      <td>The Red Jumpsuit Apparatus</td>
      <td>21</td>
      <td>7.612781</td>
      <td>7.394563</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sorrow (1997 Digital Remaster)</td>
      <td>David Bowie</td>
      <td>77</td>
      <td>6.734795</td>
      <td>6.620835</td>
    </tr>
    <tr>
      <th>2</th>
      <td>I'd Hate To Be You When People Find Out What T...</td>
      <td>Mayday Parade</td>
      <td>21</td>
      <td>6.831190</td>
      <td>6.612972</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Recado Falado (Metrô Da Saudade)</td>
      <td>Alceu Valença</td>
      <td>143</td>
      <td>6.648431</td>
      <td>6.564807</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Q-Ball</td>
      <td>Brotha Lynch Hung</td>
      <td>33</td>
      <td>6.705204</td>
      <td>6.531126</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Underground</td>
      <td>Eminem</td>
      <td>24</td>
      <td>6.631778</td>
      <td>6.427654</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Cold Blooded (Acid Cleanse)</td>
      <td>The fFormula</td>
      <td>38</td>
      <td>6.565968</td>
      <td>6.403747</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Walk Through Hell (featuring Max Bemis Acousti...</td>
      <td>Say Anything</td>
      <td>31</td>
      <td>6.578550</td>
      <td>6.398944</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Night Village</td>
      <td>Deep Forest</td>
      <td>20</td>
      <td>6.575026</td>
      <td>6.351420</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Drive</td>
      <td>Savatage</td>
      <td>24</td>
      <td>6.539166</td>
      <td>6.335042</td>
    </tr>
  </tbody>
</table>
</div>



**Observations and Insights:**
- The recommended songs from the tuned svd model are much different than the untuned svd model
- In general, it seems that the tuned model is recommending less popular songs

### Cluster Based Recommendation System

In **clustering-based recommendation systems**, we explore the **similarities and differences** in people's tastes in songs based on how they rate different songs. We cluster similar users together and recommend songs to a user based on play_counts from other users in the same cluster. After running the Coclustering method with default settings, the metrics compared to the other models are:

    RMSE: 2.9591
    MAE:  2.2116
                 algorithm      rmse       mae  precision  recall  f1_score  \
    0             KNNbasic  3.185239  2.575525      0.682   0.772     0.724   
    1       KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745   
    2        KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695   
    3  KNNbasic_item_tuned  2.903997  2.301706      0.688   0.785     0.733   
    4                  SVD  2.721453  2.168153      0.696   0.798     0.744   
    5            SVD_tuned  2.673590  2.143426      0.694   0.799     0.743   
    6         CoClustering  2.959111  2.211564      0.622   0.666     0.643   


predictions using SVD tuned tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 4.71
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 4.00
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 3.17


**Observations and Insights:**
- The clustering model has an RMSE of 2.9 and MAE of 2.2
- The f1 score is .643
- Overal the clustering metrics are performing similarly slightly poorer compared to other models
- The predicted rating for the song with rating 10 is 4.71
- The predictions for the other heard song with raitng 1 is 4

Next, I run GridsearchCV on the clustering-based recommendation system to tune its hyper-hyperparameters. The optimal hyperhyperparameters suggested by the search are:

    3.0094114249385258
    {'n_cltr_u': 3, 'n_cltr_i': 3, 'n_epochs': 40}


**The model metrics after rerunning coclustering with the tuned hyperparamters**

    RMSE: 2.9613
    MAE:  2.2139
                 algorithm      rmse       mae  precision  recall  f1_score  \
    0             KNNbasic  3.185239  2.575525      0.682   0.772     0.724   
    1       KNNbasic_tuned  2.830942  2.254989      0.698   0.799     0.745   
    2        KNNbasic_item  2.998977  2.254952      0.658   0.736     0.695   
    3  KNNbasic_item_tuned  2.903997  2.301706      0.688   0.785     0.733   
    4                  SVD  2.721453  2.168153      0.696   0.798     0.744   
    5            SVD_tuned  2.673590  2.143426      0.694   0.799     0.743   
    6         CoClustering  2.959111  2.211564      0.622   0.666     0.643   
    7   CoClustering_tuned  2.961292  2.213922      0.622   0.666     0.643   


predictions using SVD tuned tuned for user 6ccd111af9b4baa497aacd6d1863cbf5a141acc6:
- prediction for Red Dirt Road by Brooks and Dunn: r_ui = 10.00   est = 4.7
- predictions for Till I collapse by Eminem and Nate Dogg: r_ui = 1.00   est = 3.99
- prediction for SOTTGXB12A6701FA0B by Phoenix (other pheonix songs are 7.6): r_ui = None   est = 3.23

**Observations and Insights:**
- Tuning the clustering model has not improved it, or only marginally
- The prediction for the heard song with rating 10 is 4.7

The final, weighted, recommendations from the tuned coclustering algorithm for user '6ccd111af9b4baa497aacd6d1863cbf5a141acc6' are:

<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Love Is Gone (Original Mix)</td>
      <td>David Guetta - Joachim Garraud - Chris Willis</td>
      <td>20</td>
      <td>8.561523</td>
      <td>8.337917</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cold Blooded (Acid Cleanse)</td>
      <td>The fFormula</td>
      <td>38</td>
      <td>8.275809</td>
      <td>8.113588</td>
    </tr>
    <tr>
      <th>2</th>
      <td>The World Is Mine</td>
      <td>David Guetta</td>
      <td>21</td>
      <td>8.056761</td>
      <td>7.838544</td>
    </tr>
    <tr>
      <th>3</th>
      <td>What Is Light? Where Is Laughter? (Album Version)</td>
      <td>Twin Atlantic</td>
      <td>20</td>
      <td>7.872448</td>
      <td>7.648841</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Kelma</td>
      <td>Rachid Taha</td>
      <td>58</td>
      <td>7.642269</td>
      <td>7.510962</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Love Is Not A Fight</td>
      <td>Warren Barfield</td>
      <td>36</td>
      <td>7.561523</td>
      <td>7.394857</td>
    </tr>
    <tr>
      <th>6</th>
      <td>I Wonder Why</td>
      <td>Dion &amp; The Belmonts</td>
      <td>41</td>
      <td>7.517873</td>
      <td>7.361699</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Hasta siempre</td>
      <td>Varios</td>
      <td>20</td>
      <td>7.552595</td>
      <td>7.328988</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Numb (Album Version)</td>
      <td>Disturbed</td>
      <td>68</td>
      <td>7.418666</td>
      <td>7.297398</td>
    </tr>
    <tr>
      <th>9</th>
      <td>221</td>
      <td>keller williams</td>
      <td>51</td>
      <td>7.411147</td>
      <td>7.271119</td>
    </tr>
  </tbody>
</table>
</div>



**Observations and Insights:**
- Ther top 10 recommended songs are similar to the user-user and SVD models

### Content Based Recommendation System

So far I have only used the play_count of songs to find recommendations but there are other information/features on songs as well, and these features can be used to increase the personalization of the recommendation system. For example, we can use the artist name and album title to recommend songs to users from artists/albums they like but songs they have not heard yet. We can also include the year the song was released and recommend music from the same time period. Here are the main functions I used for the content model:


<script src="https://gist.github.com/benjamin-j-cooper/ab20e9c29b12c86e354f77cfefdc036e.js"></script>


Before Running any of the content based models, I preprocessed the text data by tolkenizing it with natural language processing methods that come standard in the NLTK package. First, I coded the year column into text:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>song_id</th>
      <th>artist_name</th>
      <th>release</th>
      <th>year</th>
      <th>year_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SODGVGW12AC9075A8D</td>
      <td>Justin Bieber</td>
      <td>My Worlds</td>
      <td>2010</td>
      <td>twothousandtens</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SODGVGW12AC9075A8D</td>
      <td>Justin Bieber</td>
      <td>My World 2.0</td>
      <td>2010</td>
      <td>twothousandtens</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SOEPZQS12A8C1436C7</td>
      <td>Deadmau5</td>
      <td>Ghosts 'n' Stuff</td>
      <td>2009</td>
      <td>twothousandzeros</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SOGDDKR12A6701E8FA</td>
      <td>Eminem / Hailie Jade</td>
      <td>The Eminem Show</td>
      <td>2006</td>
      <td>twothousandzeros</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SOWGXOP12A6701E93A</td>
      <td>Eminem</td>
      <td>Without Me</td>
      <td>2002</td>
      <td>twothousandzeros</td>
    </tr>
  </tbody>
</table>
</div>


Then I combined all of the text features into a single column 'text':



<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year_text</th>
      <th>text</th>
    </tr>
    <tr>
      <th>song_id</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>SODGVGW12AC9075A8D</th>
      <td>twothousandtens</td>
      <td>Justin Bieber My Worlds twothousandtens</td>
    </tr>
    <tr>
      <th>SODGVGW12AC9075A8D</th>
      <td>twothousandtens</td>
      <td>Justin Bieber My World 2.0 twothousandtens</td>
    </tr>
    <tr>
      <th>SOEPZQS12A8C1436C7</th>
      <td>twothousandzeros</td>
      <td>Deadmau5 Ghosts 'n' Stuff twothousandzeros</td>
    </tr>
    <tr>
      <th>SOGDDKR12A6701E8FA</th>
      <td>twothousandzeros</td>
      <td>Eminem / Hailie Jade The Eminem Show twothousa...</td>
    </tr>
    <tr>
      <th>SOWGXOP12A6701E93A</th>
      <td>twothousandzeros</td>
      <td>Eminem Without Me twothousandzeros</td>
    </tr>
  </tbody>
</table>
</div>


I then calculated a tf-idf matrix and calculated the cosign similarity. 


<script src="https://gist.github.com/benjamin-j-cooper/757aa09d34a886cde387d1ed4635b3fe.js"></script>


The Recommendations using this method are:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Cats In The Cradle</td>
      <td>Ugly Kid Joe</td>
      <td>30</td>
      <td>7.789474</td>
      <td>7.606899</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cold Blooded (Acid Cleanse)</td>
      <td>The fFormula</td>
      <td>38</td>
      <td>7.000000</td>
      <td>6.837779</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Hold Me_ Thrill Me_ Kiss Me_ Kill Me</td>
      <td>U2</td>
      <td>33</td>
      <td>6.770725</td>
      <td>6.596648</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Twilight Galaxy</td>
      <td>Metric</td>
      <td>28</td>
      <td>6.696697</td>
      <td>6.507715</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Last Nite</td>
      <td>The Strokes</td>
      <td>21</td>
      <td>6.724206</td>
      <td>6.505988</td>
    </tr>
    <tr>
      <th>5</th>
      <td>The Calculation (Album Version)</td>
      <td>Regina Spektor</td>
      <td>44</td>
      <td>6.636842</td>
      <td>6.486086</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Mansard Roof (Album)</td>
      <td>Vampire Weekend</td>
      <td>26</td>
      <td>6.587426</td>
      <td>6.391310</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Face To Face</td>
      <td>Daft Punk</td>
      <td>32</td>
      <td>6.525241</td>
      <td>6.348465</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Injection</td>
      <td>Rise Against</td>
      <td>23</td>
      <td>6.485387</td>
      <td>6.276872</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Chinese</td>
      <td>Lily Allen</td>
      <td>14</td>
      <td>6.092105</td>
      <td>5.824844</td>
    </tr>
  </tbody>
</table>
</div>



**Observations and Insights:**
- This is excellent, we are recommending songs by the same artists/albums the user has likes and adding in some weight for the decade of the users song preferences. 
- We are also ranking the recommendations based on song popularity, so more listened to songs by other users will be weighted heavier for this user

### hybrid recommendation system
I have explored five different recommender methods (six if you include the popularity-based method) for recommending songs to a user in a personalized way. This is all well and good, but how do we know which method is recommending songs the user will actualy listen to? As an avid listener of music, is it not also true that a users preferences can change, and may change drastically during the day or from day to day? It also seems that the models we have presented so far sometimes recommend similar songs, but other models are drastically different as in the item-item recommendations and content based recommendations. In this section, I build a hybrid recommender system which takes into account recommendations from multiple models, applys weights based on which models we want to be most represented in the results, and then provides a 'hybrid' recommendation. 

In my hybrid system, I fit models and make predictions by combing two of the previously evaluated models:
- SVD (default settings)
- User-User collaborative Filtering (tuned)<br>



<script src="https://gist.github.com/benjamin-j-cooper/7c018c0c143dac2f2b86e263bdeb698d.js"></script>



I chose these two models because both had the best F1_scores metrics, both had fairly good predictions, and both recommended markedly different songs. I then add in a subset of recommendations from the content-based filtering method to increase the 'familiarity' for the user of the recommended songs/artists. This will hopefully provide a highly personalized recommendation for a user with a balance of new songs and familiar artists to give choices based on potential dynamic user preferences. I also evaluated the performance of different weight combinations using the hold-out set. For example, we can try different combinations of wA and wB for the SVD and User-User model combination, ranging from (0.1, 0.9) to (0.9, 0.1), and compute their respective RMSE scores:


<script src="https://gist.github.com/benjamin-j-cooper/0eb3455fc8709ac6fcbe5b3d507f409f.js"></script>


    RMSE: 2.7976
    MAE:  2.2302
    Weight combination (0.1, 0.9): RMSE = 2.7976, MAE = 2.2302
    RMSE: 2.7495
    MAE:  2.1971
    Weight combination (0.3, 0.7): RMSE = 2.7495, MAE = 2.1971
    RMSE: 2.7186
    MAE:  2.1749
    Weight combination (0.5, 0.5): RMSE = 2.7186, MAE = 2.1749
    RMSE: 2.7057
    MAE:  2.1634
    Weight combination (0.7, 0.3): RMSE = 2.7057, MAE = 2.1634
    RMSE: 2.7110
    MAE:  2.1619
    Weight combination (0.9, 0.1): RMSE = 2.7110, MAE = 2.1619


**Observations and Insights:**
- there is not much difference in RMSE for the different combinations of model weights
- The 'best' weight combination is SVD .7 - collaborative filtering .3

## **Conclusion and Recommendations**

**1. Comparison of various techniques and their relative performance based on chosen Metric (Measure of success)**:
- In General the Method 2 dataset had better MSE and MAE than the method 1 dataset, but the Method 1 dataset had better f1_score and the predictions for listened to songs were closer to the actual playcounts
- The SVD and user-user based models performed the best according to RMSE, MAE, and f1
- The item-item model recommended different songs that the SVD, clustering, and user-user
- In general, tuning the models did improve their performance, however it became clear that one of the biggest effects on model performance is the data going into the model. 
- The Content based recommender system, just based on artist name, album title and year does a decent job of recommending artists the user likes, and songs from albums the user has listened to.
- Many of the songs in the SVD,clustering, collaboritive filtering recommendations were not artists in the users top listened artist/song list, therefore I added the Content Based Recommendations into the hybrid recommender system.
- I chose to tune my hybrid recommendation system using SVD with default settings because it was the best performing model, and user-user collaborative Filtering model. Combining these added more potential song diversity that might align with the user preferences into the final recommendation. 
- I also added content-based recommendations into the hybrid model for 'familiarity'
- There is room for improvement in the performance of the models and final recommender system:
 - more features such as genre, loudness, danceability, and lyrics could be added as features to improve Content based recommendations
 - Further improvement could be made on filtering/scaling the play_counts to achieve better predictions
 - A different approach could be tried, such as Neural Networks

**2. Refined insights**:
- The impact of the Y variable - in this case play_count - cannot be understated. 
- The distribution and scarcity in the play_counts, and how I chose to filter and transform it had large impacts on the model performance
- The Content-based recommender system, although perhaps the 'simplist' of the models besides the popularity based recommender system, performs predictably and precisely recommends songs based on content
- matrix factorization outperformed other models. It runs quickly, and while it has only marginally better performace metrics than other collaborative or cluster-based models, its predictions were the closest to actual.
- The metrics you choose to assess model performance with are extremely important. depending on the metrics you choose, they can change the decisions you make about models and recommendations.

**3. Proposal for the final solution design:** 
- I am proposing the hybrid recommender system I built be adopted. It provides a good balance of artists/albums the user is known to like, but may not have listened to other songs of, and new content recommended by usesr-user collaborative filtering and matrix factorization,
- In short, it is highly personalized!
- This hybrid recommender system could be adjusted and improved further based on more features for content-based recommending or alternative compositions of models/weights

**Final 10 song recommendation for user 6d625c6557df84b60d90426c0116138b617b9449:** 



<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist_name</th>
      <th>count_plays</th>
      <th>predicted_interaction</th>
      <th>corrected_ratings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Clara meets Slope - Hard To Say</td>
      <td>Clara Hill</td>
      <td>89</td>
      <td>9.677092</td>
      <td>9.571092</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Catch You Baby (Steve Pitron &amp; Max Sanna Radio...</td>
      <td>Lonnie Gordon</td>
      <td>616</td>
      <td>8.470891</td>
      <td>8.430600</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Make Her Say</td>
      <td>Kid Cudi / Kanye West / Common</td>
      <td>156</td>
      <td>7.772713</td>
      <td>7.692649</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Cats In The Cradle</td>
      <td>Ugly Kid Joe</td>
      <td>30</td>
      <td>7.789474</td>
      <td>7.606899</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Recado Falado (Metrô Da Saudade)</td>
      <td>Alceu Valença</td>
      <td>143</td>
      <td>7.642525</td>
      <td>7.558901</td>
    </tr>
    <tr>
      <th>5</th>
      <td>#40</td>
      <td>DAVE MATTHEWS BAND</td>
      <td>72</td>
      <td>7.661807</td>
      <td>7.543956</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Walk Through Hell (featuring Max Bemis Acousti...</td>
      <td>Say Anything</td>
      <td>31</td>
      <td>7.678929</td>
      <td>7.499324</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Eternal Flame (Single Version)</td>
      <td>Atomic Kitten</td>
      <td>49</td>
      <td>7.411352</td>
      <td>7.268495</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Cold Blooded (Acid Cleanse)</td>
      <td>The fFormula</td>
      <td>38</td>
      <td>7.000000</td>
      <td>6.837779</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Hold Me_ Thrill Me_ Kiss Me_ Kill Me</td>
      <td>U2</td>
      <td>33</td>
      <td>6.770725</td>
      <td>6.596648</td>
    </tr>
  </tbody>
</table>
</div>


# References
1. Thierry Bertin-Mahieux, Daniel P.W. Ellis, Brian Whitman, and Paul Lamere. The Million Song Dataset. In Proceedings of the 12th International Society for Music Information Retrieval Conference (ISMIR 2011), 2011.
