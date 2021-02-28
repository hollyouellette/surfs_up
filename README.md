# Surfs Up 
## Module 9 Challenge

### Overview of the Analysis

In this challenge we were aspiring future owners of a Surf n' Shake shop in Oahu, Hawaii. In order to get investor backing to make this aspiration a reality, weather analysis of Oahu was completed to ensure that rain would not impede this surf shop venture from achieving success. Previous analysis was completed to showcase precipitation trends in Oahu. The analysis below was performed to gather more information about temperature trends, specifically in the months of June and December.

### Results

To complete the temperature analysis, the summary statistics for both June and December were calculated with the following output:
<p align= "center"> 
<img src="https://github.com/hollyouellette/surfs_up/blob/main/Analysis/june_temps.png" width=200 height=300>
<img src="https://github.com/hollyouellette/surfs_up/blob/main/Analysis/december_temps.png" width=200 height=300>
</p> 

Based on the summary statistics, we can identify three key differences in weather between June and December:
   
   
   
   1. On average, the temperature is 3.9&#8457; colder in the month of December than in June. 
   2. At its lowest temperature, December is 8&#8457 colder than in the month of June.
   3. The daily temperatures in December see more deviation than temperatures in the month of June, demonstrated by December's Standard Deviation being 0.489 higher than for the temperatures in June. 

### Summary

Upon analyzing the results of this analysis, we can conclude that regardless of the time of year, Oahu see's temperatures that are warm enough to host a year-round business venture that focuses on retailing surf apparel and iced cream.

In addition to the queries performed in this analysis, I would perform the following two queries to gather more weather data for June and December:

   1. **5 Year Lookback of June & December Weather Data**. By completing this, we would be able to visually identify summary statistic trends in temperatures for June & December year over year. This would also showcase any potentially concerning downward or upward trends in Oahu's temperature. We would be complete this by adding a filter to the query used in the prior analysis to isolate the summary statistics by year. The following is an example of what this query would look like for December 2012:

            y_2012 = dt.date(2012, 12, 31) - dt.timedelta(days=364)

            year_2012 = session.query(Measurement.date, Measurement.tobs).\
                     filter((func.strftime("%m", Measurement.date) =="12")).\
                     filter(Measurement.date >= y_2012).all()

            year_2012_df = pd.DataFrame(year_2012)

            year_2012_df.describe()

   2. **Average Temperature 5 year Trend Analysis**. In order to assemble the data from the previous query into a format that the investors would find helpful in their decision making, I would re-factor the code above to isolate the average temperature for each year. From there, I would assemble the annual average temperatures in a DataFrame so that investigators can visually see ths 5-year trend in the average temperature for each month (December example below).

<p align="center"><img src="https://github.com/hollyouellette/surfs_up/blob/main/Analysis/december_lookback.png" width=700></p>
   
