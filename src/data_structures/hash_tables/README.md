# Introduction to Hash Tables

A hash table, also known as a hash map, is a data structure that implements an associative array abstract data type, a structure that can map **keys** to **values**. A hash table uses a **hash function** to compute an index, also called a hash code, into an array of buckets or slots, from which the desired value can be found.

In Python, the built-in `dictionary` is a classic implementation of a hash table.

## What is a Hash Table?

A hash table is all about storing key-value pairs. You use a `key` (e.g., a name) to find its corresponding `value` (e.g., a phone number). This is incredibly fast because the hash table uses the key to directly calculate where the value is stored.

This process involves two main components:

1.  **The Hash Function:** A function that takes a key and transforms it into a numerical index.
2.  **The Array (Buckets):** An array where the values are stored. The index calculated by the hash function tells the hash table which "bucket" to place the value in.

### Real-World Analogy

Think of a large filing cabinet (the array). Each drawer is numbered.

- You have a piece of paper with information (the **value**).
- You write a title on it (the **key**).
- A special system (the **hash function**) tells you _exactly_ which drawer number to put the paper in based on its title.
- When you need the paper back, you use the title again, the system gives you the same drawer number, and you can retrieve it instantly without searching through all the drawers.

![Hash Table](https://media.geeksforgeeks.org/wp-content/uploads/20240508162721/Components-of-Hashing.webp)

## Core Hash Table Operations

### 1. Insert (or Set)

To add a key-value pair, the hash table takes the key, runs it through the hash function to get an index, and stores the value at that index in the underlying array.

**Example (Python Dictionary):**

```python
# Create a hash table (dictionary)
phone_book = {}

# Insert key-value pairs
phone_book["Alice"] = "555-1234"
phone_book["Bob"] = "555-5678"
phone_book["Charlie"] = "555-8765"

print(f"Phone book: {phone_book}")
```

### 2. Search (or Get)

To find a value, you provide the key. The hash table uses the hash function to calculate the index and immediately goes to that location to retrieve the value. This is why lookups are so fast.

**Example (Python):**

```python
# (Continuing from above)

# Search for Bob's number
bobs_number = phone_book["Bob"]

print(f"Bob's number is: {bobs_number}")
```

### 3. Delete (or Remove)

To delete a pair, the hash table finds the location using the key's hash and removes the element.

**Example (Python):**

```python
# (Continuing from above)

del phone_book["Charlie"]

print(f"Phone book after deletion: {phone_book}")
```

## Hash Collisions

What happens if the hash function generates the same index for two different keys? This is called a **collision**.

Modern hash tables have strategies to handle this. A common one is **Chaining**, where each bucket in the array doesn't just store a single value, but a linked list of values. If a collision occurs, the new key-value pair is simply added to the linked list at that index.

![Hash Collision](https://media.geeksforgeeks.org/wp-content/uploads/20241220115555333222/collision-in-hashing.webp)

Because of collisions, the performance of a hash table can sometimes be worse than average, but this is rare in well-designed hash tables.

## Performance (Big O Notation)

| Operation  | Average Case Time | Worst Case Time | Explanation                                                               |
| ---------- | ----------------- | --------------- | ------------------------------------------------------------------------- |
| **Insert** | O(1)              | O(n)            | Super fast on average. The worst case (O(n)) happens if all keys collide. |
| **Search** | O(1)              | O(n)            | Super fast on average. The worst case requires searching a linked list.   |
| **Delete** | O(1)              | O(n)            | Super fast on average. The worst case is the same as search.              |

## Advantages and Disadvantages

### Advantages

- **Very Fast Lookups:** The main benefit. Getting a value by its key is, on average, a constant-time operation.
- **Flexible Keys:** You can use many different types of objects as keys (strings, numbers, etc.).

### Disadvantages

- **No Order:** Hash tables do not store elements in a sorted or predictable order.
- **Worst-Case Performance:** A bad hash function or many collisions can slow down operations significantly.
- **Memory Overhead:** The underlying array might be much larger than the number of elements stored to keep the number of collisions low.

## Conclusion

Hash tables are incredibly powerful and are one of the most commonly used data structures in programming. They are perfect for any situation where you need fast access to data based on a unique identifier or key.
