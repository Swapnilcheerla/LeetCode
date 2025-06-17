# Problem Statement
- MyLinkedList() Initializes the MyLinkedList object.
- int get(int index) Get the value of the indexth node in the linked list. If the index is invalid, return -1.
- void addAtHead(int val) Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
- void addAtTail(int val) Append a node of value val as the last element of the linked list.
- void addAtIndex(int index, int val) Add a node of value val before the indexth node in the linked list. If index equals the length of the linked list, the node will be appended to the end of the linked list. If index is greater than the length, the node will not be inserted.
- void deleteAtIndex(int index) Delete the indexth node in the linked list, if the index is valid.



# Approach

## get 
* take a count traverse until the count == inded then return val
## add at head 
* create a  new node
* node of next will be already existing head 
* make node as head ( if you don't make head as node old one will be head no use of adding node)
## add at tail
- check the list is empty
*  if empty so head will be node
- if not empty interate until the curr pointer next is null
- curr pointer next will be new node

## add at index
- if index =0 means add at head code reause 
- traverse the list while increament a count == index - 1
then
* new node next will be curr.next
* curr.nect will be new node

## delete at index
- check if list is empty just return 
- check if index ==0  except head return
- if traverse until the count == index -1
the next= next.next we skip one node 
- check if index is greater than the size of the list just return





# Code
```python
class Node:
    def __init__(self, val=0):
        self.val = val
        self.next = None
class MyLinkedList:

    def __init__(self):
        self.head=None

        

    def get(self, index: int) -> int:
        curr=self.head
        i=0
        while curr:
            if i==index:
                return curr.val
            
            curr=curr.next
            i+=1
        return -1
        

    def addAtHead(self, val: int) -> None:
        node=Node(val)
        node.next=self.head # this is connected to node
        self.head=node      # this node is made ad head now hhead is newly added node
        

        

    def addAtTail(self, val: int) -> None:
        node=Node(val)
        # so what if the linked list was not yet created 
        if not self.head:   # this is where linked is empty
            self.head= node
            return

        curr=self.head
        while curr.next: # this is until next is null which means end of the linked list
            curr=curr.next
        curr.next=node
        

    def addAtIndex(self, index: int, val: int) -> None:
    
        node=Node(val)
        if index == 0:
            self.addAtHead(val)
            return
        curr=self.head
        i=0
        while curr and i<index - 1:
            
            curr=curr.next
            i+=1
        if curr:
            node.next = curr.next
            curr.next=node

        
        

    def deleteAtIndex(self, index: int) -> None:
        if not self.head:
            return
        if index==0:
            self.head=self.head.next
            return
        i=0
        curr= self.head
        while curr.next and i<index-1 :
           curr=curr.next
           i+=1
        if curr.next:
            curr.next=curr.next.next
        return


# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```