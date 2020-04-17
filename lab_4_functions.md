# Python Lab 4: Putting the FUN in FUNctions

Functions are a way of organizing code so that it can be used multiple times within a program.

Let's take a look at what a function definition looks like:

```python
def add_two_numbers(x, y):
    sum = x + y
    return sum
```

If you placed the above code in your file, it will define a function called `add_two_numbers()` that you could use in the rest of your code. Just like when we define a variable by saying `x = 7` and then we can use that variable in the rest of our file, the same works for functions just instead of an `=` we use the `def` keyword seen above.

Let's break down the parts of the above function line-by-line to see what is going on:

```python
(1) def add_two_numbers(x, y):
(2)     sum = x + y
(3)     return sum
```

On line 1 we have the keyword `def` establishing that we are defining a function. Afterwards comes the name of our function `add_two_numbers`, and then immediately following the name of our function we have a set of parenthesis. Inside these parentheses are the arguments that our function takes.

This function takes two arguments and it calls them `x` and `y`. So when we call this function, we need to give it two values, one for `x` and one for `y`. When writing a function, you can specify it to take any number of arguments you want, even no arguments. But try not to get out of control and have your function take 20 arguments, as your code will look gross, and the Ghost of Ugly Code will haunt your dreams.

After the arguments on line 1, we have a colon `:` , this starts the body of the function.

On line (2), we have the start of the function's body, which will be indented. All the indented lines after the function definition are part of the function, up until there is something written on a line that is not indented (just like with IF/ELSE statements and loops).

On line (3), we have a `return` statement. A function doesn't have to return anything, sometimes we just want the code inside the function to run, but in this case, we want the function to compute something and return to us a value.

When I want to call the function `add_two_numbers()`, all I need to do is use the functions name and give it two values, and I will set a variable equal to whatever it returns, like so:

```python
def add_two_numbers(x, y):
    sum = x + y
    return sum

my_num = add_two_numbers(4, 5)

print(my_num)
```

The above code will print give the output:

```
$ 9
```

---

## <u>Scope</u>

In the body of the function, we only have access to variables passed into the function(`x` and `y`) as well as any variables that are defined globally in our program, meaning they are no inside any function (**it is not good practice to have global variables**). If there is a global variable named `x` and then we have a function that takes an argument that it calls `x`, the inside the function, the variable `x` from the function's argument will take precedence over the global variable. For example, look at the following code:

```python
name = "billy"

def greet_person(name):
    greeting = "Hello " + name + "!"
    print(greeting)


greet_person("Zach")
```

The above code will have the following output:

```
$ Hello Zach!
```

We refer to variable `name` at the top of the file as having a "global scope" as it is available globally throughout the file. Variables defined within a function are only able to be used inside that function, and so their scope is only of that function. If you try to refer to a variable outside of its scope, you will get an error saying that the variable has not been defined. Take a look at the following code:

```python
(1) def greet_person(name):
(2)   greeting = "Hello " + name + "!"
(3)    print(greeting)
(4)
(5) print(greeting)
```

The above code will return an error when you try to run it, since on line 5 we try to print the variable `greeting` but it is not defined within the scope in which we are trying to reference it. We are trying to reference it in the global scope, but it is only defined within the `greet_person()` function.

The function `greet_person()` is also an example of a function that doesn't return anything, since there is no return statement, and we just want the code inside the function to run.

---

As you can see, function definitions don't require you to specify the types of the variables you need to pass to them, which is a popular complaint people have about Python. Two ways of fixing this are by adding "Type Hints" and by adding a "docstring" at the top of the function describing what the function does and what the types of the arguments it takes are, and what the function will return.

#### <u>Function Docstrings</u>

Here is an example of how to write function docstring, which is done slightly differently from regular comments, since we will use a **triple-quoted string**, which will allow our docstring to go on multiple lines. It is good practice to never use triple-quoted strings for anything else besides function docstrings like this:

```python
def add_two_numbers(x, y):
    """add_two_numbers takes two numbers and returns their sum
    Args:
        x (int) - the first integer to add
        y (int) - the second integer to add
    Returns:
        sum (int) - the combined value of x and y
    """
    sum = x + y
    return sum
```

This kind of verbose commenting is not necessary but can be helpful, especially when multiple people are going to be working on the same code. At the very least, give your function a descriptive name and make sure it is clear what the types of the arguments are, either through a comment or type hints, or preferably both.

#### <u>Type Hints</u>

Here is an example of using Type Hinting on our `add_two_numbers()` function:

```python
(1) def add_two_numbers(x: int, y: int) -> int:
(2)     sum = x + y
(3)     return sum
```

Next to each of the arguments, I add a colon, a space, and the type that the argument needs to be. Then before I go to the next line, I write an arrow (`->`) and then the type of the value that the function returns, and then the colon to go into the function body.

---

We place code into functions for various reasons including:

- to break up the logic of our program into smaller, more understandable chunks that are easier to reason about and debug
- to avoid having to write code to do the same thing multiple times in our program, and instead write it once and call that function whenever we need to

Try to keep your functions small if you can. A good rule of thumb to try to stick by is to have your functions be less than 50 lines long. Try to have each line in your file also not be more than 100 characters wide. This will make your code much easier to read and debug too.

From here on out, try to get used to writing your Python programs with all your code inside of functions. and the code you wish to run first should be put inside of a block like this:

```python
def greet_the_world():
    print("Hello World!")

if __name__ == "__main__":
    greet_the_world()
```

This way we can avoid having any code in the global scope, which is what we want. When you place the above code in a file and run it, the code inside the `if __name__ == "__main__":` block will run first, which in this case calles the function `greet_the_world()`.

The reason this works is because when you run a python file, certain variables are already defined behind the scenes, one of them being `__name__`, and when you run a file, that file is the main file, so the `__name__` variable is set to `"__main__"` by the python interpreter.

If you were ever to want to import one of the functions from this file into another file, everything in the global scope would be run automatically, but the code inside this IF statement wouldn't since, this file would not be the main file, it would just be a file we are importing code from.

---

## Task: Add a Function To Your Adventure Game

The task is to add a function to your adventure game that checks to make sure the user input an acceptable response.

Here I have written the beginning to a game where I ask the user for their name, and ensure that they enter a name that is not empty. Then I ask them if they want to go through a door, and I make sure they enter a valid response before moving on in the story. The code to get the valid response still needs to be written.

```python

def get_valid_name() -> str:
    """get_valid_name asks the user for their name until the provide a name that is not empty
    Returns:
        The users name as a string
    """
    name = input("What is your name? ")
    while name == "":
        print("Please input a valid name!")
        name = input("What is your name? ")
    return name


def ask_question(question: str) -> bool:
    """ask_question asks the user a yes or no question and repeats the question until they input
        'yes' or 'no' for their response
    Args:
        question (str) - question to ask the user
    Returns:
        A boolean value (True or False), True if the response was a 'yes' and False if 'no'
    """
    # TODO: write the rest of this function



def start_game():
    name = get_valid_name()
    print("Welcome " + name + "!")

    if ask_question("There is a door in front of you, open it? (y/n)"):
        print("You went through the door!")
    else:
        print("You stayed in the room and starved.")


if __name__ == "__main__":
    start_game()
```

The way you should read the above code is by doing the following:

1. Look to see if there is anything important done in the global scope, in this case we have a few functions defined globally.
2. Look for the `if __name__ == "__main__":` block and read the code inside there. The code inside there is what will run after any global code before it is run. In this block we call the function `start_game()` so let's look there next.
3. Inside `start_game()`, the first thing we do is call the function `get_valid_name()` and set the variable `name` equal to the response of the function. So let's look at `get_valid_name()`.
4. Inside `get_valid_name()` we aske the user for their name until they enter a valid name, and then we return the name.
5. Now we are back inside the `start_game()` function. We greet the player, then we call the `ask_question()` function. This function returns a boolean value, so we use it as the clause of our IF statement.
6. We look inside the `ask_question()` function, as that will run and return a boolean back to whatever code called this function.
7. Now we are back in `start_game()` and if the `ask_question()` function returned `True`, then the IF block runs, and if the `ask_question()` function returns `False` then the ELSE block runs.

Your task is to complete the `ask_question` function and incorporate it into your game, or use the code I wrote above and just modify that.
