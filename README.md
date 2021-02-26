<p align="center">
<img src="Data/img/newplot.png"  height="400" width="600" />
</p>

# Spread of Covid-19 in South Korea

## Introduction  

The COVID-19 pandemic in South Korea is part of the worldwide pandemic of Covid-19 disease 2019 caused by SARS-CoV-2. The first case in South Korea was announced on 20 January 2020. The numbers of confirmed cases continuously increased on 19 February by 20, and on 20 February by 58 or 70, giving a total of 346 confirmed cases on 21 February 2020, according to the Korea Disease Control and Prevention Agency, with the sudden jump mostly attributed to "Patient 31" who participated in a gathering at a Shincheonji Church of Jesus the Temple of the Tabernacle of the Testimony church in Daegu. This study aims to address some of the controversial topics related to covid-19 using real world data.

The questions that this study will focus on are:

 * Does Covid-19 affect Women and Men Differently? If yes, how significant?
 * what age groups are most vulnerable? can we use those findings to predict future? If yes, how accurate?
 * what age group are most likely to contract the virus?
 * How likely to spread Covid-19 under different weather conditions?  
 
 ## Raw Data

The data on spread of Covid-19 in South Korea came from Korea Centers for Disease Control & Prevention (http://www.cdc.go.kr/index.es?sid=a2). Then, the data was modified and put it on Kaggle (https://www.kaggle.com/kimjihoo/coronavirusdataset) for study purpose. This is where the data for this project came from. All census data is included in the data folder. 

 ### Data Cleaning Workflow

1. The case data conatained information about more than 65 cities in South Korea, not including information about overseas and immigrants. Plan was to grab only information that needed to visualize the spread of Covid in South Korea. There were some null values that needed to taken care, and the data type of longitude and latitude was object. In order to use object data type in plotly, the change in data type was required from object to float 64. I created some new 2 columns and stored float longitude and latitude in them.

| lat_float         | long_float        |
|------------------:|-------------------|
|  37.538621|26.992652|
|37.482080|26.901384|
|37.508163|126.884387|
|37.546061|126.874209|
|37.679422|127.044374|

2. The gender data set was seperated into two small data sets for work purpose because both male and female were stored in raws rather than columns.

3. Data set age had to be grouped by different age groups. Then, I filtered out confirmed and deceased cases related to age group 80s. Those data columns were used to creat a new data column to determine death rate of each group. what I found was surprising.  


|age|confirmed|deceased|deathrate|
|-----|--------|-----|----------|
|0s|16107|0|0|
|10s|	68752	|0	|0.000000|
|20s|	345827|	0|	0.000000|
|30s|	137539	|194	|0.001411|
|40s	|168250	|295	|0.001753|
|50s	|230030	|1537	|0.006682|
|60s	|158505	|3743	|0.023614|
|70s	|82107	|7599	|0.092550|
|80s	|54086	|12136	|0.224383|


4. The weather data set was grouped by different province in S.Korea, and decided to create a new data frame that includes average weather conditions for each province. Then, I decided to combine that new dataframe with average cases in each province.

	|province|confirmed|	avg_temp|	precipitation|	max_wind_speed|	avg_relative_humidity|
 |..........|........|.........|................|............|......................|
 |Busan|156|15.16|1.9|6.4|62.8|
 |Chungcheongbuk-do|60|11.9|1.25|3.9|64.89

