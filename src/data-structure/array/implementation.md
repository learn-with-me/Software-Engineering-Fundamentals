# Implementation

### Example

Here is a simple example of how arrays are used in C++:

```cpp
#include <iostream>
using namespace std;

int main() {
    // Declare and initialize an array
    int arr[5] = {1, 2, 3, 4, 5};

    // Access elements
    cout << "Element at index 2: " << arr[2] << endl; // Output: 3

    // Insert an element (inefficient)
    int n = 5; // Current size of the array
    int newArr[6];
    for (int i = 0; i < n; i++) {
        newArr[i] = arr[i];
    }
    newArr[2] = 10; // Inserting 10 at index 2
    for (int i = 2; i < n; i++) {
        newArr[i + 1] = arr[i];
    }
    n++;
    cout << "Array after insertion: ";
    for (int i = 0; i < n; i++) {
        cout << newArr[i] << " ";
    }
    cout << endl;

    // Delete an element (inefficient)
    for (int i = 2; i < n - 1; i++) {
        newArr[i] = newArr[i + 1];
    }
    n--;
    cout << "Array after deletion: ";
    for (int i = 0; i < n; i++) {
        cout << newArr[i] << " ";
    }
    cout << endl;

    // Traverse the array
    cout << "Traversing the array: ";
    for (int i = 0; i < n; i++) {
        cout << newArr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

In this example:
- We declare and initialize an array.
- We access an element using its index.
- We insert a new element at a specific index, which requires shifting elements.
- We delete an element, which also requires shifting elements.
- We traverse the array and print each element.
