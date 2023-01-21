# surfs_up

>While on vacation in Hawaii last year, you discovered a newfound passion for surfing. You've been trying to create a plan that will let you not just return to Hawaii, but live there forever. You finally come up with an idea that you think is foolproof, a Surf and Shake shop serving surfboards and ice cream to locals, tourists, and of course, yourself.
>You have some savings you're willing to invest, but we'll need some real investor backing to get this off the ground. So after putting together a strong business plan, you reach out to an investor, W. Avy, who is famous for his love of surfing. Your first meeting with him goes extremely well, but he has one concern, what about the weather?

>He's extremely serious about this. He invested in a surf shop early in his career. However, he didn't ask for any weather analysis and that early venture was rained out of existence. W. Avy knows you've been learning how to properly analyze data and asks if you can run some analytics on a weather data set he has from the very island where you'd like to open your shop, the beautiful Awahoo.

Language:Python

Database:SQLite

Libraries:Pandas,SQLAlchemy

IDE: Jupyter Notebook

_________________________________________________________________________________


## 1) Overview of the analysis: 
### Explain the purpose of this analysis.

You come up with the idea to open a surf shop that also sells ice cream, and you need an investor to help get this project off the ground.  The requirement from the investor was to perform a weather analysis on a weather dataset for the possible future location of a surf shop that also sells ice cream.
The investor had previously backed a surf shop, but didn't ask for this requirement for the funding. Using the weather data set will allow us to find average temperatures and precipitation for any month in the dataset.

## 2)Results: 
### Provide a bulleted list with three major points from the two analysis deliverables. Use images as support where needed.

1. The average temperature is rather similar when you compare June to December.  This is good news for our investor;because, based on historical data, there should not be a significant drop in sales in the winter months based purely on temperature.
2. The minimum temperature in December is in the 50s compared to the 60s in June.  This could be a concern to our investor as customers may be less likely to want to surf and purchase ice cream in cooler weather. 
3. The standard deviations are similar as well.  There is more variability in the temperature in December than June.  This would make sense as the earth's orbit around the sun affects temperatures.

Figure 1: 

![June](/Images/June_temp.png)

Figure 2: 

![December](/Images/Dec_temp.png)

## 3)Summary: 
### Provide a high-level summary of the results and two additional queries that you would perform to gather more weather data for June and December.

Based on the temperature analysis, the results look favorable for opening a surf shop that serves ice cream.  Figure 1 and Figure 2 show that the temperatures on Awahoo are similar in the winter and summer.  That is good news as if there is not a significant difference between the two "extreme" seasons that the intermediate seasons should in theory have similar temperatures as well. 

Additional Queries:

1. The weather database also has precipataion data as well. It would be good to run that anlaysis as well.  The temperature could be good, but rain could ruin the chances of any sales that day.

    results_3=session.query(Measurement.prcp ).\
    filter(func.strftime("%m", Measurement.date) == "6").all()
    
    results_4=session.query(Measurement.prcp ).\
    filter(func.strftime("%m", Measurement.date) == "12").all()

2. In the same vain, it could also be useful to filter the data by the closest weather station(s) to the future location of the shop to understand temperature and precipataion as well.

    results_5=session.query(Measurement.tobs,Measurement.station).\
    filter(Measurement.station == 'local station(s)').\
    filter(func.strftime("%m", Measurement.date) == "6").all()
    
    results_6=session.query(Measurement.tobs,Measurement.station).\
    filter(Measurement.station == 'local station(s)').\
    filter(func.strftime("%m", Measurement.date) == "12").all()


