# City-Bike-Analysis-2018-Tableau
Creation of dashboards in Tableau summarizing key findings of Citi Bike utilization in Jersey City, NJ for 2018

## Tableau Public Links

 https://public.tableau.com/profile/jason.klug#!/vizhome/CityBike2018Analysis/AnalysisbyGender

 https://public.tableau.com/profile/jason.klug#!/vizhome/CityBike2018Analysis_OverviewDashboard/AnalysisOverallSummary?publish=yes


## Dashboard Screen Shots


![overall_dashboard](https://user-images.githubusercontent.com/48166327/64482004-e004ea80-d19d-11e9-95fe-a4c92dcbb1e5.PNG)



![gender_map_dashboard](https://user-images.githubusercontent.com/48166327/64482006-e2674480-d19d-11e9-84f1-177eafb3d2b3.PNG)



![repair_dashboard](https://user-images.githubusercontent.com/48166327/64482008-e4310800-d19d-11e9-9862-a0750a424e11.PNG)



## Cleaning the data

  - All csv files were downloaded from https://www.citibikenyc.com/system-data
  - Bike trip history data was used.
  - Monthly csv files were concatenated for 2018 in jupyter notebook 
  - Headers were renamed, data types were checked, missing values and data ranges were inspected.
  - To remove failed rides, damaged bikes or errors in bike checkout all rides that originated and finished at the same station in less than 90 seconds were removed. This removed 413 records from the 353,891 records for 2018
  - After plotting trip duration (sec) i noticed that there were 1434 rides longer than 2hr, 664 longer than 4hrs, and 419 longer than 8hrs.  
>The Citi Bike website states that subscribers get 45-minute unlimited rides and then are charged $2.50 every 15 minutes.  So i thought that people would not want to ride a clunky Citi bike for longer than 2 hours and then expanded that time to 4 hours to not eliminate any actual data of people who did not mind paying that rate or did not understand the payment structure. 
  - I decided that any rides longer than 4 hours were stolen bikes or docking errors and removed 664 rows. 
  - I added an "Age" column to the data frame using the birthyear
> At looking at the range of birth years I realized that people were either lying about their age or making mistakes inputting there birth year. There were births years from 1887 making the person 131 years old!  I decided that anyone over 70 years old was probably not being honest with their age (to all those 70+ year old city bike riders my apologies!).  
  - Those older than 70 years old in the dataset (130 records) were removed.
  - The final cleaned dataset contained 352815 records out of an initial 353,891 records (loss of 0.3%).
  - This final data frame was exported to csv and imported into tableau

### Column Headers
 
- Trip Duration (seconds)
- Start Time and Date
- Stop Time and Date
- Start Station Name
- End Station Name
- Station ID
- Station Lat/Long
- Bike ID
- User Type (Customer = 24-hour pass or 3-day pass user; Subscriber = Annual Member)
- Gender (Zero=unknown; 1=male; 2=female)
- Year of Birth

## Findings

By Month:
  - Subscribers make up about 94% of the rides or Citi Bike
  - Ridership for subscribers peaks in August and customers peaks in July. Making sense with the nice summer weather
  - For the year there were 386,578 subscribers and 25,664 customers for 2018
  - The month with the greatest rate of growth was March

By Week:
  - Subscribers had the most bike rides during the week (Tuesday Peak)
  - Customers had more rides on the weekend.  This group may represent tourists
    
By Hour:
  - Subscribers had peak riding hours around 8AM and 6PM.  Traditional times to start and leave work. There was a small increase in ridership from 12 to 1PM (lunch?). Interestingly, there are fewer 5PM rides than 8AM rides suggesting a population of people work late or take another means of transportation home. This group probably represents a majority of commuters for work 
  - Customers rides peaked around 5-6PM
  - These dynamics were similar in the summer and winter with lower absolute numbers in the winter 
    
By age:
  - The most frequent age for subscribers is 30 years old
  - The most frequent age for subscribers is 28 years old
  - Range of 16 to 70 years old
  - Teenagers take the longest rides
  - Customers take longer rides than subscribers on average across all ages
    
By Distance/duration:
  - The most frequent distance was 0.51 miles (duration (sec convert to hr) * 7.456 mi/hr rate)
  - The most frequent trip duration was 244 seconds or around 4 minutes
    
By Gender:
  - Males make up around 73% of the riders while females make up around 21%.  The remaining 6% are unknown/not identified
  - Ridership peaks in August for men and women and shows a similar increase and decrease over months
  - Men and women ride the most during the week with a peak on Tuesday. Men's rides have a greater reduction over the weekend compared to women
  - Unknown riders rode more on the weekend
    
By Starting Station:
  - The starting station with the most rides is Grove St. PATH.  It is centrally located in Jersey City
  - The starting station with the longest distance rides is Newport Parkway. This station is right near the Holland Tunnel were bikes are allowed on trains 
  - Columbia Park is the most under-utilized starting station
    
By Ending Station:
  - Grove St. PATH is the most popular ending location for a trip. It is centrally located and has a lot of other transportation options(trains, etc.)
  - Newport Parkway is the longest trip distance ending point 
  - Many ending stations are located throughout Manhattan and Brooklyn
    
By Bike:
  - Bike ID #29491 had the greatest number of trips
  - 9 bikes only had a single ride
  - Bike ID #34155 had the longest average rides (4.4 miles) 
  - The bikes with the most variable ride distances had shorter cumulative total distances rode over the year
    
By location:
  - A majority of the rides originated in downtown Jersey City near Grove Street PATH. While frequent these trips were shorter than rides that started further out
  - Most rides ended in downtown Jersey City near where they originated.  Yet an appreciable amount ended throughout Manhattan and Brooklyn. Some rides were over 20 miles
  - More rides began and ended in zip codes with higher per capita incomes