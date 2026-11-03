# Python PEP 8 Cheatsheet

PEP 8 is the official style guide for Python code. Consistent style makes code easier to read and maintain.

## Indentation & Line Length
- Use **4 spaces** per indent level (never mix tabs and spaces).
- Limit lines to **79 characters** (72 for comments/docstrings).
- Break long lines inside parentheses, brackets, or braces.

```python
# Good
result = some_function(argument_one, argument_two,
                       argument_three)

# Good: hanging indent
result = some_function(
    argument_one,
    argument_two,
)
```

## Blank Lines
- **2 blank lines** around top-level functions and classes.
- **1 blank line** between methods inside a class.

## Imports
- Put imports at the top of the file, one per line.
- Order: **standard library → third-party → local**, with a blank line between groups.
- Avoid wildcard imports (`from x import *`).

```python
import os
import sys

import requests

from mypackage import mymodule
```

## Naming Conventions

| Type | Convention | Example |
|------|-----------|---------|
| Variable / function | `snake_case` | `user_name`, `get_data()` |
| Class | `PascalCase` | `UserProfile` |
| Constant | `UPPER_SNAKE_CASE` | `MAX_RETRIES` |
| Module / package | `lowercase` (short) | `utils`, `mypackage` |
| Private / internal | leading underscore | `_internal_var` |
| Name-mangled | double underscore | `__secret` |

## Whitespace

```python
# Good
x = 1
spam(ham[1], {eggs: 2})
def func(a, b=0): ...

# Bad
x=1
spam( ham[ 1 ], { eggs: 2 } )
def func(a, b = 0): ...
```

- No space before a comma, colon, or semicolon.
- No space just inside brackets.
- One space around operators and after commas.
- No spaces around `=` for keyword arguments or defaults.

## Comments & Docstrings
- Comments should explain **why**, not **what**.
- Use `# ` (hash + one space) for inline comments, with at least 2 spaces before them.
- Write docstrings for all public modules, functions, classes, and methods.

```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b
```

## Programming Recommendations
- Compare to `None` with `is` / `is not`, not `==`.
- Use `if x:` instead of `if x == True:` or `if len(x) > 0:`.
- Use `isinstance()` instead of comparing `type()` directly.
- Prefer `def` over assigning a `lambda` to a name.
- Catch specific exceptions; avoid bare `except:`.

```python
# Good
if value is None: ...
if my_list: ...

# Bad
if value == None: ...
if len(my_list) > 0: ...
```

## Tools
| Tool | Purpose |
|------|---------|
| `flake8` | Check style and errors |
| `pycodestyle` | Check PEP 8 compliance |
| `black` | Auto-format code |
| `isort` | Sort imports |
| `ruff` | Fast linter and formatter |
