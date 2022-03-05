# Readings For Class04

## ***Classes and Objects***

**Classes** can be defined as the template used to create an **Object**, where an **Object** is a container that holds variables and functions in a single entity, by getting them from the template aka **Classes**.

~ ***How to assign a template or a **Class** for a given **Object**?***

By creating a variable and assign it to the class's name. As can be seen below on **line 7**
```
1 class MyClass:
2    variable = "blah"
3
4    def function(self):
5       print("This is a message inside the class.")
6
7 myobjectx = MyClass()
```

~ ***How to access the object's variables?***

By writing the variable name of the created object followed by a dot then the name of the variable inside the object that I want to access. As shown below:
```
myobjectx.variable
```

~ **Important note**:

I can assign multiple objects for a given class, which means they would share different copies of the same variables and functions. And a change happening in one object doesn't affect the rest of the objects.


~ ***How to access the object's functions?***

Same procedure with accessing object's variables (using the dot notation). As shown below:
```
myobjectx.function()
```


~ ***The __init__() function***

A function that's called when the class is first being initiated. And it's used for asigning values in the given class.
 

<br>
<br>


## ***Thinking Recursively in Python***

The key concept of **Recusive thinking** is:

Solving a big problem can be done by dividing it into subproblems and solvong each one of them at a time.

	
<br>

**Recursive Function** can be defined as the function that refers or calls itself repeatidly until a certain condition is met then it returns a value. And the structure for all Recursive Functions is the same, as it's made up of two parts:
1. **Base Case**
2. **Recurise Case**

	
<br>


~ The procedure followed to solving any recursive function is by having each recursive call add a stack frame to the **call stack** until the base case is reached. Then, the stack begins to unwind as each call returns its results

	
<br>


### **Recursive Data Structures in Python**

A data structure is recursive if it can be deﬁned in terms of a smaller version of itself, and in Python, **list**, **setes** and **dictionaries** are considered to be recursive data structures.
 

<br>
<br>


## ***Python Testing with pytest: Fixtures and Coverage***


<br>

### **Fixtures**

When writing pytests, I could use general data to be shared among all the test function when invoked, and here comes the importance of **Fixtures** as they provide a defined, reliable and consistent context for the tests.

The services, state, or other operating environments or any general data set up by fixtures can be accessed by test functions through **arguments**. For each fixture used by a test function there is typically a parameter (named after the fixture) in the test function’s definition.

~ **How to define or write an Fixture?**

You can tell pytest that a particular function is a fixture by decorating it with **@pytest.fixture**


<br>

### **Coverage**

After writing tests for functions in your actual code, can you be certain that you've actually tested all of the possible paths of those functions?

To be 100% accurate that a certain function makes sense decpite passing the test you wrote for it, there's a package called **pytest-cov** on PyPI that can be downloaded and installed to help make sure of that. 

And after that's done, you can invoke pytest with the **--cov option**. This way you'll get a coverage report for every part of the Python library that your program or code used.
