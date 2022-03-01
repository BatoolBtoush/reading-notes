# Readings: Testing and Modules

## ***Unit tests and TDD***

Those two definitions are ways to check the behavior of our code, while the **Unit tests** are codes I specifically write to exercise the input and output of some code, and **Test-Driven Development** (TDD) is a strategy to think and write, tests first.


<br>

Starting with the **Unit tests**

**1-** We have to write out functions that explicitly describe the functionality I want the test to do and the what is expected of it, basically some sort of documentation.

Just like in this code, where the name of the function is a perfect example of documentation:

```
def test_should_return_female_when_the_name_is_from_female_gender():
    detector = GenderDetector()
    expected_gender = detector.run(‘Ana’)
    assert expected_gender == ‘female’
```



**2-** Keeping in mind the naming convention of the test file and its relation to the module file I want to test.

But while also separating the two folders


**3-** Now going for the part of running the actual test, while following a convention called **AAA: Arrange, Act and Assert**


- **Arrange:** you need to organize the data needed to execute that piece of code (input).

- **Act:** here you will execute the code being tested (exercise the behavior).

- **Assert:** after executing the code, you will check if the result (output) is the same as you were expecting by using a testing tool.


**4-** If the test fails -and it will-, think about an important thing about **TDD** called **cycle** at it's made up of three steps:

- 🆘 Write a unit test and make it fail (it needs to fail because the feature isn't there).

- ✅ Write the feature and make the test pass! 
- 🔵 Refactor the code.



Now as for implementing the feature, it's about writing a method or a function that returns the right answer or the expected output.

As in:

```
def run(self, name):
    return 'female'
```

This is in reference  to: [In Tests We Trust — TDD with Python](https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932)
 

<br>
<br>


## ***What does the ``if __name__ == “__main__”:`` do***

If a source file is being run by the python interpreter or is the entry point for my code, the ``__name__`` variable is set to a value of ``__main__``.

But if this file or module is being imported in another file, the ``__name__`` variable is set to the module's name.

<br>

**-->** This if statement helps with knowing whether my script is being run directly or being imported by something else.

As it only allows the execution of some code only if the file is run directly not imported.
 

<br>
<br>


## ***Recursion***

Recursion is the process in which a function calls itself inside the function (directly or indirectly), and this function is called a recursive function.

This process helps in solving complex codes in algorithms in an easier way.

The idea of recursion, is to solve a big problem by breaking it down into smaller problems until I reach something called the base case, which is a case that is provided with a solution and the solution to the bigger problems in the same function is based of of that smaller problems until the base case is reached and once it's reached the the recursive function is stopped.

But if the base case is wrong or undefined, this would lead to stackoverflow errors.

**-->** **Direct and indirect calling of the  recursive function:**

It's direct when the function calls itself.

And indirect when the function calls another function, and this other function calls the first function
 

<br>
<br>


## ***Python Lists***

Lists are donated by square brackets [], and can be accessed with len() which identifies its length, and [] with index.

When assignment happens:
``` 
nums =[1,2,3,4,5]
other = nums
```

It means that the variables nums and other are both pointing at the list, not making a copy of the list for the other variable. 
 

<br>
<br>


## ***Python Strings***

Strings are donated by single quotes '' or double quotes "".

A string literal can span multiple lines, if there was a backslash \ at the end of each line to escape the newline. As they can also be inside triple quotes, """ or ''' and then they can span multiple lines of text.

Strings are considered to be immutable, which means that once they're set they can't be changed, but they can still be accessed with [] indices, as the string literals are like that of a list, therefore the len() function can work on strings and it returns the length of the said string.