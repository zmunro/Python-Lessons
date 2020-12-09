# Python Lab 2: Comparisons, Conditionals, and Loops

There are many times we want to compare two items when programming.
We may want to see:
- if one number is bigger than another
- if two numbers are equal to eachother
- if a statement is True/False
- etc.


There are several comparison operators, today we will look at:
-  <u>greater than</u>  \>
-  <u>less than</u>  <
-  <u>equal to</u> ==
-  <u>not equal to</u> !=


So if I type:
  ```python
    5 < 3
  ```
Python will evaluate this to `False`, since this statement is not logically correct. The statements `5 < 3` and `False`, are completely equivalent.

Similarly, the statement `5 == 5` is equivalent to `True`.
Pay carefuly attention to the use of the **double equal** sign here, that is the comparison operator to see if two values are equal. This is very different to the single equals sign, which assigns a value to a variable.

#### Try it for yourself
Everyone take a minute to compare a few things in your python interpreters. Try comparing:
- lists
- booleans
- sets
- integers
- tuples




## Conditional Logic

This is what controls the flow of your program. We use conditional logic, in conjunction with comparisons, to make our programs do different things.

The main conditional logic statement is the if/else statement, which looks like this:
```python
if 5 > 3:
  print("hello")
  x = 5
  print(x)
else:
  print("world")
```

There are a lot of things going on here so we are going to break it down.
First, I have the key word `if`, which is followed by some statement that either must evaluate to `True` or `False`. In this case that statement is `5 > 3`.
At the end of the first line, I have a colon (`:`), marking the end of this if-conditional line.

The next line of code is **indented**. In Python, this is what signifies that this next line of code is "inside" of the if-statement. All the code inside the if-statement will run if the logical statement after the `if` evaluates to `True`. If the logical statement after `if` evaluates to `False`, then the code inside the if-block is skipped, and the code inside the else-block is run instead.

You can put as many lines of code inside the if-blocks and else-blocks, as long as they are properly indented. If you put another if statement inside of the if-block, the things inside that if block will need to be indented again (and so on), for example:

```python
if 10 > 2:
  print("10 is greater than 2")
  if 10 == 5:
    print("10 is also greater than 5")
else:
  print("10 is not greater than 2")
```

We can use the `and` and `or` operators in conjunction with boolean values as well. You use these the same way you would use a `+` or a `-`.
```python
$ True and True
True

$ True and False
False

$ True or False
True

$ 5 > 7 or 7 > 5
True

$ 3 * 3 == 9 and 5 * 5 == 25
True
```

__Note__: the `$` are not important here. Then above code is meant to demonstrate what would happen if you were to run Python interactively on a command line with those commands. The command line begins with a `$`, and after you write your command and hit enter, the result appears on the following line.

If we have two conditions we want to ensure are `True` in order for code inside of an if-statement to run, we can use the `and` operator.

```python
if 5 > 2 and 10 > 5:
  print("10 is greater than 5 and 5 is greater than 2")
```

#### Try for yourself:

Everyone experiment real quick with writing an `if`/`else` statement. If it helps, you can add parentheses to aid in readability and order of operations, like this:
```python
if ((5 > 2) or (10 > 20)):
  print("Either 5 is greater than 2 or 10 is greater than 20")
```




## Loops:

Loops are what we use when we want to do something over and over again.
The most common type of loop is a `for` loop.
There are different ways to write a `for` loop, but the simplest way is to say:

```python
for x in some_group:
  # do something with x...
```
a real example might be:

```python
for num in [0, 1, 2, 3, 4, 5]:
  print(num)
```

In the above loop, it will run 6 times. Each time, x will take on a new value in the list, starting at 0 then going right until it gets to 5.


We can replace this list with a variable that is a list like so:
```python
my_list = [0, 1, 2, 3, 4, 5, 6]
for number in my_list:
  print(number)
```


## Tasks:
#### Part 1: Looping
Add up all the numbers between 1 and 1,000 using a for loop.

__Note__: to make a list of numbers from 1 to X, we can use the built-in function `range()`.
So `range(3)` is `[0, 1, 2]`




#### Part 2: FizzBuzz
For each number from 1 to 100, do the following:
  - if it is divisible by 3 (and not 5) print out "fizz"
  - if it is divisible by 5 (and not 3) print out "buzz"
  - if it is divisible by 3 and 5 print out "fizzbuzz"
  - if it is not divisible by 3 or 5, print the number

__Note__:
  - the modulo operator looks like this: `%`
    It is used to see what the remainder is when one number is divided by another.
```python
$ 12 % 5
2

$ 10 % 5
0

$ 10 % 3
1
```