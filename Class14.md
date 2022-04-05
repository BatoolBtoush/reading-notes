# Readings: Data Visualization

## **Introduction**

matplotlib is considered to be the single most used Python package for 2D-graphics. It provides both a very quick way to visualize data from Python and publication-quality figures in many formats.

## **IPython**
IPython is an enhanced interactive Python shell that has features including named inputs and outputs, access to shell commands, improved debugging. It allows interactive matplotlib sessions.

## **pyplot**
pyplot provides a convenient interface to the matplotlib object-oriented plotting library.

<br>

## **Visualizing statistical relationships**

Statistical analysis is the study of how variables in a dataset interact with one another and how those connections are influenced by other variables. Because when data is displayed appropriately, the human visual system can perceive trends and patterns that indicate a relationship, visualization can be a key component of this process.

Three seaborn functions; starting with relplot():

This is a figure-level function for showing statistical correlations using scatter plots and line plots, which are two common ways.scatter plots and line plots. relplot() combines a FacetGrid with one of two axes-level functions:

1. scatterplot() (with kind="scatter"; the default)

2. lineplot() (with kind="line")


<br>




## **Statistical Data Visualization With Seaborn**

The Python visualization library Seaborn is based on matplotlib and provides a high-level interface for drawing attractive statistical graphics.


Starting with importing:
```
>>> import matplotlib.pyplot as plt
>>> import seaborn as sns
```

The basic steps to creating plots with Seaborn are:
1. Prepare some data
2. Control figure aesthetics
3. Plot with Seaborn
4. Further customize your plot

```
>>> import matplotlib.pyplot as plt
>>> import seaborn as sns
>>> tips = sns.load_dataset("tips")
>>> sns.set_style("whitegrid")
>>> g = sns.lmplot(x="tip",
                    y="total_bill", 
                    data=tips,
                    aspect=2)
>>> g = (g.set_axis_labels("Tip","Total bill(USD)").
set(xlim=(0,10),ylim=(0,100)))
>>> plt.title("title")
>>> plt.show(g)

```
<br>

### ***Data***

```
> import pandas as pd
>>> import numpy as np
>>> uniform_data = np.random.rand(10, 12)
>>> data = pd.DataFrame({'x':np.arange(1,101),
 'y':np.random.normal(0,4,100)})
```
<br>

### ***Categorical Plots***

- **Scatterplot**:

>>> Scatterplot with one categorical variable 

>>> Categorical scatterplot with non-overlapping points

```
>>> sns.stripplot(x="species",
                  y="petal_length",
                  data=iris)
>>> sns.swarmplot(x="species",
                  y="petal_length", 
                  data=iris)
```

<br>

### ***Regression Plots***

Plot data and a linear regression model fit.

```
>>> sns.regplot(x="sepal_width",
                y="sepal_length", 
                data=iris,
                ax=ax)
```