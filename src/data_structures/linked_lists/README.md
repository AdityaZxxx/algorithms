# Introduction to Linked Lists

A linked list is another fundamental linear data structure. Unlike arrays, linked lists do not store elements in contiguous memory locations. Instead, the elements are "linked" to each other using pointers or references.

## What is a Linked List?

A linked list is a sequence of **nodes**, where each node contains two pieces of information:

1.  **Data:** The actual value or element being stored.
2.  **Next:** A reference (or "pointer") to the next node in the sequence.

The first node in the list is called the **head**, and the last node's "next" reference points to `null` (or `None` in Python), indicating the end of the list.

Think of it like a treasure hunt. Each clue (node) tells you where to find the next one, until you reach the final clue that says "end".

![Linked List](https://media.geeksforgeeks.org/wp-content/uploads/20240410135517/linked-list.webp)

### Key Concepts

- **Node:** The basic building block of a linked list, containing data and a reference to the next node.
- **Head:** The entry point to the linked list. It's a reference to the very first node.
- **Next:** The reference within a node that points to the next node in the list.

## Common Linked List Operations

Here are the most common operations you can perform on a singly linked list.

### 1. Traversing the List

To access elements, you must start at the `head` and follow the `next` references until you reach the desired node. This process is called **traversal**.

**Example (Python):**

```python
# First, let's define a Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

# Create a simple linked list: 10 -> 20 -> 30
head = Node(10)
head.next = Node(20)
head.next.next = Node(30)

# Traverse and print the list
current = head
while current is not None:
    print(current.data, end=" -> ")
    current = current.next
print("None")
```

### 2. Searching for an Element

Similar to traversal, you start at the `head` and check each node's data one by one until you find the element you're looking for.

**Example (Python):**

```python
# (Assuming Node class and list from above)

def find_element(head, value):
    current = head
    index = 0
    while current is not None:
        if current.data == value:
            print(f"Found {value} at index: {index}")
            return
        current = current.next
        index += 1
    print(f"{value} not found in the list.")

find_element(head, 20)
```

### 3. Inserting an Element

Insertion is efficient in a linked list. You just need to update the `next` references, without shifting any elements.

- **At the beginning:** Create a new node, point its `next` to the current head, and then make the new node the new head. This is very fast.
- **In the middle/end:** Traverse to the node _before_ the desired insertion point, then update the `next` references to "splice" the new node into the list.

**Example (Inserting at the beginning):**

```python
# (Assuming Node class and list from above)

# Insert 5 at the beginning
new_node = Node(5)
new_node.next = head
head = new_node # The new node is now the head
```

### 4. Deleting an Element

Deletion is also efficient. You find the node _before_ the one you want to delete and update its `next` reference to "skip over" the deleted node.

**Example (Deleting from the middle):**

```python
# (Assuming Node class and list from above)
# Let's delete 20 from the list: 5 -> 10 -> 20 -> 30

# Find the node before 20 (which is 10)
previous = head.next # This is node 10
node_to_delete = previous.next # This is node 20

# Skip over node 20
previous.next = node_to_delete.next
```

## Performance (Big O Notation)

| Operation                           | Time Complexity | Explanation                                                             |
| ----------------------------------- | --------------- | ----------------------------------------------------------------------- |
| **Access (by index)**               | O(n)            | Slow. You must traverse the list from the head to find the nth element. |
| **Search**                          | O(n)            | Slow. In the worst case, you have to look at every element.             |
| **Insertion (at beginning)**        | O(1)            | Very fast. Just update the head.                                        |
| **Deletion (at beginning)**         | O(1)            | Very fast. Just update the head.                                        |
| **Insertion/Deletion (middle/end)** | O(n)            | Can be slow, as you first need to traverse to the correct position.     |

## Advantages and Disadvantages

### Advantages

- **Dynamic Size:** Linked lists can grow and shrink easily. You just add or remove nodes.
- **Fast Insertions/Deletions:** Adding or removing nodes is very fast if you are already at the correct position (especially at the beginning).

### Disadvantages

- **Slow Access:** You can't access an element by its index directly. You must traverse the list from the beginning.
- **Extra Memory:** Each node requires extra memory to store the `next` reference.

## Conclusion

Linked lists are an excellent choice when you need to perform many insertions and deletions and don't need fast random access to elements. They are the opposite of arrays in terms of performance trade-offs.
