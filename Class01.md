>## ***Pain vs. Suffering***

Although the pain we're going to go through during this course would be the ultimate test to our mental, physical and emotional health, it would still be the stepping stone to building the confident, capable and creative full-stack web developers that we'll officially be by the end of it.

That's why an important distinguish has been made between **pain and suffering**.

As the first highlights the end goal which is to build an better life, and the latter is just pain with no greater purpose, and that's exactly the opposite of what we're doing here.
<br>
</br>
<br>
</br>

>## ***Big O Notation***

"Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm."
Taken from: [A beginner's guide to Big O Notation](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation)


So basically Big O is a way of evaluating an alogrithm's rate of growth, as it descirbes the complexity of it and the importance of studying complexity is to look out for efficiency and time as they are related.

And here are some fucntions to help wrap my head around it:

1. O(1): Constant time complexity

    So the execution time of these algorithms is independent of the size or space of the input data.

2. O(N): Linear time complexity
the execution time of these algoithms will grow is directly proportional to the size of the input data.

3. O(N²): Quadratic time complexity

    The execution time of these algorithms is directly proportional to the square of the size of the input data.

4. O(2^N):  Exponential Time complexity

    It's when the growth doubles with each addition to the input data set.
<br>
</br>
<br>
</br>

>## ***Python Names and Values***

Main idea is that the syntax to python works just like any other language but still there has to be some clearance made.



- How assignment works: x is assigned a value of 23
``` 
x =23
```





- Re-assignment happens independatly: here y is still 23 despite x changing its value to 12
```
x =23
y = x
x =12
```



- Assignments never copies data: here both nums and other are pointing at the same list, not copying it
```
nums =[1,2,3]
other = nums
```

- Lots of things are references, like objects attributes, list elements, dictionary values, basically anything to the left of an assignment.
<br>
</br>
<br>
</br>

>## ***The Python Environment***

1. **The Interpreter**

   using an interpreter rather that directly python, is a lot more convnient as some programs would require different python versions.



Starting with **Pyenv**, which is a set of tools, such as:

-  pyenv: installs python and later helps intall an interpreter
- pyenv-virtualenv: configures global tools

<br>
</br>

2. **Dependency Management**
   
    As managing projects can get messy there are tools to help with that.

starting with **Poetry**, as it takes care of managing dependency of the projects, and seperating them via virtual environments.

Or using **pip and pyenv-virtualenv**

<br>
</br>

3. **Consistent Formatting and Readability**

   There are tools to help make sure of my project's code being easy and consistent to read not only by me but by others who I might be working with.

Starting with **Black**, which is a tool that focuses on what is necessary, the content. It does that by freeing you from manual code formatting through automation. 
Taken from: [How to Setup an Awesome Python Environment for Data Science or Anything Else](https://towardsdatascience.com/how-to-setup-an-awesome-python-environment-for-data-science-or-anything-else-35d358cc95d5)

<br>
</br>

4. **Type-Correctness**

    To help insure that when I'm writing my code it's free of errors, I can use tools that make sure of whether the types of variables and functions are really what should be.

Starting with **Mypy**, which is a static type checker for python code, that finds errors before they appear and sometimes this would even create a bigger problem so you can just stick with it only warning you about the things you want.

<br>
</br>

5. **Automate the Automation**

    To even make matters easier, we can spare ourselves from even initating **Mypy** or **Black**, by using tools.

Starting with **Pre-commit**, is a tool that executes checks before you commit code to your repository.