##### Curious-Kina
# Cyclistic Case Study - Google Data Analytics

### About the Company
  Cyclistic, a successful bike-sharing company launched in 2016 offering services all across Chicago. Since then, they have expanded to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations. The bikes can be unlocked from one station and returned to any other station in the system anytime.

  Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make this possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

### Senario 
  The director of marketing at Cyclistic, believes the future success of the company depends on maximizing the number of annual memberships. Your team has been tasked with addressing the following questions (with *your* specific focus on addressing the first one):

●   **How do casual riders and annual members use Cyclistic bikes differently?**

●   Why would casual riders buy Cyclistic annual memberships?

●   How Cyclistic can use digital media to influence casual riders to become members?

### Stakeholders 
**Casual riders:** The initial focus group because the goal is to understand their behavior of using Cyclistic's bike-sharing service. Our end goal of developing insights that will influence their decision to become a member is one of the driving factors of conducting this analysis.

**Cyclistic Executive Team:** Are who we must gather quality insights for to support the approval of the change in business goals. This stakeholder has the ability to implement decisions in the company for its future success and rely on the findings in this case study to support that investment.

**Cyclistic Marketing Team:** Are the individuals who will be at the forefront of communication when executing marketing startegies that connect with casual riders. The goal of this project is to gain a clear understanding of casual and member bike-sharing customers behaviors, and provide insights that meet the casual riders needs and as a result influence their decision of committing to a membership with Cyclistic. 

# Ask 

## Things to consider:

*What is the problem the analysis is trying to solve?*

Finding the difference between casual and annual Cyclistic rider patterns.

Finding trends or patterns that influence casual riders from becoming Cyclistic members.

Increase the transition rate of casual riders becoming members.

*How can your insights drive business decisions?* 

Inform stakeholders on how to meet casual rider needs (**Better marketing to targeted audience**)

Influence increases in casual riders becoming annual Cyclistic members (**Meet goal of project**)

## Deliverable
### Business Task
  Analyze Cyclistic historical bike trip data to identify trends that contribute to the differences in annual and casual Cyclistic bike riders’ usage. Recommend insights that support a marketing strategy targeting casual riders to become annual members to increase the future success of company profits.

# Prepare 

## Things to consider:

*Does your data ROCCC?*

The data is represented as being collected by Cyclistic, a fictional bike sharing company. However, the actual data has been collected by Motivate International, Inc. with a restricted license in efforts to protect consumer data. 

*How is the data organized?*

The data is organized in comma-delimited (.CSV) format with 15 columns, including: ride ID #, ride type, start/end time, ride length (in minutes), day of the week, starting point (code, name, and latitude/longitude), ending point (code, name, and latitude/longitude), and member/casual rider.

*How are you addressing licensing, privacy, security, and accessibility?* 

A [license](https://ride.divvybikes.com/data-license-agreement) has been provided by Motivate International Inc. for useage of the public data provided.

*How did you verify the data’s integrity?*

The data’s integrity was verified by the original data source using tracked records within the bike-sharing system database.
   
### Install the Required Packages in R:

```
install.packages("tidyverse")
                ("dplyr")
                ("lubridate")
                ("readr")
                ("ggplot2")
                ("modeest")
                
``` 

```
library(tidyverse)
        (dplyr)
        (lubridate)
        (readr)
        (ggplot2)
        (modeest)
        
```

## Deliverable
### Data Source

[Motivate International Inc.](https://divvy-tripdata.s3.amazonaws.com/index.html)

# Process 

## Things to consider:

*What tools are you choosing and why?*

We will be working in R because the data is large and we will be able to clean, manipulate, and visualize the data all on the same platform.  
 
*What steps and how can you verify that your data is clean and ready to analyze?* 

I verified the data was clean and ready to analyze by using a data cleaning checklist during the cleaning process. 

## Deliverable 
### Documentation of cleaning process (as shown below)

#### Upload the Datasets in R for Cleaning and Preparation for Analysis

Begin with identifying and storing your working directory for ease in calling the data you will be working with:
 
```
    
    getwd() #displays your working directory
    setwd() #sets your working directory to call data from where you stored the datasets locally on your computer
    
 ```
    
 Now Upload your datasets:

```
    April_2021 <- read.csv("Divvy Trip April_2021.csv")
    May_2021 <- read.csv("Divvy Trip May_2021.csv")
    Jun_2021 <- read.csv("Divvy Trip Jun_2021.csv")
    Jul_2021 <- read.csv("Divvy Trip Jul_2021.csv")
    Aug_2021 <- read.csv("Divvy Trip Aug_2021.csv")
    Sep_2021 <- read.csv("Divvy Trip Sep_2021.csv")
    Oct_2021 <- read.csv("Divvy Trip Oct_2021.csv")
    Nov_2021 <- read.csv("Divvy Trip Nov_2021.csv")
    Dec_2021 <- read.csv("Divvy Trip Dec_2021.csv")
    Jan_2022 <- read.csv("Divvy Trip Jan_2022.csv")
    Feb_2022 <- read.csv("Divvy Trip Feb_2022.csv")
    Mar_2022 <- read.csv("Divvy_Trip Mar_2022.csv")
    
```

#### Wrangle and Transform your Data

Fix data type inconsistencies, start by combing through your data to understand its structure by using the following functions **colnames(), str(), head(), and glimpse()** :

```
    colnames(April_2021)
    colnames(May_2021)
    colnames(Jun_2021)
    colnames(Jul_2021)
    colnames(Aug_2021)
    colnames(Sep_2021)
    
    and so on ...

```
Rename the columns to make them consistent:

```
    (April_2021 <- rename(April_2021, trip_id = "ride_id", 
                            bike_id = "rideable_type", 
                            start_time = "started_at", 
                            end_time = "ended_at", 
                            from_station_name = "start_station_name", 
                            from_station_id = "start_station_id", 
                            to_station_name = "end_station_name", 
                            to_station_id = "end_station_id", 
                            usertype = "member_casual"))

    (May_2021 <- rename(May_2021, trip_id = "ride_id",
                            bike_id = "rideable_type", 
                            start_time = "started_at", 
                            end_time = "ended_at", 
                            from_station_name = "start_station_name", 
                            from_station_id = "start_station_id", 
                            to_station_name = "end_station_name", 
                            to_station_id = "end_station_id", 
                            usertype = "member_casual"))
                            
    (Jun_2021 <- rename(Jun_2021, trip_id = "ride_id",
                            bike_id = "rideable_type", 
                            start_time = "started_at", 
                            end_time = "ended_at", 
                            from_station_name = "start_station_name", 
                            from_station_id = "start_station_id", 
                            to_station_name = "end_station_name", 
                            to_station_id = "end_station_id", 
                            usertype = "member_casual"))
                            
                            and so on ...
                            
```
Inspect the dataframes and look for incongruencies using the **str()** function: 

#### Note: Make sure all columns match so that they will be able to stack correctly. 

```
    str(April_2021)
    str(May_2021)
    str(Jun_2021)
    str(Jul_2021)
    str(Aug_2021)
    str(Sep_2021)
    str(Oct_2021)
    str(Nov_2021)
    str(Dec_2021)
    str(Jan_2022)
    str(Feb_2022)
    str(Mar_2022)
    
```
Stack inidividual monthly dataframes into one big dataframe by binding the rows:

```
    all_trips <- bind_rows(April_2021, 
                            May_2021, 
                            Jun_2021, 
                            Jul_2021, 
                            Aug_2021, 
                            Sep_2021, 
                            Oct_2021, 
                            Nov_2021, 
                            Dec_2021, 
                            Jan_2022, 
                            Feb_2022, 
                            Mar_2022)
                            
```

Remove unneccessary columns and add columns that list the date for the day, month, and year of each ride for aggregation:

```
Removals:

    all_trips <- all_trips %>% 
    + select(-c(start_lat, start_lng, end_lat, end_lng))

Additions:

    all_trips$date <- as.Date(all_trips$start_time)
    all_trips$month <- format(as.Date(all_trips$date), "%m")
    all_trips$day <- format(as.Date(all_trips$date), "%d")
    all_trips$year <- format(as.Date(all_trips$date), "%Y")
    all_trips$day_of_week <- format(as.Date(all_trips$date), "%A")

```
Inspect the new table that has been created:

```
        colnames(all_trips)     # List of column names
        nrow(all_trips)         # To see how many rows are in data frame?
        dim(all_trips)          # Dimensions of the data frame?
        head(all_trips)         # See the first 6 rows of data frame.  Also tail(all_trips)
        str(all_trips)          # See list of columns and data types (numeric, character, etc)
        summary(all_trips)      # Statistical summary of data.

```
Add a column to calculate ride length in seconds:

```

    all_trips$ride_length <- as.numeric(difftime(all_trips$end_time,all_trips$start_time))

```

Remove all NA columns and all negative ride lengths:

```
    all_trips_no_na <- drop_na(all_trips)
    
    all_trips <- all_trips_no_na[!(all_trips_no_na$from_station_name == "HR QR" | all_trips_no_na$ride_length<0),]
    
```

# Analyze 

## Things to consider:   

*What surprises did you discover in the data?*  

Annual members ride more often than casual and single-ride customers combined.

The most popular day for casual riders using Cyclistic is on Saturdays, while the most popular day for members is on Wednesday. 

*What trends or relationships did you find in the data?*

Classic bikes are more commonly used by both casual and annual Cyclistic members.

Although, members use the bike-sharing services more often. Causual and single use riders tend to ride the bikes for longer periods of time.

*How will these insights help answer your business questions?* 

These insights help with understanding the behaviors of both usertypes' bike usage.

## Deliverable
### Summary of analysis
By combining all of the data into one dataset, I was able to run an analysis to track the busiest day of the week by usertype. This allowed me to see the difference (if any) in both casual and member usage of Cyclistic's bikes. I then proceeded with my analysis by assessing which type of user rides longer, this would give me insight into the type of behaviors riders engage in while using Cyclistic bikes. Lastly, I ran an analysis to identify which bike type is more popular for both members and casual riders. This would allow me to suggest potentially removing the other bike types from the fleet at specific stations to see if there is potentially an increase in those who choose to ride, but may not see any classic bikes availble at that time.


Let's start with a statistical summary of the cleaned data using the following functions:

``` 
    summary(all_trips)
    str(all_trips)

```

Run a Descriptive Analysis for all trips, then between casual and annual members:

```
OVERALL
    mean(all_trips$ride_length)
        [1] 1292.676
    median(all_trips$ride_length)
        [1] 703
    max(all_trips$ride_length)
        [1] 3356649
    min(all_trips$ride_length)
        [1] 0

1. INPUT (mean)

        aggregate(all_trips$ride_length ~ all_trips$usertype, FUN = mean)
        
    OUTPUT 
            all_trips$usertype      all_trips$ride_length
        1             casual              1904.550
        2             member               802.221

2. INPUT (median)

        aggregate(all_trips$ride_length ~ all_trips$usertype, FUN = median)
    
    OUTPUT
            all_trips$usertype      all_trips$ride_length
        1             casual                   946
        2             member                   562

3. INPUT (max)

        aggregate(all_trips$ride_length ~ all_trips$usertype, FUN = max)
        
    OUTPUT 
            all_trips$usertype      all_trips$ride_length
        1             casual               3356649
        2             member                 89998

4. INPUT (min)

        aggregate(all_trips$ride_length ~ all_trips$usertype, FUN = min)
        
    OUTPUT
            all_trips$usertype      all_trips$ride_length
        1             casual                     0
        2             member                     0

```
To find whether casual riders or annual members complete more rides than the other separating the number of rides by usertype:

```
1.  INPUT
            all_trips %>% 
         + group_by(usertype) %>% 
         + summarise(number_of_rides = n(), average_duration = mean(ride_length))

    OUTPUT
           # A tibble: 2 × 3
        usertype        number_of_rides     average_duration (in seconds)
         <chr>              <int>            <dbl>
        1 casual           2546482            1905.
        2 member           3176905             802.
```
To find the most used bike type for each usertype:

```
1.  INPUT
            all_trips %>% 
        + group_by(usertype, bike_id) %>% 
        + summarise(number_of_rides = n())
    
    OUTPUT
            # A tibble: 5 × 3
        # Groups:   usertype [2]
        usertype        bike_id        number_of_rides
        <chr>           <chr>              <int>
        1 casual    classic_bike          1257615
        2 casual    docked_bike            303984
        3 casual    electric_bike          984883
        4 member    classic_bike          1992992
        5 member    electric_bike         1183913
```

To find the most popular day of the week for casuals and annual members riding Cyclistic bikes:

```
1.  INPUT
        aggregate(all_trips$day_of_week ~ all_trips$usertype, FUN = mfv)# Share
    
    OUTPUT
            all_trips$usertype      all_trips$day_of_week
        1             casual              Saturday
        2             member             Wednesday

```

To find the average ride time each day for annual members vs. casual riders:

```
1.  INPUT
        aggregate(all_trips$ride_length ~ all_trips$usertype + all_trips$day_of_week, FUN = mean)
    
    OUTPUT
            all_trips$usertype      all_trips$day_of_week 
        1              casual                Friday
        2              member                Friday
        3              casual                Monday
        4              member                Monday
        5              casual              Saturday
        6              member              Saturday
        7              casual                Sunday
        8              member                Sunday
        9              casual              Thursday
        10             member              Thursday
        11             casual               Tuesday
        12             member               Tuesday
        13             casual             Wednesday
        14             member             Wednesday
                 all_trips$ride_length (in seconds)
                1              1806.1966
                2               788.3755
                3              1888.9376
                4               778.1150
                5              2056.9284
                6               899.6031
                7              2245.0173
                8               920.9511
                9              1672.9012
                10              754.2578
                11             1646.0970
                12              751.3135
                13             1665.9461
                14              755.3658

```
Analyze ridership by usertype and day of the week: 

```
1.  INPUT
        all_trips %>% 
        + mutate(day_of_week = wday(start_time, label = TRUE)) %>% 
        + group_by(usertype, day_of_week) %>% 
        + summarise(num_of_rides = n(),average_duration = mean(ride_length/60)) %>%
        + arrange(usertype, day_of_week)
        
    OUTPUT
        # A tibble: 14 × 4
        # Groups:   usertype [2]
         usertype   day_of_week     num_of_rides    average_duration (in minutes)
        <chr>       <ord>              <int>            <dbl>
        1 casual        Sun            482801             37.4
        2 casual        Mon            292993             31.5
        3 casual        Tue            276371             27.4
        4 casual        Wed            286400             27.8
        5 casual        Thu            293632             27.9
        6 casual        Fri            364277             30.1
        7 casual        Sat            550008             34.3
        8 member        Sun            387717             15.3
        9 member        Mon            439428             13.0
       10 member        Tue            490095             12.5
       11 member        Wed            499901             12.6
       12 member        Thu            475330             12.6
       13 member        Fri            453108             13.1
       14 member        Sat            431326             15.0
```
    
# Share 

## Things to Consider 

*How do your findings relate to your original question?* 

The findings show distinct differences in days used, ride length times, and the overall usage of Cyclistic bikes between casual customers and annual members. 

Number of rides by usertype: 

```

1.  INPUT
            all_trips %>% 
        +     mutate(day_of_week = wday(start_time, label = TRUE)) %>% 
        +     group_by(usertype, day_of_week) %>% 
        +     summarise(number_of_rides = n()
        +               ,average_duration = mean(ride_length)) %>% 
        +     arrange(usertype, day_of_week)  %>% 
        +     ggplot(aes(x = day_of_week, y = number_of_rides, fill = usertype)) +
        +     geom_col(position = "dodge") + 
        +     labs(title = "Table 1: Number of Rides by Day and Rider Type") + 
        +     ylab("Number of Rides (1e+05 = 100,000)") + 
        +     xlab("Day of Week")
        
    OUTPUT 
```

![Number of Rides](https://user-images.githubusercontent.com/99767816/166845719-1433462b-2663-4478-b2c3-e136f6221b43.png)



Average Duration by Day of Week:

```

1.  INPUT
            all_trips %>% 
        +     mutate(day_of_week = wday(start_time, label = TRUE)) %>% 
        +     group_by(usertype, day_of_week) %>% 
        +     summarise(number_of_rides = n()
        +     ,average_duration = mean(ride_length/60)) %>% 
        +     arrange(usertype, day_of_week)  %>% 
        +     ggplot(aes(x = day_of_week, y = average_duration, fill = usertype)) +
        +     geom_col(position = "dodge") + 
        +     labs(title = "Table 2: Average Ride Duration by Day and Rider Type") + 
        +     ylab("Average Duration (minutes)") + 
        +     xlab("Day of Week")
        
    OUTPUT
```

![Average Duration](https://user-images.githubusercontent.com/99767816/166844772-31fbb4be-031b-477c-ab96-e709f83b6eef.png)

Number of rides by month based on usertype:

```

    INPUT 
            all_trips %>% 
        +     group_by(usertype, month) %>% 
        +     summarise(number_of_rides = n()
        +     ,average_duration = mean(ride_length)) %>% 
        +     arrange(usertype, month)  %>% 
        +     ggplot(aes(x = month, y = number_of_rides, group = usertype)) +
        +     geom_line(aes(color = usertype)) + 
        +     geom_point() +
        +     labs(title = "Table 6: Number of Rides by Month and Rider Type") + 
        +     ylab("Number of Rides (1e+05 = 100,000)") + 
        +     xlab("Month")
        
    OUTPUT
```

![Number of Rides by Month](https://user-images.githubusercontent.com/99767816/166847283-e3b1f793-c8f8-42ef-8865-972e1dc99768.png)

## Deliverable
### Key Findings 

   The most popular day to ride for casual customers is on Saturdays and Sundays. 
    
   Annual members are more consistent with bike rides throughout the week, while casual customers typically increase usage of Cyclistic bikes on weekends (Saturdays and Sundays). 
    
   As observed in Table 2, Casual riders are more likely to ride 2x longer than members on any given day of the week or weekend.   
   
   The average trip duration for casual riders is 30 minutes, while for annual members it is between 13- 15 minutes. 
   
   Bike usage for casual riders and annual riders are higher during the summer months of June - August.

# Act 

## Things to consider: 

*How could your team and business apply your insights?* 

The team can apply my insights when deciding how and when to market to casual customers. 

Stakeholders can use the insights as supporting data that backs up their decision to focus on marketing to casual customers.  

*What next steps would you or your stakeholders take based on your findings?*

Next steps stakeholders or the team can take could be taking things a step further with data collection by distinguishing which casual riders purchased all day passes and single ride passes. 

#### Question to answer: 
How do casual riders and annual members use Cyclistic bikes differently?

#### Final Conclusions 

Annual members' bike activity is showing to be consistent across the week which could be indication that they use the bikes rountinely for commuting purposes. 

Casual riders show spikes in bike usage during the weekend and for increased periods of time which could be an indication that they use the bikes for leisure puposes such as sightseeing, or activities with friends. 

### Top 3 Recommendations for a New Marketing Strategy
1. Offer a third membership type custom to weekends only that allows riders access with privileges secluded to the weekend hours at a discount. 
2. The company could run a promotion during the summer on annual memberships that allow casual riders to join at a discounted price. They could also include special perks for doing so. For example, paying a lower price when signing up, or sign up with friend and get a $50 credit on future rides. 
3. Offer a 1 month trial annual membership period that allows casual riders the ability to enjoy the perks of being a member without the full commitment. During the trial you can allow them to collect points for riding or some type or rewards program, that will only continue when they sign up for an annual membership. 

### Other Considerations for Further Exploration
1. When collecting bike data, note whether casual riders purchased a single ride pass or a full day pass. 
2. The most popular bike being used is the Classic bike type, this could be an indication that those are the preffered bike types that both casual and annual users choose when selecting a bike. Could this imply that the availbility of other bike types can be reduced during the weekends? So that using the Classic bikes are easily accessible at popular stations where there may be a need for more bike inventory to meet increased weekend demands. 
