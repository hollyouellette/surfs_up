# Surfs Up 
## Module 9 Challenge

### Overview of the Analysis

In this challenge we were aspiring future owners of a Surf n' Shake shop in Oahu, Hawii. In order to get investor backing to make this aspiration a reality, weather analysis of Oahu was completed to ensure that rain would not impede this surf shop venture from acheiving success. Previous analysis was completed to showcase precipitation trends in Oahu. The analysis below was performed to gather more information about temperature trends, specifically in the months of June and December.

### Results

To complete the temperature analysis, the summary statistics for both June and December were calculated with the following output:
<p align= "center"> 
<img src="https://github.com/hollyouellette/surfs_up/blob/main/Analysis/june_temps.png" width=200 height=300>
<img src="https://github.com/hollyouellette/surfs_up/blob/main/Analysis/december_temps.png" width=200 height=300>
</p> 

Based on the summary statistics, we can identify three key differences in weather between June and December:
   
   
   
   1. On average, the temperature is 3.9&#8457; colder in the month of December than in June. 
   2. At it's lowest temperature, December is 8&#8457 colder than in the month of June.
   3. The daily temperatures in December see more deviation than temperatures in the month of June, demonstrated by December's Standard Deviation being 0.489 higher than for the temperatures in June. 

### Summary

Upon analyzing the results of this analysis, we can conclude that regardless of the time of year, Oahu see's temperatures that are warm enough to host a year-round beusiness venture that focuses on retailing surf apparel and iced cream.

In addition addition to the queries performed in this analysis, I would perform the following two queries to gather more weather data for June and December:

   1. **4 Year Lookback of June & December Weather Data**. By completing this, we would be able to determine whether the average temperatures in June & December are consistent year over year, or if there are any potentially concerning downward or upward trends. This would be completed by first quering the database for each year. The following is an example of what this query would look like for 2021:

            y_2012 = dt.date(2012, 12, 31) - dt.timedelta(days=364)

            year_2012 = session.query(Measurement.date, Measurement.tobs).\
                     filter((func.strftime("%m", Measurement.date) =="12")).\
                     filter(Measurement.date >= y_2012).all()

            year_2012_df = pd.DataFrame(year_2012)

            year_2012_df.describe()

   2. 
1. Identify the most active stations and repeat the analysis using only data from the station with the highest number of temperature observations.
         session.query(Measurement.station, func.count(Measurement.station)).\
         group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
         
2.  I would analyze the weather data from five years previous to see if the temperatures are consist or trending upward or downward (from 2012-2017):
         
         y_2012 = dt.date(2012, 12, 31) - dt.timedelta(days=364)

         year_2012 = session.query(Measurement.date, Measurement.tobs).\
                  filter((func.strftime("%m", Measurement.date) =="12")).\
                  filter(Measurement.date >= y_2012).all()

         year_2012_df = pd.DataFrame(year_2012)

         year_2012_df.describe()
