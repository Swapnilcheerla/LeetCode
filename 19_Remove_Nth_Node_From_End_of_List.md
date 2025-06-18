# problem statement

- Given the head of a linked list, remove the nth node from the end of the list and return its head.



# Intuition
count total length and minus the n elements from it and
traverse index=length-n
now same like delete at index



# Complexity

- Time Complexity: O(N),  L is the length of the linked list.  `single traversal`
- Space Complexity: O(1), constant extra space for counters.


# Code
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        l=0
        curr=head
        while curr:
            curr=curr.next
            l+=1
        print(l)
        curr=head
        index=l-n
        if index == 0:
            return head.next
        i=0
        while curr.next and i<index-1:
            curr=curr.next
            i+=1
        if curr.next:
            curr.next=curr.next.next
        
        return head
        



        

        
```

# Approach 2: using fast and slow pointer

## Approach 

make a dummy linked list by adding extra zero start while return remove this extra added 

fast pointer first already at the n+1 place
slow will be at start

now when fast pointer reached at the end which means null 
the the slow pointer will be at just before the remove element
now slow.next=slow.next.next

just return dummy.next beacuse we added zero at start

```python
#Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy=ListNode(0,head)
        fast=slow=dummy
        for _ in range(n+1):
            fast=fast.next
        while fast:
            fast=fast.next
            slow=slow.next
        slow.next=slow.next.next
        
        return dummy.next
```