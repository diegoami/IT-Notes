# IMPORTING DATA

## Messy data

```
The following stock data was collect on 2016-AUG-25 from an unknown source
These kind of comments are not very useful, are they?
Probably should just throw this line away too, but not the next since those are column labels
name Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
# So that line you just read has all the column headers labels
IBM 156.08 160.01 159.81 165.22 172.25 167.15 164.75 152.77 145.36 146.11 137.21 137.96
```


To import this

```
df2 = pd.read_csv(file_messy, delimiter=' ', header=3, comment='#')
```

## Reading dates

```
Dates,Temperatures
2016-07-01,0
```



## Converting to datetime

```
date_list = \
['20101211 04:00',
 '20101211 05:00',
 '20101211 06:00'
]

temperature_list = \
[45.799999999999997,
 45.5,
 45.799999999999997,
]

```


```
time_format = '%Y-%m-%d %H:%M'
my_datetimes = pd.to_datetime(date_list, format=time_format)
time_series = pd.Series(temperature_list, index=my_datetimes)
```

results into

```
2010-12-11 04:00:00    45.8
2010-12-11 05:00:00    45.5
2010-12-11 06:00:00    45.8
```

## Indexing by datetime

```
ts1 = ts0.loc['2010-10-11 21:00:00']
ts3 = ts0.loc['12/15/2010':'12/31/2010']
```


## Reindexing by datetime

Having two datasets

```
ts1
2016-07-01,0
2016-07-02,1
2016-07-03,2
2016-07-04,3

ts2
Dates,Temperatures
2016-07-01,0
2016-07-04,1
```


you can reindex ts2, possibly ffilling the missing value

```
ts3 = ts2.reindex(ts1.index)

            Temperatures
Dates
2016-07-01           0.0
2016-07-02           NaN
2016-07-03           NaN
2016-07-04           1.0
```

# AIRPORT Data

```
Date (MM/DD/YYYY),Carrier Code,Flight Number,Tail Number,Destination Airport,Scheduled Departure Time,Actual Departure Time,Scheduled Elapsed Time(Minutes),Actual Elapsed Time(Minutes),Departure Delay(Minutes),Wheels-off Time,Taxi-out Time(Minutes),DelayCarrier(Minutes),DelayWeather(Minutes),DelayNational Aviation System(Minutes),DelaySecurity(Minutes),DelayLate Aircraft Arrival(Minutes),Unnamed: 17
2015-07-01,  WN,238.0,N233LV,DAL,12:30,12:34,55.0,48.0,4.0,12:41,7.0,0.0,0.0,0.0,0.0,0.0,
2015-07-01,  WN,285.0,N526SW,DAL,09:25,09:20,55.0,51.0,-5.0,09:27,7.0,0.0,0.0,0.0,0.0,0.0,
2015-07-01,  WN,311.0,N734SA,MDW,15:05,15:49,150.0,146.0,44.0,15:57,8.0,6.0,0.0,0.0,0.0,34.0,
```

## Selecting by substring

```
dallas = df['Destination Airport'].str.contains('DAL')

Date (MM/DD/YYYY)
2015-07-01    False
2015-07-01    False
2015-07-01    False
2015-07-01    False
2015-07-01     True
2015-07-01     True
```

returns a series that can be resampled and group functions can be applied to it

```
print(dallas.resample('D').sum())
print(dallas.resample('D').count())
```

