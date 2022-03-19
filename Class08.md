# Readings: Game of Greed 3

## **List Comprehensions in Python**

There's another more concise way to write clean and elegent code when implementing lists, that is by using list comprehensions which are also more flexible for loopss. 

### ***Syntax***

```
my_new_list = [ expression for item in list ]
```
for example:
```
  rolls = ([random.randint(1, 6) for _ in range(6)]) 
  ```
  - ***expression is: random.randint(1, 6)*** and this would mean to generate random numbers between 1 and 6 inclusivly
  
  - ***item is: _*** not exactly noting to do anything to each item in the range, but including it either way
  
  - ***list is: range(6)***, this would generate a list of numbers. And we'd iterate through each item in that range, and save a copy of the item in a new list called rolls.

Each item in the list will be tested to an expression. What item is eventually stored in the output list is determined by the expression. 
Where here I'm creating a list using **range()**

<br>


~~ Adding a **filter** to the list comprehension gives more options. We can choose specific items from the list while ignoring others by applying filters. This is a Python list's advanced feature, for example:
```
even_numbers = [ x for x in range(1,20) if x % 2 == 0]
```

<br>


### ***Using list comprehensions with strings***
```
# a list of the names of popular authors
authors = ["Ernest Hemingway","Langston Hughes","Frank Herbert","Toni Morrison",
    "Emily Dickson","Stephen King"]

# create an acronym from the first letter of the author's names
letters = [ name[0] for name in authors ]
print(letters)
```
output: ['E', 'L', 'F', 'T', 'E', 'S']

 

<br>
<br>


## **Primer on Python Decorators**

Decorators make it easy to invoke higher-order functions using a straightforward syntax. And they can be defined as functions that take another function and modify its functionality without affecting it directly.

 However, to understand decorators, it is enough to think about functions as something that turns given arguments into a value.


<br>

### ***First-Class Objects***

 When a function is called a First-Class Object it means that it can be passed around and used as an argument, just like any other object (string, int, float, list)

 ```
 def say_hello(name):
    return f"Hello {name}"

def be_awesome(name):
    return f"Yo {name}, together we are the awesomest!"

def greet_bob(greeter_func):
    return greeter_func("Bob")

```
say_hello() and be_awesome() functions are regulare functions that expect a string as an input, but greet_bob() is a function that expect another function as an input.

If we were to do this and pass say_hello() and be_awesome() as arguments to greet_bob():

```
>>> greet_bob(say_hello)
'Hello Bob'

>>> greet_bob(be_awesome)
'Yo Bob, together we are the awesomest!'
```
The say_hello and be_awesome functions are named without parentheses. This means that only a reference to the functions is passed not that they're executed. But The greet_bob() function is written with parentheses, so it will be called as usual.


<br>

### ***Simple Decorators***

Decorators wrap a function, modifying its behavior. 

For example:
```
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

def say_whee():
    print("Whee!")

say_whee = my_decorator(say_whee)
```
What happens when say_whee() is called is the following:
```
>>> say_whee()
Something is happening before the function is called.
Whee!
Something is happening after the function is called.
```
The so-called decoration happens at the following line:
```
say_whee = my_decorator(say_whee)
```
In effect, the name say_whee now points to the wrapper() inner function. Keeping in mind that we return wrapper as a function when we call my_decorator(say_whee):
```
>>> say_whee
<function my_decorator.<locals>.wrapper at 0x7f3c5dfd42f0>
```
But since wrapper() has a reference to the original say_whee() as func, it will call that function between the two calls to print().

 

<br>
<br>


## **PySnooper For Debugging**

PySnooper is a poor man's debugger.

It goes like this when you're attempting to determine why your Python code isn't performing as expected. And you're wondering about which lines are running and which are not, as well as the values of the local variables. While some people would place print lines in strategic spots, with some of them displaying variable values.
But Instead of methodically creating the correct print lines, **PySnooper** allows you to perform the same thing by simply adding one decorator line to the function. You'll get a detailed log of your function's execution, indicating which lines were executed when and when local variables were updated.
```
import pysnooper

@pysnooper.snoop()
def ....
```
