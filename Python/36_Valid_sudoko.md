# Valid Sudoko or Not
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

- Each row must contain the digits 1-9 without repetition.
- Each column must contain the digits 1-9 without repetition.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

# Intuition
- check rows wise 
- check column wise
- check box wise
Note: no number should be repeated 


# Approach
- Iterate row wise add to set if already number exist return false
- Iterate column wise add to set if already number exist return false
- Now box wise 

```
00 01 02   03 04 05   06 07 08
10 11 12   13 14 15   16 17 18
20 21 22   23 24 25   26 27 28

30 31 32   33 34 35   36 37 38
40 41 42   43 44 45   46 47 48
50 51 52   53 54 55   56 57 58

60 61 62   63 64 65   66 67 68
70 71 72   73 74 75   76 77 78
80 81 82   83 84 85   86 87 88
```

Each box should not contain same number 

so there are  9 box  so we have to iterate each boxes and seperate and add to set check if exist if exist  return false

To check each box seperately we need to iterate store start value of each box 

```
starts=[(0,0),(0,3),(0,6),
                (3,0),(3,3),(3,6),
                (6,0),(6,3),(6,6)]
```



# Complexity
- Time complexity:
  O(N^2)

- Space complexity:
 O(1)

# Code
```python3 []
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        for i in range(9):
            s=set()
            for j in range(9):
                ele=board[i][j]
                if ele in s:
                    return False
                elif ele != '.':
                    s.add(ele)
        for i in range(9):
            s=set()
            for j in range(9):
                ele=board[j][i]
                if ele in s:
                    return False
                elif ele != '.':
                    s.add(ele)

        starts=[(0,0),(0,3),(0,6),
                (3,0),(3,3),(3,6),
                (6,0),(6,3),(6,6)]
        for (bstart,bend) in starts:
            s=set()
            for i in range(bstart,bstart+3):
                for j in range(bend,bend+3):
                    ele=board[j][i]
                    if ele in s:
                        return False
                    elif ele != '.':
                        s.add(ele)
        return True                                                        

        
```


# Another Approach

```
      0            1             2
   -------------------------------
0 | 00 01 02   03 04 05   06 07 08
  | 10 11 12   13 14 15   16 17 18
  | 20 21 22   23 24 25   26 27 28

1 | 30 31 32   33 34 35   36 37 38
  | 40 41 42   43 44 45   46 47 48
  | 50 51 52   53 54 55   56 57 58

2 | 60 61 62   63 64 65   66 67 68
  | 70 71 72   73 74 75   76 77 78
  | 80 81 82   83 84 85   86 87 88
```
```
Hash Sets Representation:

Row 0 : {00, 01, 02, 03, 04, 05, 06, 07, 08}
Col 0 : {00, 10, 20, 30, 40, 50, 60, 70, 80}

Box (0,0) : {00, 01, 02, 10, 11, 12, 20, 21, 22}
Box (0,1) : {03, 04, 05, 13, 14, 15, 23, 24, 25}
Box (0,2) : {06, 07, 08, 16, 17, 18, 26, 27, 28}

Box (1,0) : {30, 31, 32, 40, 41, 42, 50, 51, 52}
Box (1,1) : {33, 34, 35, 43, 44, 45, 53, 54, 55}
Box (1,2) : {36, 37, 38, 46, 47, 48, 56, 57, 58}

Box (2,0) : {60, 61, 62, 70, 71, 72, 80, 81, 82}
Box (2,1) : {63, 64, 65, 73, 74, 75, 83, 84, 85}
Box (2,2) : {66, 67, 68, 76, 77, 78, 86, 87, 88}
```


### 📌 Data Structures

- `rows[i]` → set of values in row `i`
- `cols[j]` → set of values in column `j`
- `boxes[boxRow][boxCol]` → set of values in the 3×3 sub-box at position `(boxRow, boxCol)`

### 📦 Box Index Mapping

For any cell at position `(i, j)`:
```
boxRow = i // 3
boxCol = j // 3
```

---

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        row=collections.defaultdict(set)
        col=collections.defaultdict(set)
        box=collections.defaultdict(set)
        for r in range(9):
            for c in range(9):
                ele=board[r][c]
                if ele in row[r] or ele in col[c] or ele in box[(r//3,c//3)]:
                    return False
                elif ele != '.':
                    row[r].add(ele)
                    col[c].add(ele)
                    box[(r//3,c//3)].add(ele)
        print(box)
        return True   
```
