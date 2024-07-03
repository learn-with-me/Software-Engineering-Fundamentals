### Understanding Balanced Trees

A balanced tree is a type of binary tree in which the height of the left and right subtrees of any node differs by no more than one. Balanced trees ensure that operations such as insertion, deletion, and lookup can be performed in O(log n) time. Common types of balanced trees include AVL trees and Red-Black trees.

### Java Implementation of AVL Tree

An AVL (Adelson-Velsky and Landis) tree is a self-balancing binary search tree where the difference in heights between the left and right subtrees (balance factor) of any node is at most one. If the balance factor of any node becomes more than one, rotations are performed to balance the tree.

Here’s how you can implement an AVL tree in Java:

#### Node Class

```java
class Node {
    int key, height;
    Node left, right;

    Node(int d) {
        key = d;
        height = 1;
    }
}
```

#### AVLTree Class with Basic Operations

```java
public class AVLTree {
    Node root;

    // A utility function to get the height of the tree
    int height(Node N) {
        if (N == null)
            return 0;
        return N.height;
    }

    // A utility function to get the maximum of two integers
    int max(int a, int b) {
        return (a > b) ? a : b;
    }

    // A utility function to right rotate subtree rooted with y
    Node rightRotate(Node y) {
        Node x = y.left;
        Node T2 = x.right;

        // Perform rotation
        x.right = y;
        y.left = T2;

        // Update heights
        y.height = max(height(y.left), height(y.right)) + 1;
        x.height = max(height(x.left), height(x.right)) + 1;

        // Return new root
        return x;
    }

    // A utility function to left rotate subtree rooted with x
    Node leftRotate(Node x) {
        Node y = x.right;
        Node T2 = y.left;

        // Perform rotation
        y.left = x;
        x.right = T2;

        // Update heights
        x.height = max(height(x.left), height(x.right)) + 1;
        y.height = max(height(y.left), height(y.right)) + 1;

        // Return new root
        return y;
    }

    // Get Balance factor of node N
    int getBalance(Node N) {
        if (N == null)
            return 0;
        return height(N.left) - height(N.right);
    }

    Node insert(Node node, int key) {
        // Perform the normal BST rotation
        if (node == null)
            return (new Node(key));

        if (key < node.key)
            node.left = insert(node.left, key);
        else if (key > node.key)
            node.right = insert(node.right, key);
        else // Duplicate keys not allowed
            return node;

        // Update height of this ancestor node
        node.height = 1 + max(height(node.left), height(node.right));

        // Get the balance factor of this ancestor node to check whether this node became unbalanced
        int balance = getBalance(node);

        // If this node becomes unbalanced, then there are 4 cases

        // Left Left Case
        if (balance > 1 && key < node.left.key)
            return rightRotate(node);

        // Right Right Case
        if (balance < -1 && key > node.right.key)
            return leftRotate(node);

        // Left Right Case
        if (balance > 1 && key > node.left.key) {
            node.left = leftRotate(node.left);
            return rightRotate(node);
        }

        // Right Left Case
        if (balance < -1 && key < node.right.key) {
            node.right = rightRotate(node.right);
            return leftRotate(node);
        }

        // return the (unchanged) node pointer
        return node;
    }

    // A utility function to print preorder traversal of the tree
    // The function also prints height of every node
    void preOrder(Node node) {
        if (node != null) {
            System.out.print(node.key + " ");
            preOrder(node.left);
            preOrder(node.right);
        }
    }

    public static void main(String[] args) {
        AVLTree tree = new AVLTree();

        /* Constructing tree given in the above figure */
        tree.root = tree.insert(tree.root, 10);
        tree.root = tree.insert(tree.root, 20);
        tree.root = tree.insert(tree.root, 30);
        tree.root = tree.insert(tree.root, 40);
        tree.root = tree.insert(tree.root, 50);
        tree.root = tree.insert(tree.root, 25);

        /* The constructed AVL Tree would be
                 30
                /  \
              20    40
             /  \    \
           10  25    50
        */
        System.out.println("Preorder traversal" +
                " of constructed tree is : ");
        tree.preOrder(tree.root);
    }
}
```

### Explanation

**Node Class:**

```java
class Node {
    int key, height;
    Node left, right;

    Node(int d) {
        key = d;
        height = 1;
    }
}
```

This class represents a node in the AVL tree, containing an integer `key`, height of the node, and pointers to the left and right children.

2. **AVLTree Class:**
   - **Height Function:**
     ```java
     int height(Node N) {
         if (N == null)
             return 0;
         return N.height;
     }
     ```
     This utility function returns the height of the tree rooted at a given node.

   - **Maximum Function:**
     ```java
     int max(int a, int b) {
         return (a > b) ? a : b;
     }
     ```

   - **Right Rotate Function:**
     ```java
     Node rightRotate(Node y) {
         Node x = y.left;
         Node T2 = x.right;

         x.right = y;
         y.left = T2;

         y.height = max(height(y.left), height(y.right)) + 1;
         x.height = max(height(x.left), height(x.right)) + 1;

         return x;
     }
     ```
     This function performs a right rotation on the subtree rooted with y.

   - **Left Rotate Function:**
     ```java
     Node leftRotate(Node x) {
         Node y = x.right;
         Node T2 = y.left;

         y.left = x;
         x.right = T2;

         x.height = max(height(x.left), height(x.right)) + 1;
         y.height = max(height(y.left), height(y.right)) + 1;

         return y;
     }
     ```
     This function performs a left rotation on the subtree rooted with x.

   - **Get Balance Function:**
     ```java
     int getBalance(Node N) {
         if (N == null)
             return 0;
         return height(N.left) - height(N.right);
     }
     ```
     This function returns the balance factor of a node.

   - **Insert Function:**
     ```java
     Node insert(Node node, int key) {
         if (node == null)
             return (new Node(key));

         if (key < node.key)
             node.left = insert(node.left, key);
         else if (key > node.key)
             node.right = insert(node.right, key);
         else
             return node;

         node.height = 1 + max(height(node.left), height(node.right));
         int balance = getBalance(node);

         if (balance > 1 && key < node.left.key)
             return rightRotate(node);

         if (balance < -1 && key > node.right.key)
             return leftRotate(node);

         if (balance > 1 && key > node.left.key) {
             node.left = leftRotate(node.left);
             return rightRotate(node);
         }

         if (balance < -1 && key < node.right.key) {
             node.right = rightRotate(node.right);
             return leftRotate(node);
         }

         return node;
     }
     ```
     This function inserts a new key into the AVL tree and balances it if necessary.

   - **Preorder Traversal:**
     ```java
     void preOrder(Node node) {
         if (node != null) {
             System.out.print(node.key + " ");
             preOrder(node.left);
             preOrder(node.right);
         }
     }
     ```

3. **Main Method:**
   ```java
   public static void main(String[] args) {
       AVLTree tree = new AVLTree();

       tree.root = tree.insert(tree.root, 10);
       tree.root = tree.insert(tree.root, 20);
       tree.root = tree.insert(tree.root, 30);
       tree.root = tree.insert(tree.root, 40);
       tree.root = tree.insert(tree.root, 50);
       tree.root = tree.insert(tree.root, 25);

       System.out.println("Preorder traversal" +
               " of constructed tree is : ");
       tree.preOrder(tree.root);
   }
   ```

### Conclusion

This example demonstrates the basic operations of an AVL tree, a type of balanced binary search tree, including insertion and balancing through rotations. The `AVLTree` class in Java provides a clear and efficient way to implement and work with balanced trees, ensuring that the tree remains balanced after every insertion operation, which allows for efficient search, insertion, and deletion operations.
