# NYC-Taxi-Trips

## Project Overview
The project details the New york City Taxi trips from 2017 to 2020, taking a llok at the most busiest week of the year, time of day, the most pick-up and drop off location and trend of trips over the year.

## Data Source
Dataset was provided courtsey of Quantum Analytics and contains 6 csv file formart of 28million trips between the year 2017 and 2020.

## Tools
Power BI - Power Query was used to clean,query, and explore the datasets
         - For visualization

## Data Cleaning/Preparation

In the initial data preparation phase, we performed the follwing tasks:
- Datasets loading ad inspections
- Datasets cleaning , filtering and conditional formatting
- Used the dataset calender to checkfor the meaning of the columns head and carried out the required formatting.
- Datasets mergeing to make 1 dataset.

## Exploratory Data Analysis

1. What's the average number of trips we can expect this week?
2. What's the average fare per trip?
3. What's the average distance traveled per trip?
4. How do we expect trip volume to change, relative to last week?
5. Which days of the week and times of the day will be busiest?
6. What will likely be the most popular pick-up and drop-off locations?
7. Weekly Trip trend for the Year.

## Data Analysis
Few Power Query carried out in Power BI.

For any trips that have a fare amount but have a trip distance of 0, calculate the distance this way: (Fare amount - 2.5) / 2.5:
```Table.ReplaceValue(#"Changed Type1",each [trip_distance],each if [trip_distance]=0 and [fare_amount]>0 then (([fare_amount]-2.5)/2.5) else  [trip_distance],Replacer.ReplaceValue,{"trip_distance"})```

For any trips that have a trip distance but have a fare amount of 0, calculate the fare amount this way: 2.5 + (trip distance x 2.5):
```Table.ReplaceValue(#"Replaced Value3",each[fare_amount],each if [fare_amount]=0 and [trip_distance]>0 then (2.5+([trip_distance]*2.5)) else[fare_amount],Replacer.ReplaceValue,{"fare_amount"})```

 Added a column to sort trips that have 'fare amount' and 'surcharges' as zero and name the negetive to futher carry out nalysis on the rows:
 ```Table.AddColumn(#"Replaced Value4", "Custom", each if [fare_amount]<0 and [extra]<0 and [mta_tax]<0 and [improvement_surcharge]<0 and [congestion_surcharge]<0 then "neg" else "ok")```

Turning negetive 'fare amount' to positive:

 ```Table.ReplaceValue(#"Added Custom3",each [fare_amount],each if [Custom]="neg" then [fare_amount]*-1 else [fare_amount],Replacer.ReplaceValue,{"fare_amount"})```

Turning negetive 'extra' to positive:
```Table.ReplaceValue(#"Replaced Value5",each [extra],each if [Custom]="neg" then [extra]*-1 else [extra],Replacer.ReplaceValue,{"extra"})```

Turning negetive 'mta tax' to positive:
 ```Table.ReplaceValue(#"Replaced Value6",each[mta_tax],each if [Custom]="neg" then [mta_tax]*-1 else [mta_tax],Replacer.ReplaceValue,{"mta_tax"})```

Turning negetive 'improvement surcharge' to positive:
```Table.ReplaceValue(#"Changed Type2",each [improvement_surcharge],each if [Custom]="neg" then [improvement_surcharge]*-1 else [improvement_surcharge],Replacer.ReplaceValue,{"improvement_surcharge"})```

Turning negetive 'congestion surcharge' to positive:
```Table.ReplaceValue(#"Changed Type3",each [congestion_surcharge],each if [Custom]="neg" then [congestion_surcharge]*-1 else [congestion_surcharge],Replacer.ReplaceValue,{"congestion_surcharge"})```


## Result / Findings 
- We had a total of 26 million trips between the span of 4 year (2017 - 2020).
- The average fare per trip was $ 12.31 for the entire 4 Year span.
- Mornings and Night were the buiest time of the day, its not surprising as the city never sleeps and done of the busiest in the world.
- 74 Manhattan, 75Manhattan, 41Manhattan and 7 Queens are the most pick-up and drop off location for passengers.
- The first few weeks of each year are usually the most buiest weeks of the year, reason been that passengers are trying to get back to work and most travellers are leaving for their various destination.

## Recommendations
Trip analysis like this should be carried out occasionally, as 
- it helps to understand the  strategies that can be better put in place in case of busy days.
- it would futher help drivers to be prepared for busy and less busy moments.
- it would help the commision to know how to allot budgets in case of road repairs and  new drivers who are just starting.
- With understanding of the buiest time of day, drivers can futher plan their day, to take rest at appropriate time or engage in other jobs or tasks to increase their wages.
      
      
























  
