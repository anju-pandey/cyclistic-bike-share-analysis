# cyclistic-bike-share-analysis
###### Analysis of how annual members and casual riders use Cyclistic bikes differently

**Introduction & Objective:**
This case study was performed as capstone project for the “Google Data Analytics Professional Certificate” course. 
Cyclistic, a bike-share company in Chicago is a fictional company. This analysis is done to know how do annual members and casual riders use Cyclistic bikes differently?
The company has 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. They offer many flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.
 They want to Design marketing strategies aimed at converting casual riders into annual members. To do that, they need to better understand how annual members and casual riders differ.
 **Our objective is to analyze the Cyclistic historical bike trip data to identify trends and usage behavior of annual members and casual riders.**

**About Data:**
We are going to use the company’s historical data i.e. year 2019 to analyze and identify trends, if exists.
The data has been made available by Motivate International Inc. under this license.) This is public data.
Data is stored as comma separated files. This <a href='https://divvy-tripdata.s3.amazonaws.com/index.html'>link</a> can be used to download the files. Files used for this study are:
 Divvy_Trips_2019_Q1.zip
 Divvy_Trips_2019_Q2.zip
 Divvy_Trips_2019_Q3.zip 
 Divvy_Trips_2019_Q4.zip 

**Data preparation and cleaning:**
As data is stored in four files and contain large data, files were imported to Google Bigquery and merged all data to one table. After merging, the available number of records is 3818004.
Following observations were made about data:
-	Trip_id is unique for each record.
-	Birthyear and gender contain null values.
-	End time is smaller than start time for some records.
-	Different station names are being used for one station code.
-	
Actions taken for inconsistency/ambiguity:
-	Unique station name is provided for unique station id.
-	Start_time is updated with end_time and end_time is updated with start_time, wherever it was inconsistent. 
-  	null values are not treated for birthyear and gender as no impact was observed due to its presence.
-	trip duration was calculated by subtracting start time from end time.
-	
**Analyzing data:**
usertype column contains two unique values: Customer and Subscriber. Subscriber is our annual member and Customer is a casual rider.



![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/4cc3c01f-37eb-4e5b-a134-23ae92051b32)






We are going to perform our analysis using the attributes below to check how annual members are different than casual riders.
Age: Is there dominant age group who either prefers to be member or casual rider?
Gender: is there specific gender who is opting for annual membership than being casual rider or vice versa?
Trip Duration: is trip duration the deciding factor for either being member or casual rider?
Weekday: is the day of week of journey differentiating the users?










 
Age
Range	All Users(Casual+Members) (%)	Casual Riders(%)	Annual Members(%)
1-20	1.38	38.13	61.87
21-40	63.81	11.34	88.66
41-60	18.12	6.95	93.05
61-80	2.55	3.74	96.26
81-100	0.01	4.12	95.88
>100	0.02	4.73	95.27
**Null	14.11	98.82	1.18
Age:

























The above chart does not show any trend or pattern which indicates preference towards membership or being casual rider due to age.
** there was no clarification available about missing/null values, hence it is not being considered while plotting the graph.















Gender:
Gender	All Users(Casual+Members) (%)	Casual Riders(%)	Annual Members(%)
Male	62.88	8.86	91.14
Female	22.47	15.32	84.68
** Null	14.65	95.93	4.07

















The above chart does not show any trend or pattern which indicates preference towards membership or being casual rider due to gender.
** there was no clarification available about missing/null values, hence it is not being considered while plotting the graph.





















Trip Duration:
•	Data contains trip durations ranging from 61 second to 123 days.       
•	99.95% trip ends in a day.
•	0.05% of trips are between 2 to 123 days.

	%	Value
Trips ending in a day	99.95	3816155
Trips for more than a day	0.05	1849
Total=	100	3818004












Further we analyzed data for trip durations which end within a day – for both the user types.
 Total no. of casual riders within an hour trip	%	Value
Total no. of casual riders for the rest of the day	83.60	735052
Total no. of casual riders for a day trip	16.40	144237

Total=	100	879289
 Total no. of annual members within an hour trip	%	Value
Total no. of annual members for the rest of the day	99.60	2925122
Total no. of annual members for a day trip	.04	11744

Total=	100	2936866






















o	99.60% of the total numbers of annual members travelling in a day, are using bike service only for less than an hour and only 0.04% are using services for more than an hour.

o	83.60% of total numbers of casual riders travelling in a day, are using bike service only for less than an hour and 16.40% are using services for more than an hour.

o	Trip duration, which is not more than an hour, a ratio of casual riders to annual members is approx. 1 : 3.979 however it changes as trip duration goes beyond an hour. Then, casual riders are having more share than annual members. for example- for trip duration, which is more than an hour but less than two hours, ratio changes to 21.928 : 1



More analysis was done to check data distribution from a day to months.
 Duration	Casual riders %	Annual members%	Casual riders	Annual members	All Users(Casual+Members)	All Users(Casual+Members)(%)
within a day	23.04	76.96	879289	2936866	3816155	99.95
< 15 days	71.56	28.44	1170	465	1635	0.04
>=15 days	84.78	15.22	78	14	92	0.00
>=1 month	85.06	14.94	74	13	87	0.00
>=2 month	75.86	24.14	22	7	29	0.00
>= 3 months	60.00	40.00	3	2	5	0.00
>=4 months	100.00	0.00	1	0	1	0.00
















o	Plots are depicting a downward trend for annual members as trip duration increases.

o	Plots are depicting an upward trend for casual members as trip duration increases.
Weekday:
 	Sun	Mon	Tue	Wed	Thu	Fri	Sat
Annual members	256241	458780	497025	494277	486915	456966	287163
Casual riders	170179	101489	88655	89745	101372	121141	208056



























o	Less annual members on Saturday and Sunday compared to Monday to Friday

o	More casual riders on Saturday and Sunday compared to Monday to Friday












Conclusion/ Summary:
After performing comparative analysis between annual members and casual riders, on historical data (year 2019) of Cyclistic company, using different attributes (age, gender, trip duration and days of week), it is found that trip duration and days of week are the distinguishing attributes between users. i.e. annual members and casual riders.
Below observations are made after study for:
        Days of week
-	A smaller number of annual users use services on Saturday and Sunday compared to other days of the week.
-	There are more casual riders on Saturday and Sunday compared to other days of the week.
       Trip duration
-	The percentage of users for both types are higher for short duration trips. As the duration of the trip increases, percentage goes low however if annual members and casual members are compared on the parameter of long duration trips then there are more casual riders than annual members.

Recommendations:
Currently, Cyclistic offers single-ride passes, full-day passes, and annual memberships. This could be a limitation for users who have different requirements, like students attending weekend classes and need to travel only on weekends or people with clear requirement of needing services only for shorter duration than annual. Considering all these points and after gaining insights from data, below recommendations are made:
-	As the number of casual riders increases on Saturday and Sunday, a special weekend plan for the whole year can be offered to convert casual riders to subscribers.

-	A year’s data did not reveal any trip lasting for a year, so in case of less usage, discounted prize should be offered for membership renewal which can potentially encourage casual users to buy membership. 

-	Monthly, quarterly, and bi-annual membership plans should be offered to provide flexibility to users.

----------------------------------------------------------------------------------------------------------------------------
Tools used for analysis: SQL (Google BigQuery) & Analysis
Visualization: Microsoft Excel

Download Presentation for stakeholders.
Download Analyzed data workbook


