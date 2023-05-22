# cyclistic-bike-share-analysis
###### Analysis of how annual members and casual riders use Cyclistic bikes differently

#### Introduction & Objective:
This case study was performed as capstone project for the <b>“Google Data Analytics Professional Certificate”</b> course. <br>

**Cyclistic**, a bike-share company in Chicago is a fictional company. This analysis is done to know how do annual members and casual riders use Cyclistic bikes differently?

The company has 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. They offer many flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.


 They want to Design marketing strategies aimed at converting casual riders into annual members. To do that, they need to better understand how annual members and casual riders differ.
 
 
 **Our objective is to analyze the Cyclistic historical bike trip data to identify trends and usage behavior of annual members and casual riders.**

#### About Data:
We are going to use the company’s historical data i.e. year 2019 to analyze and identify trends, if exists.


The data has been made available by Motivate International Inc. under this license.) This is public data.

Data is stored as comma separated files. This <a href='https://divvy-tripdata.s3.amazonaws.com/index.html'>link</a> can be used to download the files. Files used for this study are:

 - Divvy_Trips_2019_Q1.zip <br>
 - Divvy_Trips_2019_Q2.zip<br>
 - Divvy_Trips_2019_Q3.zip <br>
 - Divvy_Trips_2019_Q4.zip 

#### Data preparation and cleaning:
As data is stored in four files and contain large data, files were <b>imported to Google Bigquery</b> and merged all data to one table. After merging, the available number of records is 3818004.


Following observations were made about data:<br>
-	Trip_id is unique for each record.<br>
-	Birthyear and gender contain null values.<br>
-	End time is smaller than start time for some records.<br>
-	Different station names are being used for one station code.<br>

Actions taken for inconsistency/ambiguity:<br>
-	Unique station name is provided for unique station id.<br>
-	Start_time is updated with end_time and end_time is updated with start_time, wherever it was inconsistent. <br>
-  	null values are not treated for birthyear and gender as no impact was observed due to its presence.<br>
-	trip duration was calculated by subtracting start time from end time.
	
#### Analyzing data:
usertype column contains <b>two unique values: Customer and Subscriber.</b> Subscriber is our annual member and Customer is a casual rider.


![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/4cc3c01f-37eb-4e5b-a134-23ae92051b32)


We are going to **perform our analysis using the attributes below** to check how annual members are different than casual riders.

<b>Age:</b> Is there dominant age group who either prefers to be member or casual rider?

<b>Gender:</b> is there specific gender who is opting for annual membership than being casual rider or vice versa?

<b>Trip Duration:</b> is trip duration the deciding factor for either being member or casual rider?

<b>Weekday:</b> is the day of week of journey differentiating the users?

##### Age
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/39c973f9-04a7-44ff-939c-51ea976f3640)

![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/adf6df7f-fedb-44e4-90bb-984632cf02ad)

The above chart does not show any trend or pattern which indicates preference towards membership or being casual rider due to age.
###### ** there was no clarification available about missing/null values, hence it is not being considered while plotting the graph.

##### Gender:
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/dbf0f2b9-07de-472b-a517-5cfce5e94b4a)

![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/19ed5250-16ce-4f59-b186-e276fe14dbac)

The above chart does not show any trend or pattern which indicates preference towards membership or being casual rider due to gender.
###### there was no clarification available about missing/null values, hence it is not being considered while plotting the graph.

##### Trip Duration:
•	Data contains trip durations ranging from 61 second to 123 days.      <br> 
•	99.95% trip ends in a day.<br>
•	0.05% of trips are between 2 to 123 days.

![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/1de7ba51-a1fb-4404-8b76-72d47e341a7e)

![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/83c035b4-bb47-4863-810e-2aae4b910fc1)


Further we analyzed data for trip durations which end within a day – for both the user types.
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/8070a00d-9ea4-4150-9759-c9e4a624798e)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/9cbda0d9-cb80-49ac-903e-bfc71acb466d)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/745f9fb1-88c3-49cd-9e4d-ca7f36e4cddd)

- 99.60% of the total numbers of annual members travelling in a day, are using bike service only for less than an hour and only 0.04% are using services for more than an hour. <br>
- 83.60% of total numbers of casual riders travelling in a day, are using bike service only for less than an hour and 16.40% are using services for more than an hour.<br>
- Trip duration, which is not more than an hour, a ratio of casual riders to annual members is approx. 1 : 3.979 however it changes as trip duration goes beyond an hour. Then, casual riders are having more share than annual members. for example- for trip duration, which is more than an hour but less than two hours, ratio changes to 21.928 : 1 <br>

More analysis was done to check data distribution from a day to months.
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/1e1026f2-9b96-4cd7-869a-63df5d145c90)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/1d235df1-21b2-4559-8b4f-d68c98516c9a)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/6cf74775-6e63-4128-b2bf-2c2337caac20)

- Plots are depicting a downward trend for annual members as trip duration increases.<br>
- Plots are depicting an upward trend for casual members as trip duration increases.

##### Weekday:
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/21057ae0-e62d-41dd-91ad-031421510042)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/d2357b74-df21-4b3d-8be3-0f92d7bbe69d)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/d5107d69-8936-412f-ad3f-07e1a04aa095)
![image](https://github.com/anju-pandey/cyclistic-bike-share-analysis/assets/124940549/876cd51e-59c3-4e0e-b195-b92800cdba8a)

- Less annual members on Saturday and Sunday compared to Monday to Friday <br>
- More casual riders on Saturday and Sunday compared to Monday to Friday

##### Conclusion/ Summary:
After performing comparative analysis between annual members and casual riders, on historical data (year 2019) of Cyclistic company, using different attributes (age, gender, trip duration and days of week), it is found that trip duration and days of week are the distinguishing attributes between users. i.e. annual members and casual riders. <br>
Below observations are made after study for: <br>
<b>Days of week</b><br>
- A smaller number of annual users use services on Saturday and Sunday compared to other days of the week.<br>
- There are more casual riders on Saturday and Sunday compared to other days of the week.<br>
<b>Trip duration</b><br>     
- The percentage of users for both types are higher for short duration trips. As the duration of the trip increases, percentage goes low however if annual members and casual members are compared on the parameter of long duration trips then there are more casual riders than annual members.

##### Recommendations:
Currently, Cyclistic offers single-ride passes, full-day passes, and annual memberships. This could be a limitation for users who have different requirements, like students attending weekend classes and need to travel only on weekends or people with clear requirement of needing services only for shorter duration than annual. Considering all these points and after gaining insights from data, below recommendations are made:

- As the number of casual riders increases on Saturday and Sunday, a special weekend plan for the whole year can be offered to convert casual riders to subscribers.

- A year’s data did not reveal any trip lasting for a year, so in case of less usage, discounted prize should be offered for membership renewal which can potentially encourage casual users to buy membership. 

- Monthly, quarterly, and bi-annual membership plans should be offered to provide flexibility to users.

----------------------------------------------------------------------------------------------------------------------------
<b>Tools used for analysis:</b> SQL (Google BigQuery) & Analysis

<b>Visualization:</b> Microsoft Excel

<a href='https://docs.google.com/presentation/d/e/2PACX-1vT3N9cvcGDGbgJR5Rqj-4tpSH6CAPbQicG04VS6Ye_0nEAWVL3R_UQ6U2A6iwOwGuKdgO8ICB_dMhz9/pub?start=false&loop=false&delayms=3000'>Download Presentation for stakeholders.</a>


<a href='https://docs.google.com/spreadsheets/d/1hby5QSqIwQYGuWiOMZdF2u1OJ-TbuKk2/edit?usp=sharing&ouid=116714514526983481166&rtpof=true&sd=true'>Download Analyzed data workbook</a>


