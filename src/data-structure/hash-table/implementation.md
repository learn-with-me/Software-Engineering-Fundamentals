# Implementation

### Example

Here's a simple implementation of a hash table using chaining in Python:

```python
class HashTable:
    def __init__(self, size=10):
        self.size = size
        self.table = [[] for _ in range(size)]

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash_function(key)
        for pair in self.table[index]:
            if pair[0] == key:
                pair[1] = value
                return
        self.table[index].append([key, value])

    def lookup(self, key):
        index = self.hash_function(key)
        for pair in self.table[index]:
            if pair[0] == key:
                return pair[1]
        return None

    def delete(self, key):
        index = self.hash_function(key)
        for i, pair in enumerate(self.table[index]):
            if pair[0] == key:
                del self.table[index][i]
                return

# Example usage:
hash_table = HashTable()
hash_table.insert("apple", 10)
print(hash_table.lookup("apple"))  # Output: 10
hash_table.delete("apple")
print(hash_table.lookup("apple"))  # Output: None
```

In this example, the `HashTable` class uses a list of lists to handle collisions through chaining. The `hash_function` method computes the index for a given key, and the `insert`, `lookup`, and `delete` methods manage the key-value pairs accordingly.
