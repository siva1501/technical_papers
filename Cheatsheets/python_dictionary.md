# Python Dictionary Cheatsheet

A dictionary stores **key-value pairs**. It is mutable, ordered (Python 3.7+), and keys must be unique and hashable.

## Creating

```python
d = {"name": "Asha", "age": 25}
d = dict(name="Asha", age=25)
d = dict([("a", 1), ("b", 2)])
d = dict.fromkeys(["a", "b"], 0)     # {'a': 0, 'b': 0}
empty = {}
```

## Accessing

```python
d["name"]               # 'Asha' (KeyError if missing)
d.get("city")           # None (no error)
d.get("city", "N/A")    # 'N/A' (custom default)
```

## Adding & Updating

```python
d["city"] = "Mumbai"            # add or overwrite
d.update({"age": 26, "x": 1})   # merge multiple
d.setdefault("lang", "Python")  # set only if missing
```

## Removing

```python
d.pop("age")             # remove key, return value
d.pop("zzz", None)       # no error if missing
d.popitem()              # remove last inserted pair
del d["name"]            # delete key
d.clear()                # remove everything
```

## Common Methods

| Method | Description |
|--------|-------------|
| `d.keys()` | View of all keys |
| `d.values()` | View of all values |
| `d.items()` | View of `(key, value)` pairs |
| `d.get(k, default)` | Safe lookup |
| `d.update(other)` | Merge another dict |
| `d.pop(k)` | Remove and return value |
| `d.copy()` | Shallow copy |
| `d.setdefault(k, v)` | Get, or insert default |
| `len(d)` | Number of pairs |
| `k in d` | Membership test (keys) |

## Looping

```python
for key in d: ...
for value in d.values(): ...
for key, value in d.items():
    print(key, value)
```

## Dictionary Comprehension

```python
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

filtered = {k: v for k, v in d.items() if v > 1}
inverted = {v: k for k, v in d.items()}
```

## Merging (Python 3.9+)

```python
a = {"x": 1}
b = {"y": 2}
c = a | b          # {'x': 1, 'y': 2}
a |= b             # update in place
c = {**a, **b}     # works in older versions too
```

## Nested Dictionaries

```python
user = {"name": "Asha", "address": {"city": "Mumbai", "pin": 400001}}
user["address"]["city"]      # 'Mumbai'
```

## Useful Patterns

```python
# Count items
from collections import Counter, defaultdict
Counter("banana")            # Counter({'a': 3, 'n': 2, 'b': 1})

# Group items (auto-creates list)
groups = defaultdict(list)
groups["fruits"].append("apple")

# Sort by value
sorted(d.items(), key=lambda kv: kv[1])

# Safe check then use
if "name" in d:
    print(d["name"])
```

## Tips
- Keys must be **immutable** (str, int, tuple), not lists or dicts.
- `d.copy()` is a **shallow** copy; use `copy.deepcopy(d)` for nested data.
- Don't modify a dict's size while iterating over it; iterate over `list(d)` instead.
