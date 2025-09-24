# Introduction to Stacks

A stack is a linear data structure that follows a particular order in which operations are performed. The order is **LIFO (Last-In, First-Out)**. It is named "stack" as it behaves like a real-world stack, for example, a stack of plates.

## What is a Stack?

A stack is an abstract data type that serves as a collection of elements, with two principal operations:

- **Push:** Adds an element to the collection.
- **Pop:** Removes the most recently added element.

This LIFO principle means that the last element you put into the stack will be the very first one you take out.

### Real-World Analogy

Imagine a stack of plates:

- You place a new plate on the **top** of the stack (**Push**).
- When you need a plate, you take one from the **top** of the stack (**Pop**).
- You can also just look at the top plate without removing it (**Peek**).

You can't easily take a plate from the middle or bottom without first removing all the plates on top of it.

![Stack of Plates](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20230726165552/Stack-Data-Structure.png)

## Core Stack Operations

Stacks have a specific set of operations, which are highly optimized.

### 1. Push

The `push` operation adds an element to the top of the stack.

**Example (Python):**

```python
# In Python, a list can be used as a stack
# The append() method acts as push()
stack = []

stack.append(10)  # Stack: [10]
stack.append(20)  # Stack: [10, 20]
stack.append(30)  # Stack: [10, 20, 30]

print(f"Stack after pushes: {stack}")
```

### 2. Pop

The `pop` operation removes the top element from the stack and returns it.

**Example (Python):**

```python
# (Continuing from above)
# The pop() method on a list removes the last element

removed_element = stack.pop() # Removes 30
print(f"Popped element: {removed_element}") # 30
print(f"Stack after pop: {stack}") # [10, 20]
```

### 3. Peek (or Top)

The `peek` (or `top`) operation lets you look at the top element of the stack without removing it.

**Example (Python):**

```python
# (Continuing from above)

# To peek, we can access the last element of the list
top_element = stack[-1]

print(f"Top element is: {top_element}") # 20
print(f"Stack remains unchanged: {stack}") # [10, 20]
```

## Performance (Big O Notation)

Stack operations are extremely fast.

| Operation | Time Complexity | Explanation                                             |
| --------- | --------------- | ------------------------------------------------------- |
| **Push**  | O(1)            | Always fast. Just adds an element to one end.           |
| **Pop**   | O(1)            | Always fast. Just removes an element from the same end. |
| **Peek**  | O(1)            | Always fast. Just looks at the element at that end.     |

## How are Stacks Implemented?

Stacks are an abstract concept and can be implemented using other data structures:

1.  **Using an Array (or Python List):** This is the most common and straightforward way. The `append` and `pop` methods of a Python list map directly to `push` and `pop`.
2.  **Using a Linked List:** A stack can also be built on top of a linked list. `push` and `pop` operations would add and remove nodes from the head of the list, which is an O(1) operation.

## Common Use Cases

Stacks are used in many areas of computer science:

- **Function Calls:** The "call stack" keeps track of the functions that are currently running in a program.
- **Undo/Redo:** An application can store user actions on a stack. "Undo" pops the last action, and "Redo" pushes it back.
- **Expression Evaluation:** Stacks are used to convert and evaluate mathematical expressions (e.g., converting infix to postfix notation).
- **Backtracking:** In algorithms that need to explore a path and then go back (like in a maze), a stack is used to keep track of the path.
