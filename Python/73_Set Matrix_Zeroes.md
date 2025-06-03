# 73. Set Matrix Zeroes

## Problem statement

if any zeros exist in that column or row make complete zeros in that column and row

```python
input : matrix = [[1,1,1],[1,0,1],[1,1,1]]
output : [[1,0,1],[0,0,0],[1,0,1]]
```

# Intuition

check each every element in matrix  if element == 0 store indexes of that element 

# Approach
Iterate each every element and if matrix[i][j]==0 store that index of i values in set and store j values in another set 
set is used to avoid dublicate elements



# Code

```python []
class Solution:
    def setZeroes(self, matrix) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        i_values=set()
        j_values=set()
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if matrix[i][j]==0:
                    i_values.add(i)
                    j_values.add(j)
        for i in i_values:
            for j in range(len(matrix[0])):
                matrix[i][j]=0
        for j in j_values:
            for i in range(len(matrix)):
                matrix[i][j]=0
             
```

# Complexity
- Time complexity:
O(m*n)


- Space complexity:
O(m+n)

But In Question Given that make constant space complexity


# Approach
check zeroth row and zeroth coloumn has any zeros 
in above approach we stored i and j indexes in set by iterating each and every element but in this approach just we make matrix[0][j]=matrix[i][0]=0 
so ith_zero is zero make all ith index to zero and jth_zero make all jth index to zero

```python
class Solution:
    def setZeroes(self, matrix) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m=len(matrix)
        n=len(matrix[0])
        
        zeroth_row=any( matrix[0][j]==0 for j in range(n))
        zeroth_col=any( matrix[i][0]==0 for i in range(m))
        for i in range(1,m):
            for j in range(1,n):
                if matrix[i][j]==0:
                    matrix[0][j]=0
                    matrix[i][0]=0
        for i in range(1,m):
            for j in range(1,n):
                if matrix[0][j]==0 or matrix[i][0]==0:
                    matrix[i][j]=0
        if zeroth_row:
            for j in range(n):
                matrix[0][j]=0
        if zeroth_col:
            for i in range(m):
                matrix[i][0]=0

```

- Time complexity:
O(m*n)


- Space complexity:
O(1)