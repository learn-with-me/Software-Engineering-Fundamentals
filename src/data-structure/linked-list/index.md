# Linked List

### What is a Linked List?

A linked list is a linear data structure in which elements, called nodes, are connected using pointers. Each node contains two parts: the data and a reference (or pointer) to the next node in the sequence. Unlike arrays, linked lists do not store elements in contiguous memory locations.

### Key Characteristics

1. **Dynamic Size**: The size of a linked list can grow or shrink dynamically as nodes are added or removed.
2. **Non-contiguous Memory Allocation**: Nodes are not stored in contiguous memory locations; each node points to the next node.
3. **Pointer-based Structure**: Each node contains a pointer/reference to the next node in the list.

### Types of Linked Lists

1. **Singly Linked List**
    - Each node points to the next node.
    - The last node points to `null` (or `None` in Python).
    - Example:
     ```plaintext
     Head -> [Data|Next] -> [Data|Next] -> [Data|Next] -> null
     ```

2. **Doubly Linked List**
    - Each node contains a pointer to both the next and the previous node.
    - Provides bidirectional traversal.
    - Example:
     ```plaintext
     Head <-> [Prev|Data|Next] <-> [Prev|Data|Next] <-> [Prev|Data|Next] <-> null
     ```

3. **Circular Linked List**
    - The last node points back to the first node, forming a circle.
    - Can be singly or doubly linked.
    - Example (Singly):
     ```plaintext
     Head -> [Data|Next] -> [Data|Next] -> [Data|Next] -> Head
     ```

### Advantages of Linked Lists

1. **Dynamic Size**: Can grow and shrink in size during runtime.
2. **Ease of Insertion/Deletion**: Inserting and deleting nodes does not require shifting elements, unlike arrays.
3. **Efficient Memory Usage**: Memory is allocated as needed.

### Disadvantages of Linked Lists

1. **Memory Overhead**: Requires extra memory for pointers.
2. **Sequential Access**: Nodes must be accessed sequentially from the head, making random access inefficient.
3. **Complexity**: More complex to implement and manage compared to arrays.

### Applications of Linked Lists

1. **Dynamic Memory Allocation**: Used in applications where dynamic memory allocation is required.
2. **Implementation of Other Data Structures**: Used to implement stacks, queues, and graphs.
3. **Navigation Systems**: Used in navigation systems where items need to be frequently added or removed.
