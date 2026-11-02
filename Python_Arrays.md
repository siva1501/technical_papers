# Python Arrays Cheatsheet

A practical reference for Python list operations and common array
problem-solving patterns.

## What is an array?

An array stores multiple values in an ordered sequence. Python lists are
commonly used as dynamic arrays in coding problems.

``` python
numbers = [10, 20, 30, 40]
```

## Creating lists

``` python
numbers = [1, 2, 3, 4]
empty = []
zeros = [0] * 5
letters = list("code")
```

## Indexing

Python uses zero-based indexing.

``` python
numbers = [10, 20, 30, 40]
print(numbers[0])   # 10
print(numbers[2])   # 30
print(numbers[-1])  # 40
```

For a list of length `n`, valid positive indexes are `0` through
`n - 1`.

## Slicing

Form: `items[start:stop:step]`. The stop index is excluded.

``` python
numbers = [10, 20, 30, 40, 50]
print(numbers[1:4])   # [20, 30, 40]
print(numbers[:3])    # [10, 20, 30]
print(numbers[2:])    # [30, 40, 50]
print(numbers[::-1])  # [50, 40, 30, 20, 10]
```

A slice creates a new list (a shallow copy).

## Traversal

By value:

``` python
for number in numbers:
    print(number)
```

By index:

``` python
for index in range(len(numbers)):
    print(index, numbers[index])
```

Use index-based traversal when positions or neighboring elements matter.

## Update, insert, and delete

``` python
numbers[1] = 99
numbers.append(60)
numbers.insert(1, 15)
numbers.remove(30)   # First matching value
last = numbers.pop()
del numbers[0]
```

Append is O(1) amortized. Insert/delete near the beginning is O(n),
because elements shift.

## Searching

Linear search works on sorted and unsorted lists:

``` python
numbers = [4, 8, 2, 9]
target = 2
found_index = -1

for index in range(len(numbers)):
    if numbers[index] == target:
        found_index = index
        break

print(found_index)  # 2
```

Time: O(n). List membership (`target in numbers`) is also O(n) in the
worst case.

## Minimum, maximum, and sum

``` python
numbers = [5, 2, 9, 1]
print(min(numbers))  # 1
print(max(numbers))  # 9
print(sum(numbers))  # 17
```

Each visits the elements: O(n).

Manual largest-value pattern:

``` python
largest = numbers[0]

for number in numbers:
    if number > largest:
        largest = number
```

## Reversing an array

``` python
numbers.reverse()        # Changes original list
reversed_numbers = numbers[::-1]  # Creates a new list
```

Two pointers, in place:

``` python
left = 0
right = len(numbers) - 1

while left < right:
    numbers[left], numbers[right] = numbers[right], numbers[left]
    left += 1
    right -= 1
```

Time: O(n). Extra space: O(1).

## Sorting

``` python
numbers.sort()                  # Sort original list
sorted_numbers = sorted(numbers)  # Return a new list
numbers.sort(reverse=True)      # Descending
```

Typical time: O(n log n).

## Removing duplicates

If order does not matter:

``` python
unique_numbers = list(set([1, 2, 2, 3, 1]))
```

To preserve first-seen order without a set:

``` python
numbers = [1, 2, 2, 3, 1]
unique_numbers = []

for number in numbers:
    if number not in unique_numbers:
        unique_numbers.append(number)
```

The no-set version can take O(n²), because list membership is O(n). A
set-based tracking approach is typically O(n) average time.

## Frequency counting with a dictionary

``` python
numbers = [1, 2, 2, 3, 1, 2]
frequency = {}

for number in numbers:
    if number in frequency:
        frequency[number] += 1
    else:
        frequency[number] = 1

print(frequency)  # {1: 2, 2: 3, 3: 1}
```

Average time: O(n). Useful for counting, duplicate detection, and
frequency comparison.

## Two Pointers

Use two indexes, often moving from opposite ends or at different speeds.

Common uses: - Reverse an array. - Check a palindrome. - Find a pair in
a sorted array. - Remove duplicates from a sorted array. - Partition
values.

Pair sum in a sorted array:

``` python
numbers = [1, 2, 4, 6, 8]
target = 10
left = 0
right = len(numbers) - 1

while left < right:
    current_sum = numbers[left] + numbers[right]

    if current_sum == target:
        print(numbers[left], numbers[right])
        break
    elif current_sum < target:
        left += 1
    else:
        right -= 1
```

Time: O(n). This decision rule requires sorted input.

## Sliding Window

Use a window to process a contiguous section.

Fixed-size example: maximum sum of `k` consecutive values.

``` python
numbers = [2, 1, 5, 1, 3, 2]
k = 3

window_sum = 0
for index in range(k):
    window_sum += numbers[index]

max_sum = window_sum

for right in range(k, len(numbers)):
    window_sum += numbers[right]
    window_sum -= numbers[right - k]

    if window_sum > max_sum:
        max_sum = window_sum

print(max_sum)  # 9
```

Time: O(n). Add the entering value and subtract the leaving value
instead of recalculating the whole window.

Variable-size windows are useful for longest or shortest contiguous
sections. The expand/shrink condition depends on the problem.

## Prefix Sum

Prefix sums store cumulative totals.

``` python
numbers = [2, 4, 6, 8]
prefix = [0]

for number in numbers:
    prefix.append(prefix[-1] + number)

print(prefix)  # [0, 2, 6, 12, 20]
```

Inclusive range sum from `left` to `right`:

``` python
range_sum = prefix[right + 1] - prefix[left]
```

Build time: O(n). Each range query: O(1).

## Hashing with arrays

A dictionary or set can avoid repeated scanning.

Two Sum idea: 1. Visit each number once. 2. Calculate `target - number`.
3. Check whether that partner was seen earlier. 4. If yes, return the
matching indexes. 5. Otherwise, store the current number and index.

Average time: O(n), extra space: O(n).

## Maximum Subarray --- Kadane's Algorithm

Find the maximum sum of a non-empty contiguous subarray.

``` python
numbers = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
current_sum = numbers[0]
best_sum = numbers[0]

for index in range(1, len(numbers)):
    if current_sum + numbers[index] < numbers[index]:
        current_sum = numbers[index]
    else:
        current_sum += numbers[index]

    if current_sum > best_sum:
        best_sum = current_sum

print(best_sum)  # 6
```

Time: O(n). Extra space: O(1). Starting with the first element handles
all-negative arrays.

## Binary Search

Binary search works on sorted data and halves the search range each
step.

``` python
numbers = [2, 4, 6, 8, 10, 12]
target = 8
left = 0
right = len(numbers) - 1
answer = -1

while left <= right:
    middle = (left + right) // 2

    if numbers[middle] == target:
        answer = middle
        break
    elif numbers[middle] < target:
        left = middle + 1
    else:
        right = middle - 1

print(answer)  # 3
```

Time: O(log n). Extra space: O(1) for the iterative version.

## Matrix basics

A matrix is a list of lists.

``` python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matrix[0][1])  # 2
```

Traverse rows and columns:

``` python
for row in range(len(matrix)):
    for column in range(len(matrix[row])):
        print(matrix[row][column])
```

For `r` rows and `c` columns, full traversal takes O(r × c).

## Common problem patterns

  Problem clue                          Pattern to consider
  ------------------------------------- ---------------------
  Pair in a sorted array                Two Pointers
  Longest/shortest contiguous section   Sliding Window
  Many range-sum queries                Prefix Sum
  Count values or detect duplicates     HashMap / Set
  Search sorted data                    Binary Search
  Maximum contiguous sum                Kadane's Algorithm
  Compare elements from both ends       Two Pointers
  Process every element once            Traversal

These are clues, not strict rules. Check the input constraints and
required output.

## Time complexity reference

Let `n` be the number of elements.

  Operation                          Typical time
  ------------------------------ ----------------
  Access by index                            O(1)
  Update by index                            O(1)
  Append at end                    O(1) amortized
  Search by value                            O(n)
  Traverse                                   O(n)
  Find min or max                            O(n)
  Insert at beginning                        O(n)
  Delete at beginning                        O(n)
  Sort                                 O(n log n)
  Binary search on sorted list           O(log n)

## Space complexity

-   O(1): fixed extra storage.
-   O(n): extra storage grows with input size.
-   O(n²): storage grows with the square of input size.

In-place two-pointer reversal uses O(1) extra space. Creating a second
list of `n` elements uses O(n).

## Edge cases

Consider empty arrays, one element, two elements, duplicates, negative
values, all-equal values, sorted and reverse-sorted input, missing
targets, and targets at either end.

## Common mistakes

-   Remember that slice stop indexes are excluded.
-   Check indexes before accessing elements.
-   Binary search requires sorted input.
-   A subarray is contiguous; a subsequence need not be.
-   Do not initialize maximum-subarray sum to zero when negative-only
    arrays are possible.
-   Write down window boundaries to avoid off-by-one errors.
-   Check whether sorting is allowed when original indexes matter.

## Problem-solving approach

1.  Understand the input and expected output.
2.  Work through a small example manually.
3.  Check whether order and contiguity matter.
4.  Check whether the input is sorted.
5.  Consider a brute-force solution first.
6.  Look for a pattern that avoids repeated work.
7.  State time and space complexity.
8.  Test edge cases.

## Quick reference

``` python
len(numbers)          # Number of elements
numbers[index]        # Access
numbers.append(value) # Add to end
numbers.pop()         # Remove last item
numbers.sort()        # Sort in place
sorted(numbers)       # Return sorted copy
numbers[::-1]         # Reversed copy
value in numbers      # Membership test
sum(numbers)          # Total
min(numbers)          # Smallest
max(numbers)          # Largest
```
