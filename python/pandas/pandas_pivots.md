# USERS

```
,weekday,city,visitors,signups
0,Sun,Austin,139,7
1,Sun,Dallas,237,12
2,Mon,Austin,326,3
3,Mon,Dallas,456,5
```

## PIVOTING

Only one column values

```
visitors_pivot = users.pivot(index='weekday', columns = 'city', values='visitors')
```

```
city     Austin  Dallas
weekday
Mon         326     456
Sun         139     237
```

Several column values

```
visitors_pivot = users.pivot(index='weekday', columns = 'city')
```

```
        visitors        signups
city      Austin Dallas  Austin Dallas
weekday
Mon          326    456       3      5
Sun          139    237       7     12
```

## STACKING / UNSTACKING

```
users = users.set_index(['city', 'weekday'])
byweekday = users.unstack('weekday')


print(byweekday)

        visitors      signups
weekday      Mon  Sun     Mon Sun
city
Austin       326  139       3   7
Dallas       456  237       5  12

print(byweekday.stack(level='weekday'))

                visitors  signups
city   weekday
Austin Mon           326        3
       Sun           139        7
Dallas Mon           456        5
       Sun           237       12
```

## MELTING

```
weekday,Austin,Dallas
Mon,326,456
Sun,139,237
```

```
visitors_by_city_weekday = visitors_by_city_weekday.reset_index()
visitors = pd.melt(visitors_by_city_weekday , id_vars=['weekday'], value_name='visitors')


  weekday variable  visitors
0     Mon   Austin       326
1     Sun   Austin       139
2     Mon   Dallas       456
3     Sun   Dallas       237
```


```
,weekday,city,visitors,signups
0,Sun,Austin,139,7
1,Sun,Dallas,237,12
2,Mon,Austin,326,3
3,Mon,Dallas,456,5
```


```
print(pd.melt(users,id_vars=['weekday','city'], value_vars=['visitors','signups']))

  weekday    city  variable  value
0     Sun  Austin  visitors    139
1     Sun  Dallas  visitors    237
2     Mon  Austin  visitors    326
3     Mon  Dallas  visitors    456
4     Sun  Austin   signups      7
5     Sun  Dallas   signups     12
6     Mon  Austin   signups      3
7     Mon  Dallas   signups      5
```

## PIVOT_TABLE


```
,weekday,city,visitors,signups
0,Sun,Austin,139,7
1,Sun,Dallas,237,12
2,Mon,Austin,326,3
3,Mon,Dallas,456,5
```


```
pd.pivot_table(users,index='weekday',columns='city')

        signups        visitors
city     Austin Dallas   Austin Dallas
weekday
Mon           3      5      326    456
Sun           7     12      139    237
```

Aggregation functions

```
users.pivot_table(index='weekday',aggfunc='count')

         city  signups  visitors
weekday
Mon         2        2         2
Sun         2        2         2

```
