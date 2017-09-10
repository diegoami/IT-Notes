# GROUPS


## Basic


```
titanic.groupby('pclass')['survived'].count()
titanic.groupby(['embarked','pclass'])['survived'].count()
```

```
sales.groupby(['state'])['eggs','salt','spam'].sum()
```


## Grouping using another dataframe

life
```
Country,1964,1965,1966
Afghanistan,33.639,34.152,34.662
Albania,65.475,65.863,66.122,
```

region
```
Country,region
Afghanistan,South Asia
Albania,Europe & Central Asia
Algeria,Middle East & North Africa
```

```
life_by_region = life.groupby(regions['region'])['2010'].mean()
```


## Aggregating

```
titanic.groupby('pclass')[['age','fare']].agg(['max','median'])

         age             fare
         max median       max   median
pclass
1       80.0   39.0  512.3292  60.0000
2       70.0   29.0   73.5000  15.0458
3       74.0   24.0   69.5500   8.0500

```

```
print(titanic.groupby('pclass')[['age','fare']].agg(['max','median']).loc[:, ('age','max')])
```


