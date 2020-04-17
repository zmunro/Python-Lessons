# Python Lab 4: Putting the FUN in FUNctions

Functions are a way of organizing code so that it can be used multiple times within a program. We use functions to break up our code into logical, easier to understand segments. The code inside of a function is executed whenever you call the function from somewhere in your code. Normally, we define functions at the top of our file, so that they are defined and available to be called before any other code in our file runs.

Function definitions in their most basic form look like this:

```python
def add_two_numbers(x, y):
    sum = x + y
    return sum
```

If you placed the above code in a file, it will define a function called `add_two_numbers()` that can be called any number of times throughout the rest of the file.

Similar to how when a variable is defined by saying `x = 7` and then that variable can be used/referenced in following code in a file, the same works for functions. The difference being that instead of using an `=` to assign a value to a variable we use the `def` keyword to give a name to a function.

---

## <u>Parts of a Function</u>

Let's break down the above function line-by-line to see what is going on.

```python
(1) def add_two_numbers(x, y):
(2)     sum = x + y
(3)     return sum
```

On **line 1** we have the keyword `def` establishing that we are defining a function. After that comes the name of our function `add_two_numbers`, and then immediately following the name of our function we have a set of parenthesis. Inside these parentheses are the arguments that our function takes.

This function takes two arguments and it calls them `x` and `y`. So when we call this function, we need to give it two values, one for `x` and one for `y`. When writing a function, you can specify it to take any number of arguments you want, even no arguments. But try not to get out of control and have your function take 20 arguments, as your code will look gross, and the Ghost of Ugly Code will haunt your dreams.

After the arguments on **line 1**, we have a colon `:` , this starts the body of the function.

On **line 2**, we have the start of the function's body, which will be indented. All the indented lines after the function definition are part of the function, up until there is something written on a line that is not indented (just like with IF/ELSE statements and loops).

On **line 3**, we have a `return` statement. A function doesn't have to return anything, sometimes we just want the code inside the function to run, but in this case, we want the function to compute something and return to us a value.

A function can have multiple `return` statements, but as soon as a return statement is reached, the function immediately ends and no further code in the function is executed. A quick example of a function that has multiple return statements is:

```python
def check_if_even(num):
    if num % 2 == 0:
        return True
    else:
        return False
```

We actually don't even need the `else` statement in the above function. The same function could be written as:

```python
def check_if_even(num):
    if num % 2 == 0:
        return True
    return False
```

If the IF statement is **false**, the code inside of the IF block will get skipped, and `return False` will be the next thing executed and after the function will immediately exit.

If the IF statement is **true**, then the code in the IF block will run, which is `return True`, and so the function will return the value `True` and then immediately exit.

---

## <u>Calling a Function</u>

When you want to call the function `add_two_numbers()`, all you need to do is use the function's name and give it all the arguments it needs, and I will set a variable equal to whatever it returns, like so:

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

In a function, you only have access to variables passed into the function, as well as any variables that are defined **globally** in your program, meaning they are defined outside of the functions (**it is not good practice to have global variables**). If there is a global variable called `name` and then we have a function that takes an argument that is called `name`, then when the function get's called, it is not clear which will be the value of `name` inside the function; will it be the value of the global variable called `name` or the value of whatever was passed to the function?

The answer is that the `name` variable from the function's argument will take precedence over the value of the global variable called `name`. This can get confusing, so it is a good idea to **NOT USE GLOBAL VARIABLES**. For an example of confusing usage of global variables, look at the following code:

```python
name = "billy"

def greet_person(name):
    greeting = "Hello " + name + "!"
    print(greeting)


greet_person("Zach")
```

You can see in the above code that we have a global variable called `name` that has the value `"billy"`. The function `greet_person()` takes one argument that it calls `name`. Inside the function `greet_person()` the `name` variable will refer to the value passed in as the argument to that function, NOT the global variable.
The above code will have the following output:

```
$ Hello Zach!
```

Let's look at another example of confusing global variable usage:

```python

generic_greeting = "Hello"

def greet_person(name):
    phrase = generic_greeting + " " + name + "!"
    print(phrase)


greet_person("Zach")
```

In the above code, we are able to reference the global variable `generic_greeting` inside of the `greet_person()` function, since the variable is defined globally. Again, **do not do this**, it is bad practice since it gets very confusing very quickly.

We refer to variable `generic_greeting` in the above code snippet as having a "**global scope**" as it is available globally throughout the file.

Variables defined within a function are only able to be used **inside that function**, so we say their scope is limited to that of the function they are defined inside of. If you try to refer to a variable outside of its scope, you will get an error saying that the variable has not been defined.

The following code is BAD and will return an error since it tries to refer to a variable outside of the scope in which it was defined:

```python
(1) def greet_person(name):
(2)     greeting = "Hello " + name + "!"
(3)     print(greeting)
(4)
(5) print(greeting)
```

The above code will return an error when you try to run it, since on line 5 we try to print the variable `greeting` but it is not defined within the scope in which we are trying to reference it. We are trying to reference it in the global scope, but it is only defined within the `greet_person()` function.

The function `greet_person()` is also an example of a function that doesn't return anything, so the function will finish when it gets to the end of the code inside of it. For this function, we don't need to have it return anything back, we just want the code inside the function to run and print a greeting.

---

As you may have noticed, function definitions don't require you to specify the type for each of the variables they require, which is a popular complaint people have with Python. Two ways of fixing this are by adding "Type Hints" and by adding a "docstring" at the top of the function describing what the function does and what the type of the arguments it takes is, and what the function will return. This won't stop people from passing in variables with the wrong type, but it will help prevent that situation from arising.

#### <u>Function Docstrings</u>

Here is an example of how to write function docstring, which is done slightly differently from regular comments, since it uses a **triple-quoted string**, which allows the docstring to go over multiple lines. It is good practice to never use triple-quoted strings for anything else besides function docstrings like this:

```python
def add_two_numbers(x, y):
    """add_two_numbers takes two numbers and returns their sum
    Args:
        x (int) - the first integer to add
        y (int) - the second integer to add
    Returns:
        (int) the combined value of x and y
    """
    sum = x + y
    return sum
```

This kind of verbose commenting is not strictly necessary but can be helpful, especially when multiple people are going to be working on the same code. At the very least, give each of your functions a descriptive name and make sure it is clear what the type of each of the arguments is, either through a comment or type hints, or preferably both.

#### <u>Type Hints</u>

Here is an example of using Type Hinting on our `add_two_numbers()` function:

```python
(1) def add_two_numbers(x: int, y: int) -> int:
(2)     sum = x + y
(3)     return sum
```

Next to each of the arguments, there is a colon, a space, and the type of that the argument needs to be. Then before the next line, an arrow (`->`) and then the type of the return value that the function produces, and lastly a colon before the start of the function body.

---

## <u>Usages</u>

We place code into functions for various reasons, such as to:

- break up the logic of our program into smaller, more understandable chunks that are easier to reason about and debug
- avoid having to write code that does the same thing multiple times in our program, and instead write it once and call that function whenever we need to

Try to keep your functions small if you can. A good rule of thumb is to have your functions be less than 50 lines long. Get used to always have each line in your file not be more than 100 characters wide. This will make your code much easier to read and debug.

From here on out, try to get used to writing your Python programs with all your code inside of functions. The code you wish to run first should be put inside of a block like this:

```python
if __name__ == "__main__":
    print("Hello World!")
```

This way we can avoid having any code in the global scope, which is what we want. When you place the above code in a file and run it, the code inside the `if __name__ == "__main__":` block will run first, which in this case prints the words `"Hello World!"`.

The reason this works is because when you run a python file, certain variables are already defined behind the scenes, one of them being `__name__`. So when you run a python file, that file can be thought of as the "main" file, so the `__name__` variable is set to `"__main__"` by the python interpreter.

If you were ever to want to import one of the functions from `file_A.py` into some other `file_B.py` so that you could use it there, everything in the global scope of `file_A.py` would be run automatically, but the code inside the `if __name__ == "__main__":` block wouldn't, since `file_A.py` would not be the main file, it would just be a file we are importing code from.

---

## Task: Add a Function To Your Adventure Game

The task is to add a function to your adventure game that checks to make sure the user input an acceptable response to each question.

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

Your task is to complete the `ask_question()` function and incorporate it into your game, or use the code I wrote above and just modify that.
