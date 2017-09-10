# PANDAS

## Cars Dataset

```
,cars_per_cap,country,drives_right
US,809, United States, True
AUS,731 , Australia,False
JAP,588,  Japan,False
IN, 18,  India,False
RU,200, Russia, True
MOR, 70,Morocco, True
EG, 45,  Egypt, True
```

### Define a new index

```
row_labels = ['US', 'AUS', 'JAP', 'IN', 'RU', 'MOR', 'EG']
cars.index= row_labels
```

### Reading CSV Files and set index

```
cars = pd.read_csv('cars.csv', index_col=0)
```


### Print by Index

```
cars.loc[['AUS','EG']]
```


### Print by Index and Column

```
cars.loc[['RU','MOR'],['country','drives_right']]
cars.loc[:,['cars_per_cap','drives_right']]
```

### Select by condition

```
dr = cars['drives_right']
sel = cars[dr]
```

```
cars[cars['drives_right']]
```

### And/Or conditon

```
cars[np.logical_and( cars['cars_per_cap'] > 100 , cars['cars_per_cap'] < 500 ) ]
```

If you instead do this

```
cars[cars['cars_per_cap'] > 100 & cars['cars_per_cap'] < 500  ]
```

you will get the error

```
ValueError: The truth value of a Series is ambiguous. Use a.empty, a.bool(), a.item(), a.any() or a.all().
```
Since the series is a labeled one-dimensional array, you can must retrieve values to make it work

```
cars[(cars['cars_per_cap'] > 100).values & (cars['cars_per_cap'] < 500).values ]
``