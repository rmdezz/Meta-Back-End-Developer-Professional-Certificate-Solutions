# Lists and sets

# Lists

Lists are a common data structure in many programming languages and are represented as objects. They have in-built methods and can be declared as a string, an integer, or float. In some programming languages, you can also have lists with mixed element types.

A list is an ordered collection of elements and can be implemented using arrays or linked lists.

## ****Array-based Lists****

Array-based lists are ordered collections built using arrays as the underlying data structure. They have the same strengths and limitations as arrays, but with the added advantage of being able to perform operations like sorting. For example:

```python
list = [3, 2, 1]
list.sort()
print(list)
```

**Output:**

```python
[1, 2, 3]
```

However, with arrays, you need to determine the initial size of the structure, which can be costly if the array needs to grow during execution. If the initial size is set too small, the array will have to be copied into a larger structure multiple times, increasing computation time.

## Linked Lists

Linked lists contain two pieces of information: the data and a pointer to the next list item. They grow dynamically by adding new nodes to the list and pointing the list to their location. Linked lists are very fast for storing large amounts of data because they only require additional storage for the reference to the surrounding nodes.

**For example:**

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

linked_list = LinkedList()
first_node = Node(1)
linked_list.head = first_node
second_node = Node(2)
first_node.next = second_node
```

# Sets

Sets are similar to lists, but store elements in an unordered way. Sets only hold unique elements, and adding an element that already exists will not change the data stored. Sets are fast to search because they use hash tables and hashing functions to determine where to store elements.

**For example:**

```python
s = set([1, 2, 3, 4, 5])
print(3 in s)
```

**Output:**

```python
True
```

However, performance degrades when dealing with very large datasets due to the possibility of hash collisions (when two different values map to the same unique hash value).

# Conclusion

In this video, you have explored the strengths and weaknesses of two important and useful data structures, lists and sets. Now, you have a better understanding of when to use each depending on your storage needs.