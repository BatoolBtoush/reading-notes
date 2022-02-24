# Linux Tutorial

<br>

## [The Command Line](#The-Command-Line)

<br>
CLI can be defined as: "Is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text." 

-Refrence : [Linux Tutorial - 1. The Command Line](https://ryanstutorials.net/linuxtutorial/commandline.php)

And by my own defintion, it's a useful tool to get you where you need to go without using GUI, as it also helps with executing various commands. Keeping in mind that the behaviour of the terminal I'll be writing CLI commands on is going to be goverened by something called (shell or bash).

This command is followed by arguments or options if it's the first CL argument, as in this example:
```
ls -l /home/batool
```
- where ls -> command 

*space to seperate*

- -l -> an option, which is the first command line argument and what it does is that it modifies the behaviour of the command

*space to seperate*

- /home/batool -> command line argument

^-^ To avoid repeating yourself and re-typing commands, the terminal stores your previous commands as to make it easier for you to reach them by using the up and down arrows. 

<br>
</br>


## [Basic Navigation](#Basic-Navigation)

<br>
This section deals with the most important concept which is how to move around the system, as we have to be in certain directories to perform a certain command, so firstly, we have to define where we are exactly or even how to get where we want.
<br>
</br>
And this is done by existent commands I'll list them down:

- **pwd:** *(Print Working Directory)* which does exactly as said, shows you where you're currently in
- **ls:** *(list)* which shows you the contents of the current directory you're in. And it can be written in multiple ways, in order to show more details about the contents; like how many there are, what type they are, owner of those files, and so on. Those commands are:


     - ```
       ls           
       ```

     - ```
       ls -l
       ```
    - ```
      ls -l /etc
      ```

- **cd:** *(change directory)* which moves me to another place that I have to type out using either, absolute or relative paths.
<br>
</br>

### ***Paths: Absolute and Relative***


A path is the way leading to the directory I want to go to, and it can be laid out in number of ways under 2 concepts: absolute paths and relative ones.

**Absolute path:** they begin with a slash (/) and I can reach this said path wherever I might be in the system, as it specifies a directory in relation with the root or home directory.

**Relative path:** they don't begin with slash, and I can't reach the exact location unless it has a relation with where I'm currently at.
<br>
</br>

More abbrevations that come in handy when referring to paths and they help to write the paths in lots of ways:
  - **(~)** : represents the home or root directory.
  - **(.)** : represents the current directory.
  - **(..)** : represents the parent directory.


### ***Shortcutes:***

I can use the Tab key to have the computer auto complete for me when typing out commands.
<br>
</br>

## [More About Files](#More-About-Files)
<br>

Starting with the big fact that is everything is a file at heart, and how we can obtain information about what type of file is my file or directory in my system is by using the command ```file``` followed by the path.

Keeping in mind important notations:
- Linux is case sensitive, so I have to write the file name exactly as it is named without changning the Capital letters to small ones and vice versa.

- some file names can be made up of more than one word, which means they have spaces in them, for example: *Fun Linux* is a directory aka file, and if I want to reach it I can't do the following as it would give me an error: "No such file or directory"
``` 
cd Fun Linux
```
So I have to use either of those 2 methods:
1. escape the space:
      ```
    cd Fun\ Linux
      ```
2. quotes "" :
      ```
    cd "Fun Linux"
      ```


One other thing is how to view the hidden files. 
It's by using the command ```ls -a```
And that the hidden files start with . at the begnning of their names.
<br>
</br>

## [Manual Pages](#Manual-Pages)
<br>

In order to not memorize everything by heart, there's a way to learn more about the type of wrok a command does and the kind of arguments they accept, and this way is Manual Pages.

How to reach them?
using this command:
```
man <command to look up>
```
As this will give the name to the specific command I want to learn more about, and the description to its job and what other ways I can use it in.
<br>
</br>


### ***Searching***
Sometimes I don't know the exact command layout but I know the job I want to get done, so I resolve to search for a particular keyword inside the manual page. This can be done by:
```
man -k <search term>
```

Now inside a given manual page, I can do some additional search for a certain term by using this:
```
/<term>
```
and after performing the search I can navigate through the results by typing ```n```

<br>
</br>


## [File Manipulation](#File-Manipulation)

### ***Making a Directory***
As the name suggests, instead of doing regular GUI I can use the terminal to create a folder aka directory, by typing this command:
```
mkdir [options] <Directory>
```

I can use ```-p``` with ```mkdir``` to create a parent directory that contains other things.

And I can use ```-v``` to show me what is exactly happening as I am creating this directory.
<br>
<br>

### ***Removing a Directory***
When removing a directory from the CLI I have to be extra careful as there is no going back.
```
rmdir [options] <Directory>
```
<br>

### ***Creating a Blank File***
Basically if we use ```touch``` with a file and that file happens to not exist, it will be automatically created for me.

```
touch [options] <filename>
```
<br>

### ***Copying a File or Directory***
Just like in GUI, I can create a copy of an already existing file, by typing out this command on the terminal:
```
cp [options] <source> <destination>
```
When we use cp the destination can be a path to either a file or directory. If it is to a file (such as examples 1, 3 and 4 above) then it will create a copy of the source but name the copy the filename specified in destination. If we provide a directory as the destination then it will copy the file into that directory and the copy will have the same name as the source.

*Taken from:* [File Manipulation!](https://ryanstutorials.net/linuxtutorial/filemanipulation.php)

But if I want to copy a whole directory, I have to use this command instead:
```
cp -r [options] <source> <destination>
``` 
Where -r stands for recursive, which means that this time I want to look at the directory and all the files it contains that I want to copy into another destination.

<br>

### ***Moving a File or Directory***

Same as the ```cp``` but one advantage, is that I can move directory without having to use ```-r```:
```
mv [options] <source> <destination>
```
<br>

### ***Removing a File (and non empty Directories)***
```
rm [options] <file>
```
With the above command, I can't remove non-empty directories but if I use ```-r``` I can remove them:
```
rm -r [options] <file>
```
<br>
<br>

**For extra care I can use ```i``` which gives me a prompt to confirm if I actaully want the changes to be made.**