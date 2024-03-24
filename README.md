# ANALYSIS OF INDIAN START-UP FUNDING ECOSYSTEM

This project required that we look into the Indian start-up funding ecosystem from 2018 to 2021.
In order to conduct this analysis, data was sourced from DAP Database, OneDrive, and a github repo.
After collecting the dataset, we had to use the Cross-Industry Standard for Data Mining (CRISP-DM) framework approach to data analysis. It involved the five-fold stages of Business Understanding, Data Understanding, Data Preparation, Analysis, and Deployment. Let’s highlight each stage in the order listed.

## BUSINESS UNDERSTANDING

In the business understanding phase, we had to state out clearly what we intended to achieve.
Per the title of the project, we’re to investigate the Indian start-up funding ecosystem to uncover as much trends that the data reveals for the start-ups and the investors alike. This meant understanding the trends funding amounts, the sectors/industries that received a greater part of the funds, and to uncover the major investors that contributed the most to start-up funding.
Below are our business questions:
- How has the funding trend changed over the years?
- What is the distribution of funding received by industry?
- What cities have attracted the most funding for start-ups?
- Which cities have attracted the most start-ups?
- Who are the major investors in this ecosystem?
- Who are the top investors in the ecosystem, and which industries do they favor?
- Are there any emerging sectors gaining traction by investors?
- Which emerging main sector/industry is gaining traction by investors?
- What are the top three (3) industries to receive funding?
- What are the top three (3) main sectors within the top three (3) industries in terms of frequency?
- Can we identify any correlation between the amount of funding they received and the sector to which they belong?



## DATA UNDERSTANDING

The datasets collected held details of the start-up names, what they do, how much they received in funds, the year they received funding, the stage of their operations when they received funding, the year the start-up commenced business, the industry/sector in which they operate, their official business location, and the investors that granted these start-ups the much needed funds.
For the 2018 dataset, some requisite columns such as sector and headquarter were incorporated into industry and location columns respectively. We had to pick out the specific details needed and thus created the headquarter and sector columns in order for the dataset to be consistent with the datasets for 2019 - 2021. Some columns such as stage and amount had their values wrongly inputed. This was noted ahead of the data cleaning exercise. Also noticed was that the amount column held values of both numerical and categorical types. There were multiple currency symbols found in the amount column. The columns for the datasets covering 2019 to 2021 were in order and so we were ready for data cleaning.  
(a)DATA CLEANING: While the 2019 dataset was downloaded from OneDrive, the 2018 dataset was soucred via a github url link in Pandas. The 2020 and 2021 datasets were first queried from the DAP database using our environment variables and then saved locally. For the data cleaning proper, we had to first take on each dataset one after the other  because we realised that concatenating the datasets before cleaning a singular dataframe proved counter productive.  
    (i)2018 DATASET:
The bulk of work was on the Amount column. Amounts stated in rupees were converted to dollar values using a function, Currency symbols, white spaces, and commas were removed wherever found in the amount column.  
    (ii)2019 DATASET:
The column was renamed to make it consistent with other datasets, amounts stated in rupees were also converted to dollar values in this dataset, characters such as white spaces, commas and currency symbols were all removed from the amount column. The amount values were converted to float data type from object data type.  
    (iii)2020 DATASET:
The “column10” which was found to contain null values only was dropped.  
    (iv)2021 DATASET
No cleaning exercise was conducted on the 2021 dataset.

## DATA PREPARATION

Given the improved state of all four (4) datasets, they were all merged into one dataframe.
Column names were changed from their previous states to “Company_Brand”. “Stage”, “Sector”, “What it does”, and “HeadQuarter”.
Rows with words such as “Undisclosed”, “Upsparks” and others were cleaned out of the concatenated dataframe. Rows with mixed values for amount and stage columns were swapped back to their correct places. The Company_Brand column was cleaned to reflect better case types.  The Sector column was mapped in order to reduce its number of unique categories.
Other columns were cleaned in order to have them standardized, mostly by changing their case types, changing of data type from float to integer, and reducing the number of categories that they hold.
We realised that this was an investigation into start-ups and so had to ensure that the companies did reflect that status by removing companies that had been in existence for longer than 5years.
After all the cleaning exercise was satisfactorily completed, we proceeded to conduct an Exploratory Data Analysis of what was left of the dataframe (which had about 2,144 rows from the initial 2,878 rows).

## DATA ANALYSIS
### (i) UNIVARIATE DATA ANALYSIS

The univariate data analysis for numerical variables can be seen below.

![Univariate Data Analysis](project/univariate.jpg?raw=true "Univariate Data Analysis")

As can be seen from the image above, the Amount variable had a mean value of $101,098,600, with minimum and maximum values of $876 and $150,000,000,000 respectively, as well as a standard deviation of approximately $3,239,380.

The Year variable had a mean of 2020, a minimum and maximum of 2018(the start year) and 2021(the end year), and a standard deviation of 1.

The Years of existence variable had a mean of 3years, a minimum and maximum of 0years and 5years respectively, and a standard deviation of 1.

The distribution of numerical variables is presented in the image below.

![Numerical Variables Distribution](project/numerical_dist.jpg?raw=true "Numerical Variables Distribution")

The Univariate distribution of Main Sector, Industry, Stage, and HeadQuarter variables are presented below

![Main Sector](project/main_sector.jpg?raw=true "Main Sector")

![Distribution of Industry](project/industry.jpg?raw=true "Industry Distribution")

![Distribution of Stage](project/stage_freq.jpg?raw=true "Distribution of Stage")

![Distribution of HeadQuarter](project/hqtr.jpg?raw=true "Distribution of HeadQuarter")


### (ii) BIVARIATE ANALYSIS
We looked into the relationships that exists between some select categorical and numerical variables and present our findings below  

![Main Sector vs Amount](project/top_sector_with_highest_funding.jpg?raw=true "Top Sectors by Amount")  
  
From the image above, Fintech is the Main Sector with the most fundings.  
  
![Main Sector vs Years of Existence](project/successful_start_up_sectors.jpg?raw=true "Main Sector vs Years of Existence")

From the image above, we can see that the top 10 Main Sectors by Years of Existence. They include Transport & Logistics, Fintech, Food & Beverages, Healthtech, Business, E-commerce, Healthcare & Wellness, Technology, Edtech, and Finance in no particular order.


![Industry by Amount](project/industry_by_highest_amount.jpg?raw=true "Industry by Amount")  

The above chart shows Finance as the Top Industry with the highest amount of funding.


![Distribution of Stages by Amount](project/top_funded_stages.jpg?raw=true "Distribution of Stages by Amount")  

The above chart shows the distribution of Stages by the amount of funding received.

## DEPLOYMENT
We attempted to profer solution to the Business questions stated in the Business Understanding section above.
#### (1) HOW HAS THE FUNDING TREND CHANGED OVER THE YEARS?

![Amount by Founding years](project/q3.jpg?raw=true "Funding Trends over Founding years")  

Much of the fundings to start-ups happened in 2021, followed by 2020, then 2018 and finally in 2019. It is not surprising at all. This trend reflects the number of records available for each of those years.

#### (2) WHAT IS THE DISTRIBUTION OF FUNDING RECEIVED BY INDUSTRY?

![Amount by Industry](project/q2.jpg?raw=true "The distribution of funding by Industrys")  

Per the Column Chart above, the bulk of funding goes to the Top Seven Industries which are Finance, Technology, Business, Food & Beverages, Health, Education, and Transport.

#### (3) WHICH CITIES/REGIONS HAVE ATTRACTED THE MOST FUNDING FOR START-UPS?

![Amount by HeadQuarter](project/q4.jpg?raw=true "Distribution of Funding by Cities")  

The top five (5) cities that attract funding to start-ups are Mumbai, Bangalore, New Delhi, Delhi, and Pune. It is clear that locating a start-up in Mumbai would help attract more funds for the business.

#### (4) WHICH CITIES/REGIONS HAVE ATTRACTED THE MOST NUMBER OF START-UPS?

![Distribution of Start-ups by HeadQuarter](project/q5.jpg?raw=true "Distribution of Start-ups by Cities")  

Even though Gurugram did not make the Top five cities that attract fundings for start-ups, it appeared as one of the Top five cities to attract start-ups.  

#### (5) WHO ARE THE MAJOR INVESTORS IN THE ECOSYSTEM?  

![Frequency of Investments by Investors](project/q6.jpg?raw=true "Top 20 Investors in the ecosystem")  

The top investor in the ecosystem is Inflection  Point Ventures, with Titan Capital coming in fifth place. There seems to be some sort of level from Kalaari Capital to Chiratae Ventures. 


#### (6) WHICH INDUSTRIES DO THE TOP THREE INVESTORS PREFER TO INVEST IN?  

![Top 3 industries invested in by Inflection Point Capital](project/q7_1.jpg?raw=true "Top 3 industries invested in by Inflection Point Capital")

The Bar Chart above shows that Inflection Point Capital prefers to invest in start-ups that are found in the Technology, Business, and Education Industries.  

![Top 3 industries invested in by Venture Catalysts](project/q7_3.jpg?raw=true "Top 3 industries invested in by Venture Catalysts")  

Venture Catalysts prefers to invest in start-ups that are associated with the Food & Beverages, Business, and Education industries.

![Top 3 industries invested in by Mumbai Angels Network](project/q7_2.jpg?raw=true "Top 3 industries invested in by Mumbai Angels Network") 

Start-ups that venture into the Transport, Hospitality, and Education industries are favored by Mumbai Angels Network.

## CONCLUSION

Based on the analysis conducted on the Indian start-up funding ecosystem from 2018 to 2021, several key insights and trends have been uncovered.

### FUNDING TRENDS:
- The analysis revealed a significant increase in funding for start-ups over the years, with the highest amount of funding observed in 2021.
- This trend reflects the growing interest and investment in the Indian start-up ecosystem, indicating a positive outlook for the future.

### DISTRIBUTION OF FUNDING BY INDUSTRY:
- The bulk of funding is concentrated in seven key industries: Finance, Technology, Business, Food & Beverages, Health, Education, and Transport.
- This distribution highlights the sectors that are attracting the most investment and may present lucrative opportunities for entrepreneurs and investors alike.

### CITIES ATTRACTING FUNDING:
- Mumbai, Bangalore, New Delhi, Delhi, and Pune emerged as the top cities attracting funding for start-ups.
- Locating a start-up in these cities may provide access to a thriving ecosystem and increased opportunities for funding and growth.

### MAJOR INVESTORS:
- Inflection Point Ventures emerged as the top investor in the ecosystem, followed by other prominent players such as Titan Capital and Kalaari Capital.
- Understanding the preferences of these investors can help start-ups tailor their pitches and strategies to attract funding.

### PREFERRED INDUSTRIES OF TOP INVESTORS:
- Analysis of the investment preferences of top investors revealed their focus on specific industries.
- For example, Inflection Point Ventures showed a preference for Technology, Business, and Education sectors, while Mumbai Angels Network favored Transport, Hospitality, and Education industries.

Finally, the analysis provides valuable insights into the Indian start-up funding ecosystem, highlighting emerging trends, key players, and areas of opportunity. By leveraging these insights, stakeholders can make informed decisions, identify potential investment opportunities, and contribute to the continued growth and success of the Indian start-up ecosystem.


# CONTRIBUTORS

This is an LP1 project completed by  
- [Prince Acquah Rockson](https://github.com/parockson)
- [Etebom Ntuk](https://github.com/netebom)
- [Elvis Obeng](https://github.com/mabrony)
- [Mohammed Idris](https://github.com/Moidris) 
- [Celestine Jerop Kaplelach](https://github.com/cjerop)
- [Andy Konney](https://github.com/drewmacony)
