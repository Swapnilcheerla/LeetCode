# 54. Spiral Matrix

Return the Given `matrix` `m X n ` in spiral order 

```python
input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
output : [1,2,3,6,9,8,7,4,5]
```
# Code

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        turns=['right','down','left','up']
        left=0
        up=0
        res=[]
        m=down=len(matrix)
        n=right=len(matrix[0])
        i=j=k=0
        for _ in range(m*n):
            if turns[k] == 'right':
                res.append(matrix[i][j])
                
                if j == right-1:
                    k+=1
                    right-=1
                    i+=1
                else:
                    j+=1
            elif turns[k] == 'down':
                res.append(matrix[i][j])
                
                if i == down-1:
                    k+=1
                    down-=1   
                    j-=1
                else:
                    i+=1

            elif turns[k] == 'left':
                res.append(matrix[i][j])
                
                if j == left:
                    k+=1
                    left+=1  
                    i-=1
                else:
                    j-=1

            elif turns[k] == 'up':
                res.append(matrix[i][j])
                
                if i == up+1:
                    k+=1
                    up+=1
                    j+=1
                else:
                    i-=1
            if k==4:
                k=0

        return res

```

# Explanation

- When right  i index remain calm and j index increases until len(matrix[0])-1 
- Then down  j index remains calm and i increament until len(matrix)
- Then left i index remains calm and j index decreases until 0
- then up  j index remains calm and i index descreases unitl 1
