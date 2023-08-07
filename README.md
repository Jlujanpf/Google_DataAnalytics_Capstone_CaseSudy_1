# Google Data Analytics Capstone CaseSudy


## 🔗 Link
- [**Tableau Dashboard**] - created a dashboard in Tableau summarizing the data.

## 📁 Files
- [**FinalAnalysis.R**]) - analyzed the data set from case study 1 in the Google Data Analytics Course using R. I did not do any data visualization in R. 
- [**FinalAnalysisTableau.R**] - create a specific data frame to use in Tableau. Deleted unncessary columns to make the code run quicker in Tableau.


I analyzed a dataset using R for a company, Cyclistic, a bike sharing company in Chicago. Created an interactive dashboard showing how annual members and casual riders use Cyclistic bikes differently. I also provided marketing strategies to convert casual riders to annual members. 

## 🚲 Background
Cyclistic is a fictional bike sharing program which features more than 5,800 bikes and 600 docking stations. It offers reclining bikes, hand tricycles, and cargo bikes, making it more inclusive to people with disabilities and riders who can't use a standard two-wheeled bike. It was founded in 2016 and has grown tremendously into a fleet of bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. 



## PROCESS:
Overview: I first analyzed the data separately (each month) in Excel, then used R to analyze the data as a whole (one year). Finally I created a dashboard in Tableau and used Figma to support the design elements. 


## Microsoft Excel
I initially wanted to gather and analyze my data in Excel because it was the tool I was most familiar with and I could get a general understanding of the data quicker. I did not combine all of the spreadsheets into one because that would've taken more processing power than my computer had. 

I began downloading the data from divvy-tripdata, and turning the .csv files into excel spreadsheets. I downloaded the most recent year of data which was at the time of starting my project: 

August 2020

September 2020

October 2020

November 2020

December 2020

January 2021

February 2021

March 2021

April 2021

May 2021

June 2021

July 2021

Added two columns to all of the months:

ride_length calculated the total ride length for each trip using the start_at column which was: ending time minus starting time. 

day_of_week calculated the day of the week for each trip using the start_at column date. 

Went over the business task and the information I had at hand and how that could be used to figure out how members and casual riders use the bike service differently

Came up with metrics to look at such as : 

total number of rides per hour, per day of the month, per season, per day of the week, and for different bike types 

Average ride length between members and casual

For every month in Excel created pivot tables and charts to go with the analysis on (this took the longest):

Total Rides per Weekday - calculated the total rides for members and casual and separated it by day of the week; used a cluster column chart

Average Ride Length - calculated the average ride length for members and casual and separated it by day of the week; used a cluster column chart

Total Rides per Hour -  calculated the total rides for members and casual separated by the time of the day (24hr); used a line comparison chart 

Total Rides per Day -  calculated the total rides for members and casual separated by the day of the month; used a line comparison chart 

Total Rides per Bike Type - calculated the total rides for members and casual separated by Bike type; used stacked column chart 

I also created a Google docs Notes list where I wrote down the exact steps for each month (had a checklist) and included my insights for each month



## R 
I originally wanted to use SQL but the files were too big to upload and I couldn't figure out how to utilize Google Cloud Platform. Instead I used R to analyze the data because it could handle all of the information quicker than Excel, and I wanted to work on my R skills. Below is my general process in R, I didn't include my mistakes/missteps or errors for the sake of brevity.



Load all of the libraries I used: tidyverse, lubridate, hms, data.table 

Uploaded all of the original data from the data source divytrip into R using read_csv function to upload all individual csv files and save them in separate data frames. For august 2020 data I saved it into aug08_df, september 2020 to sep09_df and so on. 

Merged the 12 months of data together using rbind to create a one year view

Created a new data frame called cyclistic_date that would contain all of my new columns 

Created new columns for:

Ride Length - did this by subtracting end_at time from start_at time

Day of the Week 

Month 

Day 

Year

Time - convert the time to HH:MM:SS format

Hour 

Season - Spring, Summer, Winter or Fall

Time of Day - Night, Morning, Afternoon or Evening

Cleaned the data by:

Removing duplicate rows

Remove rows with NA values (blank rows)

Remove where ride_length is 0 or negative (ride_length should be a positive number)

Remove unnecessary columns: ride_id, start_station_id, end_station_id, start_lat, start_long, end_lat, end_lng

Calculated Total Rides for:

Total number of rides which was just the row count = 4,152,139

Member type - casual riders vs. annual members 

Type of Bike - classic vs docked vs electric; separated by member type and total rides for each bike type

Hour - separated by member type and total rides for each hour in a day

Time of Day - separated by member type and total rides for each time of day (morning, afternoon, evening, night)

Day of the Week - separated by member type and total rides for each day of the week

Day of the Month - separated by member type and total rides for each day of the month

Month - separated by member type and total rides for each month

Season - separated by member type and total rides for each season (spring,  summer, fall, winter)

Calculated Average Ride Length for:

Total average ride length

Member type - casual riders vs. annual members 

Type of Bike - separated by member type and average ride length for each bike type

Hour - separated by member type and average ride length for each hour in a day

Time of Day - separated by member type and average ride length for each time of day (morning, afternoon, evening, night)

Day of the Week - separated by member type and average ride length for each day of the week

Day of the Month - separated by member type and average ride length for each day of the month

Month - separated by member type and average ride length for each month

Season - separated by member type and average ride lengths for each season (spring,  summer, fall, winter)

Then using all of this data I created my own summary in my case notes and took note of the: total rides for each variable, average ride lengths for each variable, and the difference between members versus casual riders. I originally wanted to create a report using R Markdown as well but for the sake of time (I had already spent over 20 hours on the project so far), I decided to skip this step, and write this article instead. 

## Tableau 
While I learned the basics of Tableau in the Google Course I wanted more practice with visualizing data and creating dashboards.



I created a separate R code (you can view it here on Github) that made some changes for specifically the Tableau portion.

For ride length I rounded the digits by 1, meaning my numbers were 29.8 or 12.5.

Revised how I created my "month" column. I used mutate() to create a column that had the month in ___ format and not number format. So instead of 01 it would say "January"

Cleaned the data: removed rows with NA values, removed duplicate rows, removed where ride_length was 0 or negative and removed unnecessary columns like:  ride_id, start_station_id, end_station_id, start_lat, start_long, end_lat, end_lng

Created a new dataframe with this information so I could test the difference between the original data frame (cyclistic_date) that I used for my analysis and the data frame I would use for Tableau (cyclistic_tableau). 

In this new data frame I removed more columns to make calculations quicker in Tableau. I removed: start_station_name, end_station_name, time, started_at, ended_at

Downloaded this data frame into a .csv file which I uploaded to Tableau

Created graphs similar to those I created in Excel but added a few:

User Type 

Total Rides by Bike Type

Ride Length by Weekday

Total Rides by Weekday

Total Rides by Hour

Total Rides by Month

Then I created a basic dashboard with all of that information, a prototype for me to view while I was creating the final dashboard (Figure 1 below). 

Created a prototype mockup in Figma

Created a final version of the mockup in Figma

Edited Dashboard in Tableau to reflect design in Figma

Edited graphs in Tableau 

Made bar graphs round

Added annotations

Highlights to specific important notes 

Got rid of labels for visual purposes

Combined Figma and Tableau (used dashboard created in Figma as the background for my Tableau Dashboard) to create a final prototype 

Made minor edits to design elements and created final dashboard 
Adding horizontal grid lines to a few of the charts

Updating the tool tips.

Making all of the top metric values (e.g. Total Rides, Average Ride Length, etc.) interactive in Tableau instead of in Figma.





