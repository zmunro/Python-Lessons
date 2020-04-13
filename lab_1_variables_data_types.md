# Python Lab 1: Variables, Data Types and Data Structures

Variables in Python are similar to variables in math class, they are just a symbol/word that represents a value that you assign to it.

You assign a value to a variable using the **"="** operator.

For example:

```python
big_number = 500
x = 12
my_first_name = "zach"
```

### <u>Variable Naming Rules</u>

- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and \_ )
- Variable names are case-sensitive (age, Age and AGE are three different variables)

In Python, it is good practice to name variables with **all lowercase letters**, and separate words with underscores. For example:

BAD:

```python
myFirstName = "bill"
```

GOOD:

```python
my_first_name = "bill"`
```

### <u>Variable Types</u>

There are many types of variables in Python, but a few of these types are similar across
most programming languages and they will be the ones we focus on today:

- strings
- booleans
- integers
- floats
- Lists
- Tuples
- Sets
- Dictionaries

Python data types are (for the most part) implied:

- if I write `x=7` then the type of `x` will be `int` (integer)
- if I write `y="7"` then the type of `y` will be `str` (string)

---

There are four Primitive Data Types:

#### <u>Strings</u>

- a set of characters, like a word or sentence, surrounded by either `"` or `'`
- e.g. `"bob"`, `"seven"`, `'social distancing'`
- endless possibilities, hours of fun

#### <u>Booleans</u>

- `True` and `False`
- first letter **must** be capitalized

#### <u>Integers</u>

- any integer, so whole numbers between negative infinity and positive infinity
- e.g. `-542`, `0`, `420`

#### <u>Floats</u>

- also known as "floating point numbers"
- name comes from the fact that there is a decimal point "floating" somewhere in the number
- e.g. `3.14`, `62.445`

---

### <u>Side Note:</u> Comments

In Python code, like in other languages, we have lines that are code, and lines that are **comments**.

Comments are where you can write notes/comments in your file to tell yourself, or whoever else is reading the code, what is going. Whatever you write in a comment will not be run as code, anything can go in a comment.

We start single-line comments with a `#` like so:

```python
# this is a comment
```

---

## We can do some basic operations with primitive data types:

Math is what you would expect:

```python
1 + 1   # => 2
8 - 1   # => 7
10 * 2  # => 20
35 / 5  # => 7.0
```

Integer division is done with `//`, and rounds down for both positive and negative numbers:

```python
5 // 3       # => 1
-5 // 3      # => -2
5.0 // 3.0   # => 1.0 # works on floats too
-5.0 // 3.0  # => -2.0
```

The result of division is always a float:

```python
10.0 / 3  # => 3.3333333333333335
```

The modulo operation takes the remainder after division:

```python
7 % 3  # => 1
6 % 2  # => 0
10 % 4 # => 2
```

Exponentiation (x<sup>y</sup>, x to the yth power):

```python
2**3  # => 8
```

Enforce precedence with parentheses:

```python
1 + 3 * 2  # => 7
(1 + 3) * 2  # => 8
```

Negate booleans with `not`:

```python
not True   # => False
not False  # => True
```

---

## Collections

Collections are our way of organizing data. There are many different ways to organize data but, a few ways are built in to the very heart of Python. Something to note about collections is that most of them are **mutable** (think "mutate"), meaning they can change once created. This is different from strings, integers, floats, and booleans. i.e.

- `4` will always represent the integer value four.
- `True` will always be the boolean value that is true.
- etc.

The collections we will look at are:

#### <u>Lists</u>

- an ordered collection of values of any type (sometimes referred to as arrays)
- mutable, so they can be altered once created
- lists are denoted by `[` square brackets `]` on either side of them, elements of lists are separated by commas
  ```python
  [1, 2, 3, 4]
  ["a", "b", "c", "d"]
  [1, "a", 2, "b", 3, "c"]
  [True, False, True, True, False, "7"]
  ```
- Data inside a list is accessible via **indexing**. This is when we specify the location/index of the position in the list we are interested in, and place it inside of square brackets like so:
  ```python
  my_list = [1, 2, 3, 4]
  my_list[0] # => 1
  ```
- Since lists are mutable we can append to them too:
  ```python
  short_list = ['a', 'b', 'c']
  short_list.append('d')
  # short list is now ['a', 'b', 'c', 'd']
  ```

### **IMPORTANT NOTE**: lists start at index `0`, as do all ordered things

#### <u>Tuples</u>

- **Immutable** ordered collection of values of any type
- Can be indexed the same way lists can
- Can be useful for when you know how long your set of data will be and you know it wont get bigger or smaller, but lists are usually preferable
- Tuples are denoted by being surrounded by parentheses:
  ```python
  (4, 5, 6)
  ```

#### <u>Sets</u>

- a mutable, unordered collection of unique items
- Since there is no ordering, they cannot be indexed, but we can still ask if an element is in a set
- Sets are denoted by being surrounded by `{` curly brackets `}`:
  ```python
  {1, 2, 3}
  2 in {1, 2, 3} # => True
  ```

#### <u>Dictionaries</u>

- Very similar to dictionaries in real life, where you have **keys** (words) and **values** (definitions). That is why they are often called key-value stores. You can think of dictionaries as being a collection of things and their definitions, or keys and their associated value.
- The keys in a dictionary must be unique, but multiple keys can have the same value.
- Dictionaries are mutable, so you can add things to dictionaries and take things out
- Values in a dictionary can be any data type or collection, but keys have to be an immutable type
- Dictionaries are denoted by the syntax `{key: value}`, so curly brackets on the outside, and a colon `:` between each key and value, and each key value pair separated by a comma:

  ```python
  my_dictionary = {'a': 1, 'b': 2, 'c': 3}

  # or equivalently:

  my_dictionary = {
      'a': 1,
      'b': 2,
      'c': 3
  }
  ```

- We index dictionaries similarly to how we index lists; by putting the key in square brackets after the list:
  ```python
  my_dictionary['a'] # => 1
  ```

---

# Task

Create a dictionary where the keys are the names of the different types and the values are an example of that type.
I'll give you an example for one of the key-value pairs:

```python
foo = {"integer": 4}
```

NOTES:

- the number of elements in your tuple element needs to be at least 2
- the keys in your dictionary should be Strings of the following words exactly as they are
  typed here:
  - `integer`
  - `float`
  - `list`
  - `tuple`
  - `dictionary`
  - `set`
  - `boolean`
  - `string`

### How to get started:

- Go to https://repl.it/languages/python3
- Copy the code below into that page and modify the dictionary at the top where it says `my_dictionary =`
- Click "Run" in the top left of the screen, if your dictionary is correct then the text
  "Dictionary is valid!" should appear on the bottom of the screen

```python
my_dictionary = {
	"integer": 4,
}


def check_dict(answer_dict):
    verify_dict = {
        "integer": "<class 'int'>",
        "float": "<class 'float'>",
        "list": "<class 'list'>",
        "tuple": "<class 'tuple'>",
        "dictionary": "<class 'dict'>",
        "set": "<class 'set'>",
        "boolean": "<class 'bool'>",
        "string": "<class 'str'>"
    }
	if set(answer_dict.keys()) != set(verify_dict.keys()):
		print("Check your dictionary's keys, something doesn't look right")
		return
	dict_correct = True
	for key,value in answer_dict.items():
		if verify_dict[key] == str(type(value)):
			print(f"Provided {key} is valid...")
		else:
			dict_correct = False
			print(f"Provided {key} is not of type {key}...")
    if dict_correct:
		print("Dictionary is valid!")
    else:
        print("Provided dictionary is invalid. Try again.")

check_dict(my_dictionary)
```
