## Maximum Subarray (Python)

The Maximum Subarray problem is to find the contiguous subarray within a one-dimensional array of numbers which has the largest sum.

### Problem Statement

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

### Example

```python
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
# Explanation: [4,-1,2,1] has the largest sum = 6.
```

### Solution (Kadane's Algorithm)

```python
def max_subarray(nums):
    max_sum = current_sum = nums[0]
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    return max_sum
```

### Complexity

- Time: O(n)
- Space: O(1)