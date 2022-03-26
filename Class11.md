# Readings: Data Analysis

## **What is Jupyter Lab**

Jupyter is a multilingual, web-based, open-source data science application. It facilitates interactive data science and scientific computing across several programming languages via the idea of notebooks, fostering reuse and reproducibility.

taken from: [JupyterLab is the data science UI we have been looking for](https://towardsdatascience.com/jupyterlab-you-should-try-this-data-science-ui-for-jupyter-right-now-a799f8914bb3)

JupyterLab provides a flexible, integrated, and expandable environment for working with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components.

<br>

<br>


## **NumPy Tutorial: Data Analysis with Python**

NumPy is a Python data analysis library that is widely used. NumPy allows you to speed up your work while also allowing you to interact with other Python packages.

The data is written as such: (semicolon separated values) format, each record is separated by a semicolon (;), and rows are separated by a new line.

```
"fixed acidity";"volatile acidity";"citric acid";"residual sugar";"chlorides";"free sulfur dioxide";"total sulfur dioxide";"density";"pH";"sulphates";"alcohol";"quality"

7.4;0.7;0;1.9;0.076;11;34;0.9978;3.51;0.56;9.4;5
7.8;0.88;0;2.6;0.098;25;67;0.9968;3.2;0.68;9.8;5
```

### ***Numpy 2-Dimensional Arrays***

A 2-dimensional array is a matrix, and it’s just a different way of thinking about a list of lists. A matrix has rows and columns. By specifying a row number and a column number, we're able to extract an element from a matrix.

***Creating A NumPy Array***

To create a NumPy array using the ```numpy.array function```. If we pass in a list of lists, it will automatically create a NumPy array with the same number of rows and columns.


***limitations of NumPy***

Is that all the elements in an array have to be of the same type.

The steps:

1. Import the numpy package.
2. Pass the list of lists wines into the array function, which converts it into a NumPy array.
3. Exclude the header row with list slicing.
4. Specify the keyword argument dtype to make sure each element is converted to a float.
```
import csv
with open("winequality-red.csv", 'r') as f:
    wines = list(csv.reader(f, delimiter=";"))
import numpy as np
wines = np.array(wines[1:], dtype=np.float)
```

<br>

### ***Alternative NumPy Array Creation Methods***

using ```numpy.zeros```; to create an array where every element is zero. The below code will create an array with 3 rows and 4 columns, where every element is 0:
```
import numpy as np
empty_array = np.zeros((3,4))

empty_array
```

### ***CREATING ARRAYS***
```np.array([1,2,3])``` - One dimensional array

```np.array([(1,2,3),(4,5,6)])``` - Two dimensional array

```np.zeros(3)``` - 1D array of length 3 all values 0


```np.ones((3,4))```- 3x4 array with all values 1
