# Algorithm Pattern Notes

This file records reusable ideas rather than full problem solutions.

## Hash Map

### Recognition cue

When repeatedly asking whether a value has already appeared, or repeatedly searching for a complementary value, consider whether a hash map can replace a nested search.

### Current learning target

**Two Sum:** the first accepted solution used two loops, which is O(n²). Revisit the problem and determine how storing previously seen values can reduce repeated searching.

---

## Stack

### Recognition cue

A stack is useful when the most recently seen unfinished item must be handled first (LIFO: Last In, First Out).

### Python basics

```python
stack = []
stack.append(x)  # push
x = stack.pop()  # pop
```

### Learned from

**Valid Parentheses:** independently recognized that opening brackets should be stored and matched when closing brackets appear. Python stack syntax was looked up during the attempt.

---

## One Pass / Running Minimum

### Recognition cue

When the answer for the current position depends on the best value seen earlier, consider maintaining that value while scanning once instead of comparing every pair.

### Learned from

**Best Time to Buy and Sell Stock:** maintain the cheapest buy price/index seen so far and compare the current selling price against it. This produces an O(n) solution.
