# Python General Cheatsheet

A practical reference for Python syntax, built-in data structures,
functions, files, and project setup.

## Running Python

``` bash
python --version
python app.py
```

## Variables and data types

``` python
name = "Siva"       # str
age = 25            # int
height = 5.8        # float
is_learning = True  # bool
nothing = None      # NoneType

print(type(age))
```

Python is dynamically typed: a variable can refer to values of different
types.

## Comments and output

``` python
# This is a comment
print("Hello, Python")
print("Age:", 25)
```

Use docstrings to describe functions, classes, and modules.

## Type conversion

``` python
int("25")       # 25
float("3.5")    # 3.5
str(100)        # "100"
list("cat")     # ['c', 'a', 't']
tuple([1, 2])   # (1, 2)
```

Invalid conversions can raise `ValueError`.

## Operators

  Category     Operators
  ------------ -------------------
  Arithmetic   `+ - * / // % **`
  Comparison   `== != > < >= <=`
  Logical      `and or not`
  Assignment   `= += -= *=`
  Membership   `in`, `not in`
  Identity     `is`, `is not`

``` python
print(10 / 3)   # 3.333...
print(10 // 3)  # 3
print(10 % 3)   # 1
print(2 ** 3)   # 8
```

Use `==` to compare values. Use `is` mainly for object identity, such as
`value is None`.

## Conditional statements

``` python
marks = 75

if marks >= 90:
    print("Excellent")
elif marks >= 50:
    print("Pass")
else:
    print("Fail")
```

Python uses indentation to define blocks. Four spaces is the common
convention.

## Loops

``` python
for number in range(1, 4):
    print(number)

count = 1
while count <= 3:
    print(count)
    count += 1
```

-   `break` exits the nearest loop.
-   `continue` skips to the next iteration.
-   `pass` is a placeholder.

## Strings

Strings are immutable sequences of characters.

``` python
text = "Python Programming"

text[0]                 # 'P'
text[-1]                # 'g'
text[0:6]               # 'Python'
text.lower()
text.upper()
text.strip()
text.replace("Python", "Java")
text.find("Program")
text.count("m")
text.startswith("Python")
text.endswith("ing")
text[::-1]              # Reverse
```

Formatted strings:

``` python
name = "Siva"
age = 25
print(f"My name is {name} and I am {age}.")
```

## Lists

Lists are ordered and mutable. They allow duplicates.

``` python
numbers = [10, 20, 30, 20]
numbers.append(40)
numbers.insert(1, 15)
numbers.remove(20)      # First matching value
last = numbers.pop()    # Remove and return last item
numbers.sort()
numbers.reverse()
```

`len(items)` returns length; `items[index]` accesses an item;
`items[start:end]` creates a slice.

## Tuples

Tuples are ordered and immutable.

``` python
point = (10, 20)
print(point[0])
x, y = point
single_item = (5,)
```

## Sets

Sets store unique elements and do not support positional indexing.

``` python
values = {1, 2, 2, 3}
values.add(4)
values.discard(2)

a = {1, 2, 3}
b = {3, 4, 5}
print(a | b)  # Union
print(a & b)  # Intersection
print(a - b)  # Difference
print(a ^ b)  # Symmetric difference
```

An empty set is `set()`. `{}` creates an empty dictionary.

## Dictionaries

Dictionaries store key-value pairs. Keys must be hashable and unique.

``` python
student = {"name": "Siva", "age": 25}
print(student["name"])
student["age"] = 26
student["city"] = "Hyderabad"
student.pop("city")

student.keys()
student.values()
student.items()
student.get("course", "Unknown")
```

Loop through key-value pairs:

``` python
for key, value in student.items():
    print(key, value)
```

## Functions

``` python
def add(first, second):
    return first + second

result = add(10, 20)
print(result)  # 30
```

Parameters receive values; `return` sends a result to the caller.
`print()` displays a value but does not return it as the function
result.

Default and keyword arguments:

``` python
def greet(name, message="Hello"):
    return f"{message}, {name}"

print(greet("Siva"))
print(greet(name="Siva", message="Welcome"))
```

## Scope

-   Local variable: created inside a function.
-   Global variable: defined at module level.
-   Prefer passing values into functions and returning results instead
    of relying on global state.

## Comprehensions

``` python
squares = [number * number for number in range(1, 5)]
evens = [number for number in range(10) if number % 2 == 0]
square_map = {number: number * number for number in range(1, 4)}
unique_lengths = {len(word) for word in ["cat", "dog", "apple"]}
```

## Lambda functions

A lambda is a small anonymous function containing one expression.

``` python
double = lambda number: number * 2
print(double(5))  # 10
```

Use `def` for more complex reusable logic.

## Exception handling

``` python
try:
    number = int(input("Enter a number: "))
    print(100 / number)
except ValueError:
    print("Enter a valid integer.")
except ZeroDivisionError:
    print("The number cannot be zero.")
finally:
    print("Program finished.")
```

Use `raise` to signal an error deliberately.

## File handling

``` python
with open("notes.txt", "r", encoding="utf-8") as file:
    content = file.read()

with open("notes.txt", "w", encoding="utf-8") as file:
    file.write("Python notes")

with open("notes.txt", "a", encoding="utf-8") as file:
    file.write("\\nMore notes")
```

Modes: `r` read, `w` write/replace, `a` append, `x` create new file.
`with` closes the file automatically.

## CSV files

``` python
import csv

with open("students.csv", "r", newline="", encoding="utf-8") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row["name"], row["age"])
```

`DictReader` uses the header row as dictionary keys.

## Modules and packages

``` python
import math
print(math.sqrt(25))

from pathlib import Path
print(Path("notes.txt").exists())
```

A module is a Python file. A package groups modules, commonly in a
directory.

``` python
def main():
    print("Application started")

if __name__ == "__main__":
    main()
```

This entry-point condition runs `main()` when the file is executed
directly, not when imported.

## Object-oriented programming

``` python
class Student:
    def __init__(self, name):
        self.name = name

    def introduce(self):
        return f"My name is {self.name}"

student = Student("Siva")
print(student.introduce())
```

-   Class: blueprint for objects.
-   Object: instance of a class.
-   `self`: current instance.
-   `__init__`: initializes an instance.
-   Inheritance: reuse or extend another class.
-   Encapsulation: organize data and behavior together.
-   Polymorphism: different types respond to the same operation in their
    own way.

## Iterables and iterators

``` python
numbers = [10, 20, 30]
iterator = iter(numbers)

print(next(iterator))  # 10
print(next(iterator))  # 20
```

A `for` loop obtains values from an iterator automatically.

## Virtual environments on Linux

``` bash
python -m venv .venv
source .venv/bin/activate
deactivate
```

A virtual environment keeps one project's installed packages separate
from other projects.

## pip and uv

``` bash
python -m pip install requests
python -m pip list
python -m pip freeze > requirements.txt
python -m pip install -r requirements.txt
```

Using uv:

``` bash
uv venv
source .venv/bin/activate
uv pip install requests
uv pip freeze > requirements.txt
uv pip install -r requirements.txt
```

## Testing with unittest

``` python
import unittest

def add(a, b):
    return a + b

class TestAdd(unittest.TestCase):
    def test_adds_two_numbers(self):
        self.assertEqual(add(2, 3), 5)

if __name__ == "__main__":
    unittest.main()
```

Common assertions: `assertEqual`, `assertTrue`, `assertFalse`,
`assertIn`, and `assertRaises`.

## Useful built-in functions

  Function                        Purpose
  ------------------------------- -------------------------------------
  `len(value)`                    Number of items
  `type(value)`                   Object type
  `range(...)`                    Integer sequence
  `sum(values)`                   Sum
  `min(values)` / `max(values)`   Smallest / largest
  `sorted(values)`                New sorted list
  `abs(number)`                   Absolute value
  `round(number, digits)`         Round a number
  `any(values)`                   True if at least one item is truthy
  `all(values)`                   True if all items are truthy
  `zip(a, b)`                     Combine corresponding items
  `enumerate(values)`             Produce index-value pairs

## Big-O quick reference

  Operation                             Typical time
  ----------------------------------- --------------
  List indexing                                 O(1)
  List append (amortized)                       O(1)
  List search                                   O(n)
  Insert/delete near list beginning             O(n)
  Dictionary lookup (average)                   O(1)
  Set membership (average)                      O(1)
  Sorting                                 O(n log n)

## Common mistakes

-   Use `==` for value comparison, not `=`.
-   Use `set()` for an empty set; `{}` is an empty dictionary.
-   Remember that strings and tuples are immutable.
-   Use `return` when a function must send a result back.
-   Prefer `with open(...)` for file handling.
-   Remember that opening a file with `w` replaces its existing content.
