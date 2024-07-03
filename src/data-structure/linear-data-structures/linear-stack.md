### Understanding Stack

A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle, where elements are added (pushed) and removed (popped) from the same end, referred to as the top of the stack. Stacks are used in various applications such as expression evaluation, backtracking algorithms, and function call management in programming languages.

### Java Implementation of Stack

Java provides a built-in class `Stack` in the `java.util` package. Here’s how to use it:

#### Using the Stack Class

```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        // Create a Stack
        Stack<Integer> stack = new Stack<>();

        // Push elements onto the stack
        stack.push(10);
        stack.push(20);
        stack.push(30);
        stack.push(40);

        // Display the elements in the stack
        System.out.println("Stack: " + stack);

        // Pop an element from the stack
        int poppedElement = stack.pop();
        System.out.println("Popped Element: " + poppedElement);

        // Display the stack after pop
        System.out.println("Stack after Pop: " + stack);

        // Peek at the top element of the stack without removing it
        int topElement = stack.peek();
        System.out.println("Top Element: " + topElement);

        // Check if the stack is empty
        boolean isEmpty = stack.isEmpty();
        System.out.println("Is the Stack empty? " + isEmpty);
    }
}
```

#### Explanation:

**Import the Stack Class:**

```java
import java.util.Stack;
```

**Create a Stack:**

```java
Stack<Integer> stack = new Stack<>();
```

Here, we create a stack of integers.

**Push Elements onto the Stack:**

```java
stack.push(10);
stack.push(20);
stack.push(30);
stack.push(40);
```

We use the `push()` method to add elements to the top of the stack.

**Display the Stack:**

```java
System.out.println("Stack: " + stack);
```

This prints the current elements in the stack.

**Pop an Element from the Stack:**

```java
int poppedElement = stack.pop();
System.out.println("Popped Element: " + poppedElement);
```

The `pop()` method removes and returns the top element of the stack.

**Display the Stack after Pop:**

```java
System.out.println("Stack after Pop: " + stack);
```

This prints the stack after removing an element.

**Peek at the Top Element:**

```java
int topElement = stack.peek();
System.out.println("Top Element: " + topElement);
```

The `peek()` method returns the top element without removing it from the stack.

**Check if the Stack is Empty:**

```java
boolean isEmpty = stack.isEmpty();
System.out.println("Is the Stack empty? " + isEmpty);
```

The `isEmpty()` method checks if the stack is empty and returns a boolean value.

### Conclusion

This example demonstrates the basic operations of a stack, including pushing elements, popping elements, peeking at the top element, and checking if the stack is empty. The `Stack` class in Java provides a convenient way to implement stacks and use their core functionalities in applications.
