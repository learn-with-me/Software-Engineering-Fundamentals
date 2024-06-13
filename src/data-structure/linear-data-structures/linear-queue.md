### Understanding Queue

A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle, where elements are inserted from one end called the rear (or back) and removed from the other end called the front. This makes queues ideal for scenarios where the order of operations matters, such as task scheduling, handling requests in a web server, or managing tasks in an operating system.

### Java Implementation of Queue

Java provides a built-in interface for queues in the `java.util` package. The most common implementation of a queue is the `LinkedList` class, which implements the `Queue` interface.

Here's a basic example of using a queue in Java:

#### Using LinkedList to Implement a Queue

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        // Create a Queue using LinkedList
        Queue<Integer> queue = new LinkedList<>();

        // Add elements to the queue (Enqueue operation)
        queue.add(10);
        queue.add(20);
        queue.add(30);
        queue.add(40);

        // Display the elements in the queue
        System.out.println("Queue: " + queue);

        // Remove an element from the queue (Dequeue operation)
        int removedElement = queue.remove();
        System.out.println("Removed Element: " + removedElement);

        // Display the elements in the queue after dequeue
        System.out.println("Queue after Dequeue: " + queue);

        // Peek at the front element of the queue without removing it
        int frontElement = queue.peek();
        System.out.println("Front Element: " + frontElement);

        // Check if the queue is empty
        boolean isEmpty = queue.isEmpty();
        System.out.println("Is the Queue empty? " + isEmpty);
    }
}
```

#### Explanation:

1. **Import the Queue Interface and LinkedList Class:**
   ```java
   import java.util.LinkedList;
   import java.util.Queue;
   ```

2. **Create a Queue:**
   ```java
   Queue<Integer> queue = new LinkedList<>();
   ```
   Here, we create a queue of integers using the `LinkedList` class, which implements the `Queue` interface.

3. **Add Elements to the Queue (Enqueue Operation):**
   ```java
   queue.add(10);
   queue.add(20);
   queue.add(30);
   queue.add(40);
   ```
   We use the `add()` method to insert elements into the queue. Elements are added to the rear of the queue.

4. **Display the Queue:**
   ```java
   System.out.println("Queue: " + queue);
   ```
   This prints the current elements in the queue.

5. **Remove an Element from the Queue (Dequeue Operation):**
   ```java
   int removedElement = queue.remove();
   System.out.println("Removed Element: " + removedElement);
   ```
   The `remove()` method removes and returns the front element of the queue.

6. **Display the Queue after Dequeue:**
   ```java
   System.out.println("Queue after Dequeue: " + queue);
   ```
   This prints the queue after removing an element.

7. **Peek at the Front Element:**
   ```java
   int frontElement = queue.peek();
   System.out.println("Front Element: " + frontElement);
   ```
   The `peek()` method returns the front element without removing it from the queue.

8. **Check if the Queue is Empty:**
   ```java
   boolean isEmpty = queue.isEmpty();
   System.out.println("Is the Queue empty? " + isEmpty);
   ```
   The `isEmpty()` method checks if the queue is empty and returns a boolean value.

### Conclusion

This example demonstrates the basic operations of a queue, including adding elements (enqueue), removing elements (dequeue), peeking at the front element, and checking if the queue is empty. The `LinkedList` class in Java provides an easy way to implement queues and leverage the powerful features of the Java Collections Framework.
