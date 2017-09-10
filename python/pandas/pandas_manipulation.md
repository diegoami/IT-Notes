# Weather dataset

```
,Wban,date,Time,StationType,sky_condition,sky_conditionFlag,visibility,visibilityFlag,wx_and_obst_to_vision,wx_and_obst_to_visionFlag,dry_bulb_faren,dry_bulb_farenFlag,dry_bulb_cel,dry_bulb_celFlag,wet_bulb_faren,wet_bulb_farenFlag,wet_bulb_cel,wet_bulb_celFlag,dew_point_faren,dew_point_farenFlag,dew_point_cel,dew_point_celFlag,relative_humidity,relative_humidityFlag,wind_speed,wind_speedFlag,wind_direction,wind_directionFlag,value_for_wind_character,value_for_wind_characterFlag,station_pressure,station_pressureFlag,pressure_tendency,pressure_tendencyFlag,presschange,presschangeFlag,sea_level_pressure,sea_level_pressureFlag,record_type,hourly_precip,hourly_precipFlag,altimeter,altimeterFlag,junk
0,13904,20110101,53,12,OVC045, ,10.00, , , ,51, ,10.6, ,38, ,3.1, ,15, ,-9.4, , 24, ,15, ,360, , , ,29.42, , , , , ,29.95, ,AA, , , ,29.95,
1,13904,20110101,153,12,OVC049, ,10.00, , , ,51, ,10.6, ,37, ,3.0, ,14, ,-10.0, , 23, ,10, ,340, , , ,29.49, , , , , ,30.01, ,AA, , , ,30.02,
2,13904,20110101,253,12,OVC060, ,10.00, , , ,51, ,10.6, ,37, ,2.9, ,13, ,-10.6, , 22, ,15, ,010, , , ,29.49, ,1, ,030, ,30.01, ,AA, , , ,30.02,
3,13904,20110101,353,12,OVC065, ,10.00, , , ,50, ,10.0, ,38, ,3.1, ,17, ,-8.3, , 27, , 7, ,350, , , ,29.51, , , , , ,30.03, ,AA, , , ,30.04,
```

## Simple operationg

Convert as string

```
df_dropped['date'] = df_dropped['date'].astype(str)
```

Convert to other format

```
df_dropped['Time'] = df_dropped['Time'].apply(lambda x:'{:0>4}'.format(x))
```

To datetime

```
date_times = pd.to_datetime(date_string, format='%Y%m%d%H%M')
```

To numeric

```
df_clean['wind_speed'] = pd.to_numeric(df_clean['wind_speed'], errors='coerce')
```


## Mapping on series

```
          state   total      Obama     Romney  winner  voters
county
Adams        PA   41973  35.482334  63.112001  Romney   61156
Allegheny    PA  614671  56.640219  42.185820   Obama  924351
Armstrong    PA   28322  30.696985  67.901278  Romney   42147
Beaver       PA   80015  46.032619  52.637630  Romney  115157
Bedford      PA   21444  22.057452  76.986570  Romney   32189
```

Now this code adds a second column based on other values. Map can be applied on a series
```
red_vs_blue = {'Obama':'blue', 'Romney':'red'}
election['color'] = election['winner'].map(lambda x: red_vs_blue[x])
```