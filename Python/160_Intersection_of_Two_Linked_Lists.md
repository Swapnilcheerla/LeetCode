# 160. Intersection of Two Linked Lists

* Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. 
* If the two linked lists have no intersection at all, return `null`.
# Intuition
Add each node to set and check exist or not

# Approach
traverse first list and add each node to set
the traverse second list check node exist in above added set or not if exists return zero else null

# Complexity
- Time complexity:
(O(n + m)) — n and m are lengths of the two lists.

- Space complexity:
 O(n) 
# Code
```python 
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode):
        a_ele=set()
        curr_nodeA=headA
        while curr_nodeA:
            a_ele.add(curr_nodeA)
            curr_nodeA = curr_nodeA.next 
        curr_nodeB=headB
        while curr_nodeB:
            if curr_nodeB in a_ele:
                return curr_nodeB
            curr_nodeB = curr_nodeB.next     
        
        return None



```


# Approach

Two Pointer approach 
pointer one starts at headA and goes until None next pointer then starts from another HeadB
Another pointer  starts at headb and goes until None next pointer then starts from another HeadA
while doing this in circular way they meet at some point then we return value


- Space complexity:
 O(1)

# Code
```python 


class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode):
        curr_nodeA=headA
        curr_nodeB=headB
        while curr_nodeA != curr_nodeB:
            curr_nodeA = curr_nodeA.next if  curr_nodeA else headB
            curr_nodeB = curr_nodeB.next if  curr_nodeB else headA
        
        return curr_nodeA
        
```