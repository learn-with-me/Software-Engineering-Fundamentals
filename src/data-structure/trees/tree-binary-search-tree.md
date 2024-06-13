### Understanding Binary Search Tree (BST)

A Binary Search Tree (BST) is a specialized type of binary tree that maintains a sorted order of elements. In a BST:
- The left subtree of a node contains only nodes with keys less than the node’s key.
- The right subtree of a node contains only nodes with keys greater than the node’s key.
- Both left and right subtrees must also be binary search trees.

This property allows efficient search, insertion, and deletion operations, typically with a time complexity of O(log n) in a balanced BST.

### Java Implementation of Binary Search Tree

Here's how you can implement a BST in Java:

#### Node Class

```java
class Node {
    int data;
    Node left, right;

    public Node(int item) {
        data = item;
        left = right = null;
    }
}
```

#### BinarySearchTree Class with Basic Operations

```java
public class BinarySearchTree {
    Node root;

    public BinarySearchTree() {
        root = null;
    }

    // Insert a new node
    void insert(int data) {
        root = insertRec(root, data);
    }

    // Recursive insert function
    Node insertRec(Node root, int data) {
        if (root == null) {
            root = new Node(data);
            return root;
        }

        if (data < root.data)
            root.left = insertRec(root.left, data);
        else if (data > root.data)
            root.right = insertRec(root.right, data);

        return root;
    }

    // Search for a value in the BST
    boolean search(int data) {
        return searchRec(root, data);
    }

    // Recursive search function
    boolean searchRec(Node root, int data) {
        if (root == null) {
            return false;
        }
        if (root.data == data) {
            return true;
        }

        if (data < root.data) {
            return searchRec(root.left, data);
        } else {
            return searchRec(root.right, data);
        }
    }

    // Inorder traversal
    void inorder() {
        inorderRec(root);
    }

    // Recursive inorder function
    void inorderRec(Node root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.data + " ");
            inorderRec(root.right);
        }
    }

    // Delete a node
    void delete(int data) {
        root = deleteRec(root, data);
    }

    // Recursive delete function
    Node deleteRec(Node root, int data) {
        if (root == null) {
            return root;
        }

        if (data < root.data) {
            root.left = deleteRec(root.left, data);
        } else if (data > root.data) {
            root.right = deleteRec(root.right, data);
        } else {
            // Node with only one child or no child
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            }

            // Node with two children: Get the inorder successor (smallest in the right subtree)
            root.data = minValue(root.right);

            // Delete the inorder successor
            root.right = deleteRec(root.right, root.data);
        }

        return root;
    }

    int minValue(Node root) {
        int minValue = root.data;
        while (root.left != null) {
            minValue = root.left.data;
            root = root.left;
        }
        return minValue;
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();

        // Insert nodes into the BST
        bst.insert(50);
        bst.insert(30);
        bst.insert(20);
        bst.insert(40);
        bst.insert(70);
        bst.insert(60);
        bst.insert(80);

        // Print the BST using inorder traversal
        System.out.println("Inorder traversal of the given tree:");
        bst.inorder();

        // Search for a value in the BST
        System.out.println("\n\nSearch for value 40 in the BST:");
        System.out.println(bst.search(40) ? "Value found" : "Value not found");

        // Delete a node from the BST
        System.out.println("\nDelete 20:");
        bst.delete(20);
        System.out.println("Inorder traversal of the modified tree:");
        bst.inorder();

        System.out.println("\nDelete 30:");
        bst.delete(30);
        System.out.println("Inorder traversal of the modified tree:");
        bst.inorder();

        System.out.println("\nDelete 50:");
        bst.delete(50);
        System.out.println("Inorder traversal of the modified tree:");
        bst.inorder();
    }
}
```

### Explanation

1. **Node Class:**
   ```java
   class Node {
       int data;
       Node left, right;

       public Node(int item) {
           data = item;
           left = right = null;
       }
   }
   ```
   This class represents a node in the BST, containing an integer `data`, and pointers to the left and right children.

2. **BinarySearchTree Class:**
   - **Insert Method:**
     ```java
     void insert(int data) {
         root = insertRec(root, data);
     }
     ```
     This method inserts a new node into the BST.

   - **Recursive Insert Function:**
     ```java
     Node insertRec(Node root, int data) {
         if (root == null) {
             root = new Node(data);
             return root;
         }

         if (data < root.data)
             root.left = insertRec(root.left, data);
         else if (data > root.data)
             root.right = insertRec(root.right, data);

         return root;
     }
     ```

   - **Search Method:**
     ```java
     boolean search(int data) {
         return searchRec(root, data);
     }
     ```

   - **Recursive Search Function:**
     ```java
     boolean searchRec(Node root, int data) {
         if (root == null) {
             return false;
         }
         if (root.data == data) {
             return true;
         }

         if (data < root.data) {
             return searchRec(root.left, data);
         } else {
             return searchRec(root.right, data);
         }
     }
     ```

   - **Inorder Traversal:**
     ```java
     void inorder() {
         inorderRec(root);
     }
     ```

   - **Recursive Inorder Function:**
     ```java
     void inorderRec(Node root) {
         if (root != null) {
             inorderRec(root.left);
             System.out.print(root.data + " ");
             inorderRec(root.right);
         }
     }
     ```

   - **Delete Method:**
     ```java
     void delete(int data) {
         root = deleteRec(root, data);
     }
     ```

   - **Recursive Delete Function:**
     ```java
     Node deleteRec(Node root, int data) {
         if (root == null) {
             return root;
         }

         if (data < root.data) {
             root.left = deleteRec(root.left, data);
         } else if (data > root.data) {
             root.right = deleteRec(root.right, data);
         } else {
             if (root.left == null) {
                 return root.right;
             } else if (root.right == null) {
                 return root.left;
             }

             root.data = minValue(root.right);
             root.right = deleteRec(root.right, root.data);
         }

         return root;
     }
     ```

   - **Find Minimum Value in the Right Subtree:**
     ```java
     int minValue(Node root) {
         int minValue = root.data;
         while (root.left != null) {
             minValue = root.left.data;
             root = root.left;
         }
         return minValue;
     }
     ```

3. **Main Method:**
   ```java
   public static void main(String[] args) {
       BinarySearchTree bst = new BinarySearchTree();

       bst.insert(50);
       bst.insert(30);
       bst.insert(20);
       bst.insert(40);
       bst.insert(70);
       bst.insert(60);
       bst.insert(80);

       System.out.println("Inorder traversal of the given tree:");
       bst.inorder();

       System.out.println("\n\nSearch for value 40 in the BST:");
       System.out.println(bst.search(40) ? "Value found" : "Value not found");

       System.out.println("\nDelete 20:");
       bst.delete(20);
       System.out.println("Inorder traversal of the modified tree:");
       bst.inorder();

       System.out.println("\nDelete 30:");
       bst.delete(30);
       System.out.println("Inorder traversal of the modified tree:");
       bst.inorder();

       System.out.println("\nDelete 50:");
       bst.delete(50);
       System.out.println("Inorder traversal of the modified tree:");
       bst.inorder();
   }
   ```

### Conclusion

This example demonstrates the basic operations of a Binary Search Tree (BST) in Java, including insertion, search, deletion, and traversal (inorder). The `BinarySearchTree` class provides a clear and efficient way to implement and work with BSTs, allowing for organized and efficient data storage and retrieval.
