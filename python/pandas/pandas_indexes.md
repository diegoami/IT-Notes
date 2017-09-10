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

