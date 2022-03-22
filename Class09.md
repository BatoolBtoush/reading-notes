# Readings: Game of Greed 4

## **Dunder Methods**

These special or magic methods in Python are a collection of predefined methods we can use to improve our classes. They can be caught directly because they start and end with double underscores, as: __ init __ and __ str __.

And that's why they're known as dunder, shortcut to saying under under.

They can be used for mimicing the behavior of built-in types. For example, ***len('string')*** which is used to get the length of a string, but if we were to use it with empty classes this would raise an error, as below:
```
class NoLenSupport:
    pass

>>> obj = NoLenSupport()
>>> len(obj)
TypeError: "object of type 'NoLenSupport' has no len()"
```
So instead, we can add double underscores to the built-in method of len, as such: __ len __
```
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```

<br>

### ***Enriching a Simple Account Class***

The best use of dunder methods is to write a more enriched classes, and here are a few steps:

1. ***Object Initialization: __ init __***

As the name suggests this dunder method is going to be used for constructing my classes objects as it takes care of setting up the object. And it would be in the beginning, in what we call a **constructor**:
```
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
```
And the class objects would be created as such:
```
>>> acc = Account('bob')  # default amount = 0
>>> acc = Account('bob', 10)
```
<br>

2. ***Object Representation: __ str __ , __ repr __***

As the name suggests these dunder method is going to be used for cRepresentating my classes objects:

- __ repr __ : An object's "official" string representation. This is how you would create a class object. The purpose of repr is to be clear.

- __ str __: An object's "informal" or pleasantly readable string representation. This is for the convenience of the end user.

<br>
<br>


## **Basic Statistics in Python**

Probability answers the simple question, “What is the chance of an event happening?” An event is seen as the outcome of some sort. But while also calculating the chance of an event happening, we also need to consider all the other events that can occur. 

to get the likelihood of an event happening we divide the number of times the event of interest can occur by the sample space.

Probability provides us with a framework for predicting how frequently incidents will occur. We can use statistics to generate probabilities based on real-world observations and compare them to the ideal.

We'll obtain our data by flipping a coin 10 times and counting how many heads we get. A series of ten coin tosses will be referred to as a trial. The number of heads we see will be our data point. We predict the average number of heads in all of our experiments to approach 50% if we conduct a large number of trials. The code below determines the average fraction of heads observed after simulating 10, 100, 1000, and 1000000 trials. .
```
import random
def coin_trial():
heads = 0
for i in range(100):
    if random.random() <= 0.5:
        heads +=1
    return heads
def simulate(n):
    trials = []
    for i in range(n):
        trials.append(coin_trial())
    return(sum(trials)/n)
simulate(10)

>>> 5.4
simulate(100)
>>> 4.83
simulate(1000)
>>> 5.055
simulate(1000000)
>>> 4.999781
```
The coin_trial function is what represents a simulation of 10 coin tosses. It uses the random() function to generate a float between 0 and 1, and increments our heads count if it’s within half of that range. Then, simulate repeats these trials depending on how many times you’d like, returning the average number of heads across all of the trials. The coin toss simulations give us some interesting results.