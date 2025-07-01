## Statement 

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

# Approach
Take a dummy node  and attach to the start node 
lets assume  swap1 as temp 1 node
swap2 as temp2 node
now we swaps two temp node and
first the dummy = prev we start from prev node
after swapping orev will be the swap1 node because we swapped

# Complexity
- Time complexity:
 $$O(n)$$ 

- Space complexity:
$$O(1)$$

# Code
```python []
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:

    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy= ListNode(0,head)
        prev=dummy

        while prev.next and prev.next.next:
            swap1=prev.next
            swap2=prev.next.next

            swap1.next=swap2.next
            swap2.next=swap1

            prev.next=swap2
            prev=swap1

        return dummy.next
           
           




        
        
        
```

``` python
Input: head = [1,2,3,4]

Output: [2,1,4,3]
```