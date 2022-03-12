# Readings: Game of Greed 1

## **Random Module**

The random module gives access to functions that help with a range of operations. But the most significant feature is the ability to generate random numbers.

1. **Randint**:
This function takes two parameters, a lowest and a highest number and it generates a random number between these two parameters (only integers).

The below Radint function will generate either (1,2,3,4,5)
``` 
import random
print(random.randint(0, 5))
```

2. **Random**: 
To get a larger random number this function can be used, and it takes no arguments.
```
import random
random.random() * 100
```


3. **Choice**:
The choice function is used for choosing a random element from a list.

```
import random
myList = ["batool", 22, True, 10,]
random.choice(myList)
```

4. **Shuffle**:
This function shuffles or randomize the elements order in the list in place.
The code below would result in something like this:
[[9], [8], [0], [4], [3], [2], [5], [6], [1], [7]]
```
from random import shuffle
x = [[i] for i in range(10)]
shuffle(x)
print(x)
```

5. **Randrange**:
This function generates randomly selected element from a range. with this syntax: ***random.randrange(start, stop[, step])***

```
import random
for i in range(3):
    print(random.randrange(0, 101, 5))
```
The code above would result in something like this:
```
75

0

45
```


<br>
<br>

## **Risk Analysis in Software Testing**

Risk analysis in software testing is the process of detecting and prioritizing problems in applications or software that you have built. After that, the process of assigning a risk level is completed. The risk is categorizes, and the impact of the risk is calculated as a result.


### *Why use Risk Analysis?*

The reason for using risk analysis when creating a project is to determine any possible threats or problem areas that might occue, because once we identify them it becomes much easier for us the developers to manage them.

And those risks or threat can be:
1. Use of new hardware
2. Use of new technology
3. Use of new automation tool
4. The sequence of code
5. Availability of test resources for the application
6. The time that you allocated for testing.
7. A defect leakage due to the complexity or size of the application.
8. Urgency from the clients to deliver the project.
9. Incomplete requirements
 

And in order to manage the situation and all the possible threat certain steps have to be followed:

1. Conduct Risk Assessment review meeting.
2. Use maximum resources to work on high-risk areas.
3. Create a Risk Assessment database for future use.
4. Identify and notice the risk magnitude indicators: high, medium, low.


<br>
<br>


## **TestCoverage**

Test coverage is a way for determining whether or not our test cases cover the application code and how much code is exercised when those test cases are run.

It helps with:

- Finding if there's a requirement not implemented by a set of test cases.
- Creating additional test cases to increase coverage.
- Identifying a quantitative measure of test coverage, which is an indirect method for quality check
- Identifying meaningless test cases that do not increase coverage.


<br>
<br>



## **Big O Notation**

Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm.

So basically Big O is a way of evaluating an algorithm's rate of growth, as it describes the complexity of it and the importance of studying complexity is to look out for efficiency and time as they are related.

And here are some functions to help wrap my head around it:

- O(1): Constant time complexity:

    So the execution time of these algorithms is independent of the size or space of the input data.

- O(N): Linear time complexity:

    the execution time   of these algorithms will grow is directly proportional to the size of the input data.

- O(N²): Quadratic time complexity:

   The execution time of these algorithms is directly proportional to the square of the size of the input data.

- O(2^N): Exponential Time complexity:

   It's when the growth doubles with each addition to the input data set.

 

Big O's role in algorithm efficiency is to describe the worst-case efficiency that an algorithm can attain when performing its function. It emphasizes on the Space and Time. In order to investigate these limiting variables, There are 4 other areas to consider:

1. Size of the input

2. Measurement Systems

3. Growth Sequences

4. Best-case scenario, worst-case scenario, and average-case scenario


<br>
<br>

## **Dependency Injection**

Dependency injection is the process of passing the task of building the object to someone else and then using the dependency directly.

There are three types of dependency injection:

1. constructor injection: the dependencies are provided through a class constructor.

2. setter injection: the client exposes a setter method that the injector uses to inject the dependency.

3. interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.