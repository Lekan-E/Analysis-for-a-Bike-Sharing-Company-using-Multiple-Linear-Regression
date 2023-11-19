# Comparative-Analysis-Project
 A customer analysis dashboard for a bike-sharing company to better understand how members and casual riders uses the bike and differ.

 # Overview
This is a case-study for a bike-sharing company with a fleet of 5,824 bicycles including (Electric, Classic and Docked Bikes) which are located in a network of 692 stations across Chicago. Bicycles can begin at a station and be returned to any station.
The company provides bicycles to annual members and casual riders which come as single-ride passes and full-day passes.

# Businesss Task
The director of marketing has tasked me to come up with startegies aimed at converting exisiting casual riders to annual members. To do that the marketing team needs to better understand riders differ.
For us to achieve this, we need to study both customer's needs, behaviours and understand the pattern. This involves studying:
    - Bicycle Preference
    - Day of the Week Preference
    - Start and End Station
    - What season of the year riders prefer

# Dataset/Data Background
The dataset was provided in the Google Data Analytics Capstone Project.
It includes a month-month dataset for a year, running from Nov. 2020 - Nov. 2021 in .csv format.
Each sheet includes ride information for each month, providing:
    - A unique ride id - ride_id
    - Bike Type - rideable_type
    - Start Date and Time - started_at
    - End Date and Time - ended_at
    - Start Station - start_station_name
    - start_station_id
    - End Station - end_station_name
    - end_Station_id
    - Start Station Latitude - start_lat
    - Start Station Longitude - start_lng
    - End Station Latitude - end_lat
    - End Station Longitude - end_lng
    - Member Type - member_casual

**** insert diagram

# Data Preparation
My first step of data preparation was to extract more data from the raw dataset to help our analysis. For this I utilised Microsoft Excel Power Query importing all 13 months data set. 

From the start date and time, we can get information on the month and year (month_year), day of the week (day_of_week) where the ride started. And with the ended_at, we can get the ride duration (ride_length) = [ended_at - started_at].

After performing this process on all 13 months dataset, I import the data into MySQL Workbench for further data preparation by creating the table sturcture and loading the .csv files using the below process. 

![Alt text](https://github.com/Lekan-E/Comparative-Analysis-Project/blob/main/Images/Misc/import%20tables.jpg)

**Figure 1: Loading Tables into SQL Workbench**

After loading all tables into SQL, I create a SQL View 'v_all_months' to combine all 13 tables into a single sheet. (A SQL View is a virtual table whose contents are obtained from an existing table called a base table.)

From this view, we can further breakdown the table into smaller tables. Working with smaller tables helps us with running queries and for data cleaning.

![Alt text](https://github.com/Lekan-E/Comparative-Analysis-Project/blob/main/Images/Misc/schema.jpg)
**Figure 2: Table Schema**


# Data Cleaning
The last and most important step before analysis is data cleaning.
Our data cleaning for this project involved:
    - Updating Missing Station Info: This process involved updating station names by finding the information from their unique ids and also using the longitude and latitude position. Using latitude and longitude we updated numerics to 3 decimal places, from there we can easily find and update the missing station names, which will be important in our analysis later on.
    - Deleting Trips with a Duration of 0 or less than 0 seconds: Ride length can only be postive for the trip to have occured. So any trip with a duration less than or equal 0 seconds is deleted from the dataset.
    
At the end of cleaning, we 5,738,312 rides ready for analysis.

which is heavly influenced by the factors which will be analysis in this project
A customer comparative analysis project to help a cycling company 
understand how and suggest a marketing strategy to convert casual riders to annual members.

and over 5 million yeary rides.