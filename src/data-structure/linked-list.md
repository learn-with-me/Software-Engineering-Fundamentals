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

### Operations on Linked Lists

1. **Insertion**
   - **At the Beginning**: Add a new node at the start of the list.
     ```java
     public void insertAtBeginning(int data) {
         Node newNode = new Node(data);
         newNode.next = head;
         head = newNode;
     }
     ```

   - **At the End**: Add a new node at the end of the list.
     ```java
     public void insertAtEnd(int data) {
         Node newNode = new Node(data);
         if (head == null) {
             head = newNode;
             return;
         }
         Node last = head;
         while (last.next != null) {
             last = last.next;
         }
         last.next = newNode;
     }
     ```

   - **At a Specific Position**: Insert a new node after a given node.
     ```java
     public void insertAfter(Node prevNode, int data) {
        if (prevNode == null) {
            return;
        }
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node last = head;
        while (last.val != prevNode.val) {
            last = last.next;
        }
        Node temp = last.next;
        last.next = newNode;
        newNode.next = temp;
     }
     ```

2. **Deletion**
   - **By a key**: Remove a node with a given key.
     ```java
     public void deleteNode(int key) {
         Node temp = head;
         Node prev = null;

         // If head node holds the key to be deleted
         if (temp != null && temp.data == key) {
             head = temp.next;
             return;
         }

         // Search for the key to be deleted
         while (temp != null && temp.data != key) {
             prev = temp;
             temp = temp.next;
         }

         // If key is not present
         if (temp == null) return;

         // Unlink the node from linked list
         prev.next = temp.next;
     }
     ```

3. **Traversal**
   - Visiting each node of the list to process the data.
     ```cpp
     void printList(Node* node) {
         while (node != NULL) {
             cout << node->data << " ";
             node = node->next;
         }
     }
     ```

4. **Searching**
   - Finding a node with a specific value.
     ```cpp
     bool search(Node* head, int key) {
         Node* current = head;
         while (current != NULL) {
             if (current->data == key) return true;
             current = current->next;
         }
         return false;
     }
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

### Example

Here is a simple example of a singly linked list in C++:

```java
class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedList {
    Node head;

    // Insert at the beginning
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;
    }

    // Insert at the end
    public void insertAtEnd(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node last = head;
        while (last.next != null) {
            last = last.next;
        }
        last.next = newNode;
    }

    // Delete a node by key
    public void deleteNode(int key) {
        Node temp = head;
        Node prev = null;

        // If head node holds the key to be deleted
        if (temp != null && temp.data == key) {
            head = temp.next;
            return;
        }

        // Search for the key to be deleted
        while (temp != null && temp.data != key) {
            prev = temp;
            temp = temp.next;
        }

        // If key is not present
        if (temp == null) return;

        // Unlink the node from linked list
        prev.next = temp.next;
    }

    // Print the linked list
    public void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LinkedList llist = new LinkedList();

        llist.insertAtBeginning(1);
        llist.insertAtEnd(2);
        llist.insertAtEnd(3);
        llist.insertAtBeginning(0);

        System.out.println("Linked List:");
        llist.printList();

        llist.deleteNode(2);
        System.out.println("Linked List after deletion of 2:");
        llist.printList();
    }
}
```

In this example:
- A singly linked list is created with nodes inserted at the beginning and end.
- A node is deleted based on its value.
- The list is printed before and after deletion to show the changes.
