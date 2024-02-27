# List ADT
### Array implementation

- Fixed length
- Same data type

```c
int my_array[4] = {1, 2, 3, 4};
```

#### Insert element

Insert at the back:
- O(1) time complexity

Insert at the front:
- O(n) time complexity

#### Remove element
- O(n) time complexity

#### Read and modify element
- O(1) time complexity
- use the index

#### Search for element
- O(n) time complexity

#### Extend the array?
- allocate memory with larger size
- copy the old array to the new array
- deallocate the old array
- double the size of the array when it is full

### Linked list implementation
- value
- pointer to next node
- not arranged sequentially in memory

Pro:
- dynamic size
- easy to insert and remove element at front

```c
struct Node {
    int value;
    struct Node *next;
}
```
```python
class Node:
    def __init__(self, value, next=None):
        self.value = value
        self.next = None
```
```c
struct LinkedList {
    struct Node *head;
}
```

#### Get the nth element
```python

def getItem(head, n):
    count = 0
    current = head

    while current is not None:
        if count == n:
            return current.value
        current = current.next
    return None
```

#### Search operation
```python
def searchItem(head, val):
    current = head
    while current is not None:
        if current.value == val:
            return True
        current = current.next
    return False
```

#### Insert an element at the front
```python
def insertFront(head, val):
    newNode = Node(val, head)
```
#### Remove element by value
```python
def removeElement(head, val):
    current = head
    while current is not None:
        nextNode = current.next
        if nextNode.value == val:
            current.next = nextNode.next
            return
        current = nextNode

