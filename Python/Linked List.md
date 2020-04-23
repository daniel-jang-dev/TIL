#### Linked List implementation
```python
// Creation of Linked List

class Node:
  def __init__(self, data=None):
    self.val = data
    self.next = None

class SLinkedList:
  def __init__(self):
    self.head = None

  // Traversing a Linked List
  def listprint(self):
    ptr = self.head
    while ptr is not None:
      print (ptr.val)
      ptr = ptr.next
 
  // Insertion in a Linked List
  def AtBegining(self,newdata):
    NewNode = Node(newdata)
    NewNode.next = self.head
    self.head = NewNode

  // Inserting at the End of the Linked List
  def AnEnd(self,newData):
    NewNode = Node(newData)
    if self.head is None:
      self.head = NewNode
      return
    ptr = self.head
    whild(ptr.next):
      ptr - ptr.next
     ptr.next = NewNode
 
  // Inserting in between two Data Nodes
  def Inbetween(self,target_node,newData):
    if target_node is None:
      return
    NewNode = Node(newData)
    NewNode.next = target_node.next
    target_node.next = NewNode

  // Removing an Item form a Liked List
  def RemoveNode(self, RemoveKey):
  ptr = self.head
  if(ptr is not None):
    if(ptr.val == RemoveKey):
      self.head = head.next
      ptr = None
      return

  while(ptr is not None):
    if ptr.val == RemoveKey:
      break
    prev = ptr
    ptr = ptr.next
    
  if (ptr == None):
    return
    
  prev.next = ptr.next
  ptr = None
``` 
