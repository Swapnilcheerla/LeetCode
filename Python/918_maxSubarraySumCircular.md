## Maximum Sum Circular Subarray

### Description 

Given a circular integer array nums of length n, return the maximum possible sum of a non-empty subarray of `nums`.

the next element of nums[i] is nums[(i + 1) % n] and the previous element of nums[i] is nums[(i - 1 + n) % n]

should include each buffer at  single time

```python
Input:nums = [5, -3, 5]
Output : 10
```

```python
class Solution:
    def maxSubarraySumCircular(self, nums) -> int:
        curr_sum_min=curr_sum_max=nums[0]
        max_sum=min_sum=total=nums[0]
        for i in range(1,len(nums)):
            total+=nums[i]
            curr_sum_max=max(curr_sum_max+nums[i],nums[i])
            curr_sum_min=min(curr_sum_min+nums[i],nums[i])
            max_sum=max(curr_sum_max,max_sum)
            min_sum=min(curr_sum_min,min_sum)
        #print(total,max_sum,min_sum)
        return max(max_sum,total-min_sum) if max_sum>0 else max_sum
```

## Explanation 
### Non Circular case Straightforward Kadane’s Algorithm
- the max sub array wraps arround the  start to end

```python
curr_sum_max = max(curr_sum_max + nums[i], nums[i])
max_sum = max(curr_sum_max, max_sum)
```
### Circular Case (Trick: total - min subarray)
- To handle wrap arround subarrays

maximum sum with wrap = total sum - min sum subarray

Why?

- The total array is all elements
- if you subtract worst part which is smallest sum , you only left with the best wraparound.

- totak =7
- min sum= -3
- total - min = 7 - (-7 )== 10  which is first and last fives

### what if all elements are negative in above case 

- then max sum is least negative number and total - min sum  becomes 0 not a valid

that why we do 
 ```python
 if max_sum > 0:
    return max(max_sum, total - min_sum)
else:
    return max_sum

 ```



