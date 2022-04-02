# **Readings: Linear Regressions**

## **Linear Regression in Python**

<br>

### ***What is Regression?***

**Regression** looks for relations between variables.
For example, we can observe multiple employees of a company to see how their salaries are affected by factors such as experience, level of education, role, and location of employment.
This is a regression problem in which each employee's data represents one observation. The idea is that experience, education, role, and city are all independent factors that influence income.

Generally speaking, in most regression analyses, a phenomenon of interest is examined, along with a number of observations. There are two or more features in each observation. And we try to establish a relationship between the features based on the assumption that (at least) one of them is dependent on the others.

- **The dependent features** are called the dependent variables, outputs, or responses.

- **The independent features** are called the independent variables, inputs, or predictors.

<br>

<br>

### ***When Do We Need Regression?***

1. When we need to answer whether and how some phenomenon influences the other or how several variables are related.

2. When we want to forecast a response using a new set of predictors.

<br>

<br>

### ***Problem Formulation***

When implementing linear regression of some dependent variable 𝑦 on the set of independent variables 𝐱 = (𝑥₁, …, 𝑥ᵣ), where 𝑟 is the number of predictors, you assume a linear relationship between 𝑦 and 𝐱: 𝑦 = 𝛽₀ + 𝛽₁𝑥₁ + ⋯ + 𝛽ᵣ𝑥ᵣ + 𝜀. This equation is the regression equation. 𝛽₀, 𝛽₁, …, 𝛽ᵣ are the regression coefficients, and 𝜀 is the random error.

<br>

### ***Linear Regressions:***

1. **Simple Linear Regression**

        - single independent variable, 𝐱 = 𝑥

        - The estimated regression function (black line) has the equation 𝑓(𝑥) = 𝑏₀ + 𝑏₁𝑥.

![Simple Linear Regression](imgs/SimpleLinearRegression.png)

<br>


2. **Multiple Linear Regression**

Multiple linear regression is a case of linear regression with two or more independent variables.

The estimated regression function is 𝑓(𝑥₁, 𝑥₂) = 𝑏₀ + 𝑏₁𝑥₁ + 𝑏₂𝑥₂.

<br>

3. **Polynomial Regression**

Polynomial regression can be thought of as a more generalized version of linear regression. We expect a polynomial relationship between the output and the inputs, and thus a polynomial calculated regression function.

Regression function 𝑓 can incorporate non-linear components like𝑏₂𝑥₁², 𝑏₃𝑥₁³, or even 𝑏₄𝑥₁𝑥₂, 𝑏₅𝑥₁²𝑥₂, in addition to linear terms like  𝑏₁𝑥₁.


<br>

<br>


## **How to run Linear regression in Python scikit-Learn**


Scikit-learn is a sophisticated Python machine learning tool. It includes techniques like r egression, classification, clustering, model selection, and dimensionality reduction. "Methods intended for regression in which the target value is supposed to be a linear combination of the input variables" are found in the sklearn.linear model package.

<br>

The first step is to import the required Python libraries into Ipython Notebook.
```
import numpy as np
import pandas as pd
import scipy.stats as stats
imprt matplotlib.pyplot as plt
import sklearn
```

<br>

The data set is available in sklearn Python module, and it can be accessed by using scikitlearn.

```
from sklearn.datasets import "data set name"
variable_to_store_the_data_set = data_set_name()
```
<br>

To convert the data set into a pandas data frame:
```
data = pd.DataFrame(variable_to_store_the_data_set.data)
data.head()
```

<br>

<br>

### ~ Important functions to keep in mind while fitting a linear regression model are:

1. **lm.fit():** fits a linear model

2. **lm.predict():** Predict Y using the linear model with estimated coefficients

3. **lm.score():** Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.


<br>

<br>


## **Overfitting/Underfitting**

We divide our data into two subsets: training data and testing data (and often three: train, validate, and test), and fit our model to the train data in order to make predictions on the test data. When we do that, one of two things can happen: our model will either be overfit or underfit.We don't want any of these things to happen since they may cause our model to be unpredictably inaccurate which means we won't be able to generalize our predictions to other data.

<br>

### ***Overfitting***

Overfitting occurs when a model is now too closely matched to the training dataset. This frequently occurs when the model is very complex (there are too many features/variables in relation to the amount of data). On training data, this model will be quite accurate, but on untrained or new data, it will most likely be very inaccurate. It's because this model isn't generic, which means we won't be able to extrapolate the conclusions to other data.

<br>

### ***Underfitting***

When a model is underfitted, it signifies that it does not fit the training data and hence misses the data's trends. It also indicates that the model can't be used with new data. This is usually the result of a very simple model (not many predictors/independent variables). It could also happen if we try to fit a linear model (like linear regression) to non-linear data. This model will very certainly have poor prediction power (on training data only, and cannot be extended to additional data).

![Underfitting and Overfitting](imgs/underfitting-overfitting.png)