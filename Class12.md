# Readings: Topic for Class12

## **Pandas**

What's really interesting about pandas is that it covers a lot of other packages. Pandas is a base package with functionality taken from a number of other packages. That means we can work entirely with pandas.

In Python, pandas is similar to Excel in that it uses tables (specifically DataFrame) and performs data manipulations. However, it is capable of much more.

<br>

<br>


## **Getting started with Pandas**

- The data does pandas handle:
A **DataFrame** is a 2-dimensional data structure that can store data of different types (including characters, integers, floating point values, categorical data and more) in columns.

A table of data is stored as a pandas **DataFrame** 

Each column in a **DataFrame** is a Series.

- Pandas provides the **read_csv()** function to read data stored as a csv file into a pandas DataFrame. pandas supports many different file formats or data sources out of the box (csv, excel, sql, json, parquet).

Getting data in to pandas from many different file formats or data sources is supported by read_* functions.

<br>

<br>


## **Pandas in 10**

~ It can be imported as such:
```
import numpy as np
import pandas as pd
```

<br>

~ Object creation:
Creating a series by passing a list of values, using Series as such:
```
s = pd.Series([1, 3, 5, np.nan, 6, 8])
```

<br>

### ***Viewing data***

To view the top rows of the frame:
```
df.head()
```

To view the bottom rows of the frame:
```
df.tail(3)
```
Display the index:
```
df.index
```
Display the columns:
```
df.columns
```

<br>

~ To shows a quick statistic summary of your data:
```
df.describe()
```

<br>

### ***Grouping***

This means involving one or more of the following steps:

1. Splitting the data into groups based on some criteria.

2. Applying a function to each group independently

3. Combining the results into a data structure

<br>

### ***Plotting***
using matplotlib API:
```
import matplotlib.pyplot as plt
```
