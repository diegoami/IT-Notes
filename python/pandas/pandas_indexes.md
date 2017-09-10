# PANDA INDEX

## CHANGE INDEX

```
       eggs  salt  spam
month
Jan      47  12.0    17
Feb     110  50.0    31
Mar     221  89.0    72
Apr      77  87.0    20
May     132   NaN    52
Jun     205  60.0    55
```

Numeric index

```
sales.index = range(len(sales))

   eggs  salt  spam
0    47  12.0    17
1   110  50.0    31
2   221  89.0    72
3    77  87.0    20
4   132   NaN    52
5   205  60.0    55
```

Upper index

```
new_idx = [idx.upper() for idx in sales.index]
sales.index = new_idx

     eggs  salt  spam
JAN    47  12.0    17
FEB   110  50.0    31
MAR   221  89.0    72
APR    77  87.0    20
MAY   132   NaN    52
JUN   205  60.0    55
```

Composite index
```

,state,month,eggs,salt,spam
0,CA,1,47,12.0,17
1,CA,2,110,50.0,31
2,NY,1,221,89.0,72
3,NY,2,77,87.0,20
4,TX,1,132,,52
5,TX,2,205,60.0,55

sales = sales.set_index(['state', 'month'])
             eggs  salt  spam
state month
CA    1        47  12.0    17
      2       110  50.0    31
NY    1       221  89.0    72
      2        77  87.0    20
TX    1       132   NaN    52
      2       205  60.0    55
```

Now accessible this way

```
NY_month1 = sales.loc[('NY',1),:]
CA_TX_month2 = sales.loc[(['CA','TX'],2),:]
sales.loc[pd.IndexSlice[:,2] ,:]
```

## SORTING INDEX

```
,Country,Year,fertility,life,population,child_mortality,gdp,region
0,Afghanistan,1964,7.671,33.639,10474903.0,339.7,1182.0,South Asia
1,Afghanistan,1965,7.671,34.152,10697983.0,334.1,1182.0,South Asia
2,Afghanistan,1966,7.671,34.662,10927724.0,328.7,1168.0,South Asia

pd.read_csv('../data/gapminder_2.csv',index_col=['Year','region','Country']).sort_index()
```