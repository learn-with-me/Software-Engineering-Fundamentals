# Hash Table

### What is a Hash Table?

A hash table (or hash map) is a data structure that provides an efficient way to store and retrieve data. It uses a technique called hashing to map keys to values, allowing for average-case constant time complexity (`O(1)`) for operations like insertion, deletion, and lookup.

### Key Concepts

1. **Hash Function**
    - **Purpose**: A hash function takes an input (or key) and returns an integer known as a hash code. The hash code is then used as an index into an array where the value corresponding to the key is stored.
    - **Properties**: A good hash function should distribute keys uniformly across the hash table to minimize collisions.

2. **Buckets**
    - **Purpose**: The array in a hash table is often referred to as a series of buckets, where each bucket can hold multiple key-value pairs.
    - **Structure**: Each bucket corresponds to an index in the array, derived from the hash code of the key.

3. **Collisions**
    - **Definition**: Collisions occur when two keys hash to the same index in the array.
    - **Handling Collisions**: There are several strategies to handle collisions, including chaining and open addressing.

### Collision Handling Techniques

1. **Chaining**
    - **Description**: Each bucket in the hash table contains a list (or another data structure like a linked list) of key-value pairs. When a collision occurs, the new key-value pair is added to the list at the appropriate bucket.
    - **Pros**: Simple to implement and handles collisions effectively.
    - **Cons**: Can degrade to O(n) time complexity if many collisions occur, resulting in long lists.

2. **Open Addressing**
    - **Description**: Instead of storing multiple elements in a single bucket, open addressing places each element directly into the array. If a collision occurs, the algorithm probes (or searches) for the next empty slot in the array.
    - **Probing Methods**:
        - **Linear Probing**: Increment the index by one until an empty slot is found.
        - **Quadratic Probing**: Use a quadratic function to determine the next slot.
        - **Double Hashing**: Use a second hash function to determine the step size for probing.
    - **Pros**: Can lead to better cache performance due to fewer linked lists and reduced memory overhead.
    - **Cons**: More complex implementation and can suffer from clustering, where groups of occupied slots create long probe sequences.

### Operations on Hash Tables

1. **Insertion**
    - Calculate the hash code of the key.
    - Determine the index from the hash code.
    - Place the key-value pair at the appropriate bucket (or probe to find an empty slot in open addressing).

2. **Deletion**
    - Calculate the hash code of the key.
    - Determine the index from the hash code.
    - Remove the key-value pair from the bucket or mark the slot as deleted in open addressing.

3. **Lookup**
    - Calculate the hash code of the key.
    - Determine the index from the hash code.
    - Retrieve the value from the appropriate bucket or probe for the key in open addressing.

### Advantages of Hash Tables

- **Speed**: Average-case constant time complexity (O(1)) for insertion, deletion, and lookup operations.
- **Efficiency**: Efficient memory usage when the load factor (number of elements / number of buckets) is maintained.

### Disadvantages of Hash Tables

- **Collisions**: Handling collisions can add complexity and degrade performance.
- **Memory Overhead**: Requires a balance between speed and memory usage, as too many empty buckets waste space, while too few increase collisions.
- **Complexity**: Implementation can be complex, especially with open addressing and probing strategies.

### Use Cases

- **Databases**: Hash tables are used in indexing and quick data retrieval.
- **Caches**: Storing recently accessed data for quick lookups.
- **Symbol Tables**: In compilers and interpreters to store variable bindings.
- **Sets and Maps**: Implementing abstract data types like sets and dictionaries.
