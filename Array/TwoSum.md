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
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        num_to_index = {}
        
        # Iterate through the array
        for index, num in enumerate(nums):
            # Calculate the complement
            complement = target - num
            
            # Check if the complement is already in the hash table
            if complement in num_to_index:
                return [num_to_index[complement], index]
            
            # Store the number and its index in the hash table
            num_to_index[num] = index
        
        # If no solution is found (though the problem guarantees one)
        return None
        
