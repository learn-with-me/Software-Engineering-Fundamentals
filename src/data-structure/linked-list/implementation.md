# Implementation

## Operations on Linked Lists

### **Insertion**

#### **At the Beginning**

Add a new node at the start of the list.

```java
public void insertAtBeginning(int data) {
    Node newNode = new Node(data);
    newNode.next = head;
    head = newNode;
}
```

#### **At the End**

Add a new node at the end of the list.
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

#### **At a Specific Position**

Insert a new node after a given node.
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

### **Deletion**

#### **By a key**

Remove a node with a given key.

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

### **Traversal**

Visiting each node of the list to process the data.

```cpp
void printList(Node* node) {
    while (node != NULL) {
        cout << node->data << " ";
        node = node->next;
    }
}
```

### **Searching**

Finding a node with a specific value.

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
