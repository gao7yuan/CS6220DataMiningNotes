# Week 2 Understanding Data
9/9/19

## Data Mining Tasks

## What is data
- what is in data
  - features
  - instances
    - a set of features
- instances, features, and classes
  - class: outcome variable that we try to predict

## Machine learning preliminaries
- formalizing the learning task
  - training data
- concept learning
- formalizing concept learning
- Given a training set, the (concept) learning algorithm has to estimate the function f or hypothesize about it.

### Inductive Learning Hypothesis
"Any hypothesis found to approximate the target function well over a large set of training examples will also approximate the target function well over other unobserved examples."

## Understanding Data
- data collection
- describing data
  - dimensionality
    - # of features
    - *the volume of the feature space increases so quickly that the available data become sparse*
  - sparsity
    - filled with empty space
    - problem for statistical methods
    - advantage because of less storage
  - resolution
    - too fine: pattern buried in noise
    - to coarse: pattern disappear
- exploration of data
  - table or multidimensional array
  - slice
  - dice
    - sub-cube
  - roll-up and drill-down
- identifying data quality problems
  - data quality
    - missing
      - how and why
      1. MCAR
        - missing not dependent on any value in dataset
      2. MAR
        - not dependent on missing or unobserved variables, but might depend on observed values
        - pattern identifiable
      3. MNAR
        - depend on missing or unobserved variables
        - particularly troublesome
    - noise and artifacts
      - noise: random
    - outliers
      - different or unusual
    - inconsistent
    - duplicate
**GIGO: Garbage In, Garbage Out**

## Summary Statistics
- modules to use
  - Pandas
  - NumPy

- how to use these modules

- basic usage
```python
# import
import pandas as pd
import numpy as np

# define array in np. n-dimensional array (ndarray) with 10,000 random numbers in the range [0-500)
values1 = np.random.randint(500, size=10000)

# define a pandas Series similar to above
values2 = pd.Series(np.random.randint(500, size=10000))

# print first 10 elements
values1[:10]
# output:
# array([441, 484, 201, 37, 0, 323, 3432, 2345, 543])
values2[:10]
# output:
# 0    345
# 1    454
# ...
# dtype: int32

# print last 10 elements
values2[-10:]

# built-in methods for basic statistics
# minimum value in the list
print 'MIN(values1) = ' + str(values1.min()) + '\t\t\tMIN(values2) = ' + str(values2.min())
# range of the values
values1.ptp()
# mean of the values
values1.mean()
# standard deviation of the values
values1.std()
# the variance of the values
values1.var()

# pandas series have a method `describe()` that returns a nice summary of these basic statistics
values.describe()
# output:
# count     100000.000000
# mean      xxxxx
# ...

# for non-numerical series objects, return a simple summary of the number of unique values and most frequently occurring ones
s = pd.Series(['a', 'a', 'b', 'b', 'a', 'a', np.nan, 'c', 'd', 'a'])
# np.nan: missing data
s.describe()
# count     9
# unique    4
# top       a
# freq      5
# dtype: object
```

- handling missing data with pandas
```python
# create a pandas DataFrame with 5 rows and 3 cols
df = pd.DaraFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'], columns=['one', 'two', 'three'])
# add two more columns
df['four'] = 'bar'
df['five'] = df['one'] > 0
# add new rows
df2 = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
# quickly access column
df2['one']
# access row
df2.loc['a']

pd.isnull(df2['one']) # check missing value
pd.notnull(df2['one']) # opposite

# propagation
# arithmetic operations
a = df[['one', 'two']]
a.loc[['a', 'c'], 'one'] = float('nan')
a
## will return a table with columns one and two, with a and c row of one replaced by nan

a + b
a - b

# go through whole data table and drop all instances (rows) corresponding to missing data
a['one'].dropna()

# sum in column one, ignore nan
a['one'].sum()

# mean of row
a.mean(1)
```

- Histograms
```python
pdhist = values2.hist()
pdhist2 = values.hist(bins=20, color='r', alpha=0.4, figsize=(10, 6))

# numpy + matplotlib
import matplotlib.pyplot as plt
nphist = plt.hist(values1)
```
- Boxplots
```python
# pandas
df = pd.DataFrame(rand(10, 2), columns=['Col1', 'Col2']) # 10 rows 2 cols?
df.head() # show top 5 rows?

box = df.boxplot(grid=False, return_type='axes')

# numpy
fig = plt.figure()
ax = fig.add_subplot(111)

x1 = np.random.normal(0, 1, 50)
x2 = np.random.normal(1, 1, 50)

npbox = ax.boxplot([x1,x2])
```

- Scatterplots
```python
# pandas
df = pd.DataFram(rand(200, 2))
pdscatter = plt.scatter(df[0], df[1])

# numpy
x = np.random.randn(200) # array length 200
y = np.random.randn(200)

fig = plt.figure()
ax = fig.add_subplot(111)

npscatter = ax.scatter(x, y, color='r')
```
