# Trie

### What is a Trie?

A trie, also known as a prefix tree or digital tree, is a specialized tree-like data structure that is used to store a dynamic set of strings, where the keys are usually strings. It is particularly effective for solving problems involving retrieval of keys, such as autocomplete and spell checker functionalities.

### Key Concepts

1. **Nodes and Edges**
   - **Nodes**: Each node in a trie represents a single character of a string.
   - **Edges**: Edges connect nodes and represent the transition from one character to the next in the strings being stored.

2. **Root**
   - The root node represents the beginning of the trie and does not contain any character.

3. **Children**
   - Each node can have multiple children, representing the next character in the possible strings.

4. **End of Word Marker**
   - Some nodes are marked to indicate that they represent the end of a valid string (word) in the trie.

### How Tries Work

1. **Insertion**
   - To insert a word, start at the root node.
   - For each character in the word, check if there is an edge to a child node corresponding to that character.
   - If the edge does not exist, create a new node and edge.
   - Move to the child node and repeat the process for the next character.
   - After the last character, mark the node as the end of a word.

2. **Search**
   - To search for a word, start at the root node.
   - For each character in the word, follow the edge to the corresponding child node.
   - If at any point the edge does not exist, the word is not in the trie.
   - If all characters are found and the final node is marked as the end of a word, the word is in the trie.

3. **Deletion**
   - To delete a word, first search for the word to ensure it exists.
   - If found, unmark the end of the word node.
   - Optionally, remove nodes that are no longer needed to save space.

### Advantages of Tries

- **Efficient Search**: Tries provide efficient search operations, typically O(m) where m is the length of the word, because each character is processed once.
- **Prefix Matching**: Tries are excellent for prefix-based searches, such as autocomplete, because all words with a given prefix are located in the same subtree.
- **Space Efficiency**: Although tries can use more space compared to other data structures for small datasets, they can be more space-efficient for large datasets with common prefixes.

### Disadvantages of Tries

- **Memory Usage**: Tries can consume a lot of memory, especially if there are not many common prefixes among the strings.
- **Complex Implementation**: Implementing tries can be more complex compared to other data structures like hash tables.

### Applications of Tries

1. **Autocomplete**: Quickly suggest completions for a given prefix.
2. **Spell Checkers**: Verify if a word exists and suggest corrections.
3. **IP Routing**: Store routing tables in networking.
4. **DNA Sequencing**: Efficient storage and retrieval of DNA sequences.
5. **Word Games**: Support for games like Boggle or Scrabble.

### Example

Here is a simple implementation of a trie in Python:

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end_of_word

    def starts_with(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True

# Example usage:
trie = Trie()
trie.insert("apple")
print(trie.search("apple"))    # Output: True
print(trie.search("app"))      # Output: False
print(trie.starts_with("app")) # Output: True
trie.insert("app")
print(trie.search("app"))      # Output: True
```

In this example, the `Trie` class supports inserting words, searching for exact words, and checking if any words in the trie start with a given prefix. The `TrieNode` class represents each node in the trie, holding a dictionary of children and a boolean indicating if the node marks the end of a word.
