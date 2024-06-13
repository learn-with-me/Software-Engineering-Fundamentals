### Understanding Heap

A heap is a specialized tree-based data structure that satisfies the heap property:
- **Max-Heap:** In a max-heap, the key at a parent node is always greater than or equal to the keys of its children, and the largest key is at the root.
- **Min-Heap:** In a min-heap, the key at a parent node is always less than or equal to the keys of its children, and the smallest key is at the root.

Heaps are commonly used to implement priority queues and for efficient sorting algorithms such as Heap Sort.

### Java Implementation of a Max-Heap

Here's how you can implement a Max-Heap in Java:

#### MaxHeap Class with Basic Operations

```java
import java.util.Arrays;

public class MaxHeap {
    private int[] heap;
    private int size;
    private int maxSize;

    private static final int FRONT = 1;

    public MaxHeap(int maxSize) {
        this.maxSize = maxSize;
        this.size = 0;
        heap = new int[this.maxSize + 1];
        heap[0] = Integer.MAX_VALUE;
    }

    // Function to return the position of the parent for the node currently at pos
    private int parent(int pos) {
        return pos / 2;
    }

    // Function to return the position of the left child for the node currently at pos
    private int leftChild(int pos) {
        return (2 * pos);
    }

    // Function to return the position of the right child for the node currently at pos
    private int rightChild(int pos) {
        return (2 * pos) + 1;
    }

    // Function to swap two nodes of the heap
    private void swap(int fpos, int spos) {
        int tmp;
        tmp = heap[fpos];
        heap[fpos] = heap[spos];
        heap[spos] = tmp;
    }

    // Function to heapify the node at pos
    private void maxHeapify(int pos) {
        if (pos > (size / 2) && pos <= size)
            return;

        if (heap[pos] < heap[leftChild(pos)] ||
            heap[pos] < heap[rightChild(pos)]) {

            if (heap[leftChild(pos)] > heap[rightChild(pos)]) {
                swap(pos, leftChild(pos));
                maxHeapify(leftChild(pos));
            } else {
                swap(pos, rightChild(pos));
                maxHeapify(rightChild(pos));
            }
        }
    }

    // Function to insert a node into the heap
    public void insert(int element) {
        if (size >= maxSize) {
            return;
        }
        heap[++size] = element;
        int current = size;

        while (heap[current] > heap[parent(current)]) {
            swap(current, parent(current));
            current = parent(current);
        }
    }

    // Function to print the contents of the heap
    public void print() {
        for (int i = 1; i <= size / 2; i++) {
            System.out.print(" PARENT : " + heap[i] +
                    " LEFT CHILD : " + heap[2 * i] +
                    " RIGHT CHILD :" + heap[2 * i + 1]);
            System.out.println();
        }
    }

    // Function to remove and return the maximum element from the heap
    public int extractMax() {
        int popped = heap[FRONT];
        heap[FRONT] = heap[size--];
        maxHeapify(FRONT);
        return popped;
    }

    public static void main(String[] arg) {
        System.out.println("The Max Heap is ");
        MaxHeap maxHeap = new MaxHeap(15);
        maxHeap.insert(5);
        maxHeap.insert(3);
        maxHeap.insert(17);
        maxHeap.insert(10);
        maxHeap.insert(84);
        maxHeap.insert(19);
        maxHeap.insert(6);
        maxHeap.insert(22);
        maxHeap.insert(9);

        maxHeap.print();
        System.out.println("The max val is " + maxHeap.extractMax());
    }
}
```

### Explanation

1. **Node Class:**
   ```java
   import java.util.Arrays;

   public class MaxHeap {
       private int[] heap;
       private int size;
       private int maxSize;

       private static final int FRONT = 1;
   }
   ```
   This class defines the structure of the Max-Heap with an array `heap`, the current size of the heap `size`, and the maximum size of the heap `maxSize`. The `FRONT` constant denotes the index of the root node in the heap array.

2. **Utility Functions:**
   - **Parent, Left Child, and Right Child:**
     ```java
     private int parent(int pos) {
         return pos / 2;
     }

     private int leftChild(int pos) {
         return (2 * pos);
     }

     private int rightChild(int pos) {
         return (2 * pos) + 1;
     }
     ```
     These functions return the position of the parent, left child, and right child of a node at the given position.

   - **Swap Function:**
     ```java
     private void swap(int fpos, int spos) {
         int tmp;
         tmp = heap[fpos];
         heap[fpos] = heap[spos];
         heap[spos] = tmp;
     }
     ```
     This function swaps the nodes at the given positions.

   - **Max Heapify Function:**
     ```java
     private void maxHeapify(int pos) {
         if (pos >= (size / 2) && pos <= size)
             return;

         if (heap[pos] < heap[leftChild(pos)] ||
             heap[pos] < heap[rightChild(pos)]) {

             if (heap[leftChild(pos)] > heap[rightChild(pos)]) {
                 swap(pos, leftChild(pos));
                 maxHeapify(leftChild(pos));
             } else {
                 swap(pos, rightChild(pos));
                 maxHeapify(rightChild(pos));
             }
         }
     }
     ```
     This function ensures the max-heap property is maintained starting from the node at the given position.

3. **Insert Function:**
   ```java
   public void insert(int element) {
       if (size >= maxSize) {
           return;
       }
       heap[++size] = element;
       int current = size;

       while (heap[current] > heap[parent(current)]) {
           swap(current, parent(current));
           current = parent(current);
       }
   }
   ```
   This function inserts a new element into the heap and maintains the max-heap property.

4. **Print Function:**
   ```java
   public void print() {
       for (int i = 1; i <= size / 2; i++) {
           System.out.print(" PARENT : " + heap[i] +
                   " LEFT CHILD : " + heap[2 * i] +
                   " RIGHT CHILD :" + heap[2 * i + 1]);
           System.out.println();
       }
   }
   ```
   This function prints the contents of the heap in a readable format.

5. **Extract Max Function:**
   ```java
   public int extractMax() {
       int popped = heap[FRONT];
       heap[FRONT] = heap[size--];
       maxHeapify(FRONT);
       return popped;
   }
   ```
   This function removes and returns the maximum element from the heap while maintaining the max-heap property.

6. **Main Method:**
   ```java
   public static void main(String[] arg) {
       System.out.println("The Max Heap is ");
       MaxHeap maxHeap = new MaxHeap(15);
       maxHeap.insert(5);
       maxHeap.insert(3);
       maxHeap.insert(17);
       maxHeap.insert(10);
       maxHeap.insert(84);
       maxHeap.insert(19);
       maxHeap.insert(6);
       maxHeap.insert(22);
       maxHeap.insert(9);

       maxHeap.print();
       System.out.println("The max val is " + maxHeap.extractMax());
   }
   ```

### Conclusion

This example demonstrates the basic operations of a Max-Heap in Java, including insertion, heapification, and extraction of the maximum element. The `MaxHeap` class provides a clear and efficient way to implement and work with heaps, allowing for organized and efficient data storage and retrieval.
