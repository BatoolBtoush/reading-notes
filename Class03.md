# Readings: FileIO & Exceptions

## ***Reading and Writing Files in Python***

A file is a set of bytes used to store data that is formatted in a specific way which will then be translated into binary 1 and 0 to be processed by the computer.


### **How to access a file?** 

To access any file I need to know the precis location of it and that can be granted by using what's called the **File Paths**, as it represents the exact location based on the current directory I'm in right now. And it's made up of three parts:

1. **Folder Path**: The location of the directory or the folder that holds the file.

2. **File Name**: The name of the file I want to access.

3. **Extension**: The file type indication which is represented by a . at the end of its name.


To access any file I need to write its location path depending on where I am, which means taking into account the directories that hold the files.

For example the path to this file "Class03.md" would be, if I wanted to access it from the "README.md" file in the root of this repo:
```
Class03.md
``` 
And that is because the two files are on the same level.

But if they were in different directories, I might have to move up to access the other file, and this can be done using special characters double-dot (..) to move one directory up. 


<br>

### **Opening and Closing a File in Python**

The next obvious thing to do with a file is open it to view its contents, and this is done by using the built-in method **input()** which takes more than one argument --> 

1. The first argument is the file path that I discussed above
2. The second argument is what mode I want when I open the file, and it can be (read, write ...), as in this table:


| Character | Meaning |
| ----------- | ----------- |
| 'r' | Open for reading (default)|
| 'w' | Open for writing, truncating (overwriting) the file first|
|'rb' or 'wb' | Open in binary mode (read/write using byte data)|

	
<br>


Now the thing that must always come after opening a file, is closing it as this is a very crucial part, and if it's not done could lead to errors.

The closing of a file is done using the built-in method **close()**, but in order to be extra careful and to always make sure to close the file after opening it no matter what, there are two possible ways to help with that:

1. Try Finally Block: as in this example, where I keep what I want done to the file after opening it in the **Try block**, and in the **Finally block** I keep the closing method which will be executed nevertheless.
```
reader = open('dog_breeds.txt')
try:
    # Further file processing goes here
finally:
    reader.close()
```

2. The with statement: which will do the same functionality of the Try and Finally block, but it's written in a clean code kind of way.
```
with open('dog_breeds.txt') as reader:
    # Further file processing goes here
```


<br>

### ***Reading and Writing Opened Files***

After opening the file comes the reading and writing of them, the kind of mode I want.


<br>

### **Reading a File**

Can be done using some methods as described below:

1. **.read(size=-1)** ---> This method read from the file based on the argument that's passed which represent the size, if I pass -1, None it will read the whole file.

2. **.readline(size=-1)** ---> This method reads the line based on the argument that's passed which represent the size, if I pass -1, None it will read the whole line.

3. **.readlines()** ---> This method reads the lines and returns them as a list.


<br>

### **Writing In a File**

Can be done using some methods as described below:

1. **.write(string)** ---> This methods writes the string to the file.

2. **.writelines(seq)** ---> This method writes the sequence to the file. 
 

<br>
<br>


## ***Python Exceptions***

The difference between a regular SyntaxError and a Python Exception, is:

**The SyntaxError** occurs when the parser runs into a statement that's written in a wrong way, and once it's fixed the error is gone.

**The Exception** occurs when a correctly written statement in our code returns an error, and the best part about the Exception in Python is that it describes the exact kind of error that has happened


<br>

### **Raising an Exception**

A certain exception or an error can be made if a condition is met by raising the exception using **raise**, just like it's shown below:

```
x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
```
And since the condition is satisfied the program will show the exception error with the special message 'x should not exceed 5. The value of x was'.


<br>

### **The AssertionError Exception**

In order to show an AssertionError, I would have to use the word assert as a way to make sure that a certain condition is met, if it's True then the program runs successfully, if not the exception is shown.


<br>

### **The try and except Block: Handling Exceptions**

Now when an exception occurs the program would halt, which is very inconvenient, that's why we have to handle the exception... Using Try and Except Block.

Where the Try would have a code that's going to be run, and the Except would handle the exception errors that might occur when running the code in the Try block.

In the code below, not only it handles the AssertionError and shows a specific message as it continues to work regularly, but it also show the kind of error that happened, and that is done by catching the error the code threw.

```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
    print('The linux_interaction() function was not executed')
```
