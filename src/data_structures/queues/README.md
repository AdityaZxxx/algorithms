# Introduction to Queues

A queue is a linear data structure that, like a stack, follows a specific order for operations. The order is **FIFO (First-In, First-Out)**. This is the opposite of stacks (LIFO).

## What is a Queue?

A queue is a collection of elements where items are added at one end and removed from the other. The two main operations are:

- **Enqueue:** Adds an element to the **end** (or **rear**) of the queue.
- **Dequeue:** Removes an element from the **front** of the queue.

This FIFO principle ensures that the first element to be added to the queue will be the first one to be removed.

### Real-World Analogy

The most common analogy for a queue is a line of people waiting for a service, like at a checkout counter or a ticket booth.

- A new person joins at the **end** of the line (**Enqueue**).
- The person at the **front** of the line is served and leaves (**Dequeue**).
- You can see who is at the front of the line without them leaving (**Peek**).

![Queue](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20230726165642/Queue-Data-structure1.png)

## Core Queue Operations

### 1. Enqueue

The `enqueue` operation adds an element to the rear of the queue.

**Example (Python):**

```python
# We can use Python's `collections.deque` for an efficient queue
from collections import deque

queue = deque()

queue.append(10)  # Queue: [10]
queue.append(20)  # Queue: [10, 20]
queue.append(30)  # Queue: [10, 20, 30]

print(f"Queue after enqueues: {queue}")
```

### 2. Dequeue

The `dequeue` operation removes the front element from the queue and returns it.

**Example (Python):**

```python
# (Continuing from above)

removed_element = queue.popleft() # Removes 10
print(f"Dequeued element: {removed_element}") # 10
print(f"Queue after dequeue: {queue}") # [20, 30]
```

### 3. Peek (or Front)

The `peek` (or `front`) operation lets you look at the front element of the queue without removing it.

**Example (Python):**

```python
# (Continuing from above)

# To peek, we can access the first element
front_element = queue[0]

print(f"Front element is: {front_element}") # 20
print(f"Queue remains unchanged: {queue}") # [20, 30]
```

## Performance (Big O Notation)

Queue operations are very fast, especially when implemented correctly.

| Operation   | Time Complexity | Explanation                                              |
| ----------- | --------------- | -------------------------------------------------------- |
| **Enqueue** | O(1)            | Always fast. Just adds an element to one end.            |
| **Dequeue** | O(1)            | Always fast. Just removes an element from the other end. |
| **Peek**    | O(1)            | Always fast. Just looks at the element at the front.     |

**Note:** If you use a standard Python `list` and remove from the beginning (`list.pop(0)`), the dequeue operation becomes `O(n)` because all other elements must be shifted. This is why `collections.deque` is preferred for implementing queues in Python.

## How are Queues Implemented?

1.  **Using a Doubly-Ended Queue (`deque`):** In Python, this is the best way. `deque` is optimized for fast appends and pops from both ends.
2.  **Using a Linked List:** A queue can be implemented with a linked list by keeping track of both the `head` and `tail` nodes. Enqueue adds a new node at the tail, and Dequeue removes a node from the head. Both are O(1) operations.

## Common Use Cases

Queues are essential in many algorithms and systems:

- **Task Scheduling:** The CPU can have a queue of processes to execute. The operating system's scheduler decides which process to run next.
- **Buffering:** When data is transferred between two processes that work at different speeds (e.g., streaming a video), a queue is used as a buffer.
- **Breadth-First Search (BFS):** A common algorithm for traversing trees or graphs, BFS uses a queue to explore nodes level by level.
- **Printers and Network Requests:** Print jobs or network data packets are often managed in a queue.
