# ETL Project

####"Report on the ETL Project"

Andrade, Jose (Tobi)

Sotomayor, Tyler

### Background

For this project we chose to look at gun violence and how it relates to gun ownership and educational attainment throughout the United States. 

## EXTRACT

### Data Sources
	
Our first data set on gun violence was found through Kaggle and came from the Gun Violence Archive (GVA) a not-for-profit corporation formed in 2013 to provide free online public access to accurate information about gun-related violence in the United States. The data was originally collected by web scraping gunviolencearchive.org and compiled into .csv file format.

Our second data set on gun ownership was found through Kaggle and came from thoughtco.com. It is based on 2017 gun registration statistics from the ATF and the Pew Research Center and was compiled by HuntingMark.com. It is important to note that there is no way to get a precise account of gun ownership in the United States on a state-by-state basis. This is due in large part to lack of national standards for licensing and registering firearms. The data set was in .csv file format.

The third data set on educational attainment was found through Kaggle and came from Wikipedia which sourced from the 2013-2017 American Community Survey 5 -Year Estimates conducted by the U.S. Census Bureau in .csv file format.

The fourth data set was a population estimate conducted by the U.S. Census Bureau in .csv file format. 

## TRANSFORM

### Data Transformation and Narrowing

The data set on gun violence in America was a 150 mb .csv file that needed to be split into two smaller files in order to upload to github.com. This was achieved by calculating the length of the file and dividing it by 2 using Pandas.  The csv was split into 2 separate files and was then read into pandas simultaneously for more data cleaning. The data set contained many fields such as date, multiple location fields, number killed, number injured, and demographics of participants. First, duplicates were dropped. Second, concerned only with 2017, we filtered for data entries that occurred after 2016-12-31. Lastly, we filtered by State, and number killed and injured.  This would allow us to compare by “State” and have a human component to how many were affected by gun violence.
	
The data set on gun ownership in America contained 3 fields: “State”, “number of guns per capita”, and “number of guns registered.” It did not require any further cleaning. The 

Likewise, the data set on educational attainment required no further cleaning. It had 4 fields: “State”, “% of high school graduates,” “% of bachelor’s degrees,” and “% of advanced degree.”

The last data set contained fields on national population totals, population change, and the components of population change. Using Pandas, this data was focused to 2 fields: “State” and “POPESTIMATE2017”, the latter being a population estimate for 2017. Since we had percentage per capita metrics on the gun ownership data we thought it would be good to cross-reference in analysis with population totals for every state.

## LOAD

### Loading data into SQLite3

We chose to load our data into a SQLite database because it is a relational database and we had multiple tables of different data (gun ownership, population,  gun violence, and educational attainment) which all had the same data point of “State”. Furthermore, it is a good embedded database which we could implement nicely in a website or application. We used the SQLAlchemy module and the “.to_sql” function to load each of our datasets into a created “gun_stats_db” database within the SQLite3 database system. From here we could perform simple queries and compare these metrics by states into beautiful visualizations. 
