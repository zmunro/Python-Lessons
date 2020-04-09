# Lab 2: Writing Python Scripts and the Command Line

## <u> The Command Line </u>
The command line may look complex at first, but the basics of it are all you need to know and they are fairly intuitive.

The command line is simply a text based way of interacting with the file system on your computer. Any of the things that you do in your file explorer on your computer, you can do through the command line, such as:
- opening files
- running programs (like when you double click on your browser icon)
- making a folder
- moving file from one folder to another
- making new files
- changing the names of files
- etc.

The **Terminal** is the program from which you execute commands on the command line.

When you are on the command line, you can think of yourself as always being *somewhere* in the filesystem on your computer, which will be denoted on the left of the terminal. This is what appears when I open my terminal:
```
zach@zach-XPS-13-9380:~/Documents/python_lessons$
```
which stands for:
```
user @ name-of-computer: path to your current folder/directory
```

**Note**: The words "folder" and "directory" are synonymous \

### <u> Basic Commands </u>

The way we execute commands and navigate our file system is with some keywords:

- **command**: cd \
    **definition**: change directory, move from where you are to a different directory
    ```
    $ cd /home/zach/Documents
    $ cd ..
    $ cd ~
    ```
\
**Note**: I am using the `$` at the beginning of the above line just to denote that it is a command being typed on the command line. You don't need to type this. \
**Note**: `..` is the directory one level up from where you are\
**Note**: `~` is your home directory. On Mac this is `/Users/{your_username}/`



- **command**: cp \
    **definition**: copy, used to copy a file or a folder from one place to another
    ```
    $ cp my_file.txt /home/zach/Documents
    ```

- **command**: mv \
    **definition**: move, used to move a file or a folder from one place to another
    ```
    $ mv my_file.txt /home/zach/Documents
    ```

- **command**: rm \
    **definition**: remove/delete, used to delete a file (permanent, does not got to into trash)
    ```
    $ rm my_file.txt
    ```

- **command**: ls \
    **definition**: list directory, lists all the files in the current directory
    ```
    $ ls
    bioinfo_services  db      dzd2             personal        random
    bio_info_work     devops  minion_pipeline  prefect         website
    configuration     dzd     notes            python_lessons  weekly_notes
    ```

\
There are thousands of other commands that can be run on the command line. You don't have to become an expert at the command line, but you will need to be a little comfortable with it. Remember, **Google is your friend.**

As you gain experience, your will get a bit better at making fewer errors, but you will get **MUCH** better at finding and fixing your errors. The more mistakes you make, the more practice you get at debugging code, which is an incredibly useful skill.

---

## <u> How to Write a Python Script </u>

A Python Scrput has the `.py` extension

The programming language Python is what is known as an *interpreted language*. This means that in order to run our code, we need to use a *python interpreter*, this is a program that is able to interpret our code and convert it to instructions that our computer can understand.

In order to execute our code, we will run the python interpreter and pass to it our file with code in it. Which looks something like this:
```
$ python my_file.py
```

Python cares a lot about the whitespace in your files, that is what the interpreter uses to infer the logical flow of program. We saw this about when we were writing if-statements:
```
if x < 7:
    print("x is less than 7!")
else:
    print("x is not less than 7!")

print("hello")
```
In the above code, the first print statement, after our if-statement, is indented, signifying that it is inside the if-block.

The second print statement, after the else-statement, is also indented, signifying it is inside the else block.

The last print statement is **not indented at all**, so it is seperate from the if/else block.

---

## Example: Write and run a Python Script

To get started writing your first Python Script create a file with the `.py` extension. Let's call it `my_script.py` and let's place it on your desktop.
```
$ cd ~/Desktop
$ touch my_script.py
```
**Note**: the `touch` command will create an empty file with the given name.

Open this file in the text editor of your choice, I suggest using Sublime Text 3, which you can download here: https://www.sublimetext.com/3

Once you have Sublime open, open your file by going to File->Open File... in the top left of the window.

You can start writing code in your file. Python will interpret and run your code in sequential order from the top of your file to the bottom.

Start by writing the following on line 1 of your file:
```
print("hello world!")
```
Now save your file and go back to your terminal, and make sure you are in the same directory as your file, you can do this by running `ls` to list the files in your current directory. If you need to, you should use the `cd` command to switch directories so that you are in your Desktop directory.

Now, run your program by typing:
```
python3 my_script.py
```
**Note**: you may need to substitute `python3` for just `python` depending on how you installed it.


Task: Write a choose your own adventure game in your script with at least 3 steps
**Note**: to get input from the user use the input() function like so

```
name = input("What is your name: ")
```

This will then display on the command line, when you run your program:

```
What is your name:
```

Task 2: Practice Problems on https://codingbat.com/python