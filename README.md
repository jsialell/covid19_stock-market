# Impact of Coronavirus on the global economy

## Content
- [Project Description](#project-description)
- [Gathering Data & Limitations](#gathering-data-&-limitations)
- [Assumptions](#assumptions)
- [Data Cleaning & Merging](#data-cleaning-&-merging)
- [Results](#results)
- [Conclusions](#conclusions)
- [Future Questions](#future-questions-&-improvements)
- [Files](#files)
- [Resources](#resources)

## Project Description  
For this project we studied the impact of coronavirus on the global economy. For this, we looked at the most popular stock markets in the world and decided to study 7 countries: China, France, Germany, Japan, Italy, Spain and the US.
We started by analyzing 9 stock market indexes for these countries, in which three of them belonged to the US, and finally deciding on the following indexes:
* SSE - China
* CAC 40 - France
* DAX 30 - Germany
* NIKKEI 225 - Japan
* FTSE MIB - Italy
* IBEX 35 - Spain
* DOW JONES - US


## Gathering Data & Limitations
### Coronavirus
* Johns Hopkins Resource Center
    1. Coronavirus daily cumulative recorded cases for each country
    2. Coronavirus daily cumulative recorded deaths for each country
* Coronavirus COVID 19 API
    1. First recorded case per country
    
Due to the fact that Johns Hopkins data started from 22-01-2020, we went to the API in order to obtain the first recorded cases, which demonstrated that China began with 548 cases on 22-01-2020, meaning that they first started to record data on this day.

### Stock Market Values
* We gather daily stock market values from 2019 to 07-04-2020 for the indexes mentioned previously from the following websites:
    1. Macrotrends (France, Germany, Japan, USA)
    2. Investing (Spain, Italy)
    3. Yahoo Finance (China)
    
* Stock Market APIs
    We weren't able to use API for the gathering of stock market data because we needed premium accounts in order to access historical data,
    the requests results returned "None" values.

## Assumptions
   1. The indexes used truly reflect the development of the financial market. 
   2. There is a correlation between the financial index and the development of the pandemic. 


## Data Cleaning & Merging
### Finance
   1. Some of the data included highest and lowest daily values for the index, for first we got an average daily value in order to have a Data Frame with dates and values for each index.
   2. The format was changed to date format for the dates and to float for the values.
   3. The tables for each index were merged together with the date key.
   4. After merging, there were a lot of null values during the same dates which were weekends. For this, the data was interpolated to fill up the null values.
   5. A calculation was made to get the percentage of increase or decrease for each index using the 7-01-2020 as a base value. We decided on this date because it was the first data recorded for most of the indexes, due to the fact that before that New Year was celebrated and a weekend followed.
   6. A new Data Frame showing a summary of the normalized index values with the minimum, maximum and newest value for each of them.

### Coronavirus
   1. The data obtained from the Johns Hopkins Data Center was daily cumulative values of recorded cases for each country. First, the data was grouped by the countries for this project, adding the values for each date.
   2. The same process was made for the daily cumulative recorded death cases.
   3. A function was defined in order to calculate the daily new cases for each country, creating a new Data Frame for daily cases recorded.
   4. Columns for the total recorded cases and total deaths for each country were added.
   5. A third column with the actual 2020 population for each country was added, in order to create a new column with the deaths per 1 million habitants for each country. 
   6. The following summary Data Frames were created:
        * Total cases per country
        * Maximum daily cases recorded per country
        * Total cases, total deaths and deaths per 1 million per country

### Plotting
The plots mentioned are shown on the slides presentation for better visualization.

* Finance
    - A figure was made containing 7 axes to plot line graphs for the dates vs. the percentage increase/decrease of the value for each country.
*Coronavirus
    - A figure was made containing 7 axes to plot bar graphs for better representations for the dates vs. the covid daily cases for each country.
*Merging
    - Both final Data Frames were merged together in order to present both data in one graph (dual plotting). This merging was done with the date key.
    - On these graphs the stock market normalized values are represented in color red, and the coronavirus daily cases are represented in blue.

## Results
* All financial indexes analysed (except the Chinese index) followed a similar pattern and they all started to decrease by mid of February. 
* CAC 40 (France) suffered the greatest loss of almost 40%. FTSE (Italy) went through significant ups and downs and it even had the greatest gain of 7% compared to the other indexes. 
* As of today, IBEX (Spain) has suffered the most (0,73 compared to 07-01-2020). And SSE (China) is doing the best (0,91 compared to 07-01-2020). 
* The number of confirmed cases of covid-19 over time followed a cluster approach for the countries considered: first China, second Europe and then the US.
* Until now (10-04-2020), the countries most affected in terms of deaths due to covid-19 are: Spain, Italy and France and to a lesser degree Germany, the US and China (number of deaths for 1 million inhabitants).

## Conclusions  
* The stock market is plummeting as the number of covid-19 cases is increasing globally.
* Most national stock market indexes dropped a few days before the actual drastic increase of confirmed cases for each country. It seems that the global economy and the stock market were anticipating measures of confinement and loss of economic activities before governments even started to take actions.  
* The stock market index considered for China (Shanghai Stock Exchange, SSE) did not decrease as much as other national indexes. This is likely due to the fact that China has a more regulated financial and economical systems than the other countries studied for this project.



## Future Questions & Improvements

* Further industrial specific indexes could be analysed to better understand the impact of the pandemic on particular industries, e.g. tourism. 
* More in-depth understanding of the Chinese financial market could help us to better understand why the Chineses index performed differently compared to all others. 
* Include further countries for which the number of confirmed cases starts to increase at a later date.
* Follow-up on the evolution of the stock market indexes if/when economic stimulus programs are adopted (e.g. Eurobonds). 


## Files
- [Data](https://github.com/jsialell/covid19_stock-market/tree/master/data)
- [Notebooks](https://github.com/jsialell/covid19_stock-market/tree/master/Jupyter_Notebooks)
- [Slides](https://github.com/jsialell/covid19_stock-market/blob/master/COVID%20vs%20Stock%20Markets.pdf)



## Resources
- [Macrotrends](https://www.macrotrends.net)
- [Yahoo Finance](https://de.finance.yahoo.com)
- [Investing](https://www.investing.com)
- [Coronavirus COVID 19 API](https://documenter.getpostman.com/view/10808728/SzS8rjbc?version=latest#cc76052f-6601-4645-80e5-ca7aaa36f8ef)
- [GitHub Repo of the Johns Hopkins University](https://github.com/CSSEGISandData/COVID--19/tree/master/csse_covid_19_data/csse_covid_19_time_series)