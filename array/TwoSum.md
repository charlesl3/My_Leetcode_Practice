# Two Sum Problem

## Problem
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

## Solution
### Approach
We use a hash map to store indices as we iterate through the list and check for the complement.

### Complexity
- **Time Complexity**: O(n)
- **Space Complexity**: O(n)

```python
def two_sum(nums, target):
    hash_map = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in hash_map:
            return [hash_map[complement], i]
        hash_map[num] = i
