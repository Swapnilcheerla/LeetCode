# 1014. Best Sightseeing Pair

## Problem statement

Source : `leetcode`
You are given an integer array values where values[i] represents the value of the ith sightseeing spot. Two sightseeing spots i and j have a distance j - i between them.

The score of a pair (i < j) of sightseeing spots is `values[i] + values[j] + i - j`: the sum of the values of the sightseeing spots, minus the distance between them.

Return the maximum score of a pair of sightseeing spots.

```python
Input: values = [8,1,5,2,6]
Output: 11
```

## Breakdown of problem statement

Given that sighting spot is values[i]+values[j]+i-j  here i-j is distance btwm them

Now lets use some maths knowledge here  we can break here as `(values[i]+i)+(values[j]-j)

let values[i]+i if left most maximum  if we take example above example to j=2 left most top is 8 we maintain left most maximum values
values[j]-j is current value

summation of these values gives us the maximum score 

# Code

```python
class Solution:
    def maxScoreSightseeingPair(self, values) -> int:
        maxleftscore=values[0]+0 # i=0  values[i] + i # this only cares abou max of left 
        max_score=0
        # values[i] + i===leftmaxscore values[j]-j
        for j in range(1,len(values)):
            max_score=max(max_score,maxleftscore+values[j]-j)
            maxleftscore=max(maxleftscore,values[j]+j)   #values[i] + i
        return max_score
```

# Dry Run

-------Index =  [0,1,2,3,4]
Input: values = [8,1,5,2,6]
i=0
maxleftscore=8
max_score=0

### loop

loop stars from 1
j=1
max_score =max (0,8+1-1)= max_score=8
maxleftscore=max(8,1+1)=8

j=2

max_score =max (8,8+5-2)= 11
maxleftscore=max(8,5+2)=8

j=3

max_score =max (11,8+2-3)= 11
maxleftscore=max(8,2+3)=8

j=4
max_score =max (11,8+6-4)= 11
maxleftscore=max(8,6+4)=10

End of loop

Answer is 11






