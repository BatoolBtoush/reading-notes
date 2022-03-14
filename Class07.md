# Readings For Class07

## **The Global Scope and Nonlocal**

We'd in the global Python scope from the minute we start any Python program. Python converts the main script of our program into a module called __main__, which is used to execute the main program. This module's namespace represents our program's whole global scope.

The interpreter executes the code in the module or script that acts as an entry point to your program whenever we run a Python program. The special name __main__ is defined for this module or script.

You get the list of names available in the primary global Python scope when we call dir() with no arguments. So that when we  give a new name (like var) ar the module's top level (__main__) , that name will be added to the list returned by dir ().

~~ important: Per program execution, there is only one global Python scope. This scope will exist until the program is finished and all of its names have been forgotten. Otherwise, the names would recall their values from the previous run the next time you ran the program.

We easily reference the value of var inside func().As it has no effect on the global name var, and it shows thatvar may be accessed freely from within func (). On the other hand, we can't assign global names inside functions unless we use a global statement.
As below:

```
>>> var = 100
>>> def func():
...     return var  # You can access var from inside func()
...
>>> func()
100
>>> var  # Remains unchanged
100
```

Basically, we can change or modify global names from anywhere in the global Python scope. Aside from that, we may use the global statement to change global names from practically anywhere in the code. But modifying global names is considered to be bad programming because it can lead to code that is:

1. Difficult to debug.
2. Impossible to reuse.

So instead, use local names rather than global names.

### ***The global Statement***

Assigning a value to a global name within a function results in the creation of a new local name in the function scope. You can use a global statement to change this behavior. This statement allows you to specify a list of names that will be handled as global names.

The global keyword is followed by one or more names separated by commas in the statement.  All names listed in a global statement are mapped to the global or module scope in which they are defined.

### ***The nonlocal Statement***

Nonlocal names can be retrieved from inner functions in the same way as global names can, but they cannot be assigned or changed. We must use a nonlocal statement if we want to change them. A nonlocal statement allows us to specify a list of names that will be treated as nonlocal.

The nonlocal statement consists of one or more names separated by commas, followed by the nonlocal keyword. These names will relate to the names in the Python scope that surrounds them.
 

<br>
<br>


## **Big O Notation**

Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm.

So basically Big O is a way of evaluating an algorithm’s rate of growth, as it describes the complexity of it and the importance of studying complexity is to look out for efficiency and time as they are related.

And here are some functions to help wrap my head around it:

O(1): Constant time complexity:

So the execution time of these algorithms is independent of the size or space of the input data.

O(N): Linear time complexity:

the execution time of these algorithms will grow is directly proportional to the size of the input data.

O(N²): Quadratic time complexity:

The execution time of these algorithms is directly proportional to the square of the size of the input data.

O(2^N): Exponential Time complexity:

It’s when the growth doubles with each addition to the input data set.

<br>

~~The time complexity of an algorithm is a measure of how long it takes an algorithm to run as a function of the input length. Similarly, an algorithm's space complexity estimates how much space or memory it takes to run as a function of the length of the input.

Both are dependent on a variety of external elements such as computer hardware, operating system and so on.
 

<br>
<br>


## **Random**

The Python Random module is a built-in module for generating random integers in Python. This module can be used to do things like generate random numbers, output a random value for a list or string.

```
import random
print(random.randint(1,6))
```
This would result in a random integer from 1 to 6.