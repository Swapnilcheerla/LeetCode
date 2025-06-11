# Game of Life 
- Any live cell with fewer than two live neighbors dies as if caused by under-population.
- Any live cell with two or three live neighbors lives on to the next generation.
- Any live cell with more than three live neighbors dies, as if by over-population.


# Intuition

check its neighbours vertically ,horizontally and diagonally count only ones


# Approach
```
    OriginalValue | Changed Value | Flag Value
    -------------------------------------------
        0               0               0
        1               0               1
        0               1               2
        1               1               3
    --------------------------------------------

```
We Dont store changed values  just we flag them 
* if neighbour count is  2 or 3 if its alive then we change live(1)
    - we flag this as 3
* if neighbour count is 3 if its dead the we change to dies(0)
    - we flag this as 2

# Complexity
- Time complexity:
 O(m*n)



# Code
```python []
class Solution:
    def gameOfLife(self, board):
        """
        Do not return anything, modify board in-place instead.
        """
        rowlen=len(board)
        collen=len(board[0])
        def neibours(r,c):  # count the neighbours where value is 1
            count_nei=0
            for i in range(r-1,r+2):
                for j in range(c-1,c+2):
                    if i<0 or j<0 or i>=rowlen or j>=collen or  (i==r and j==c) or board[i][j]==0 :
                        continue
                    elif board[i][j] in  [1,3]:
                        count_nei+=1
            return count_nei

        for r in range(rowlen):
            for c in range(collen):
                count_nei=neibours(r,c)
                if board[r][c]==1 and count_nei in [2,3]:
                    board[r][c]=3.  # flag the value if current value is 1 and neighbours count is 2 or 3
                elif board[r][c]==0 and count_nei ==3:
                    board[r][c]=2   # flag the value if current value is 0 and neighbours count is  3

        for r in range(rowlen):
            for c in range(collen):
                if board[r][c] in [2,3]:
                    board[r][c]=1     # now reverse the flag value and changed value
                elif board[r][c]==1:
                    board[r][c]=0 # # now reverse the flag value and changed value