
# Recursion Notes - Full Revision

## 1. **Introduction to Recursion**

### Definition:
When a function calls itself, it is known as **recursion**. Recursion continues until a **specified condition** is met, known as the **base case**.

### Key Concepts:
1. **Recursive Function**: A function that calls itself.
2. **Base Case**: Condition to stop the recursion and avoid an infinite loop.
3. **Stack Overflow**: If no base case is defined, recursion continues infinitely and leads to a stack overflow.

---

### **Example 1: Infinite Recursion**

#### Code:
```cpp
#include <iostream>
using namespace std;

void printOne() {
    cout << "1" << endl;
    printOne(); // Recursive call with no base case
}

int main() {
    printOne();
    return 0;
}
```

#### Output:
```
1
1
1
...
Segmentation fault (Stack Overflow)
```

#### Explanation:
- The function `printOne` keeps calling itself infinitely because there is no **base case**.
- This leads to a **stack overflow error** when memory is exhausted.

---

### **Example 2: Corrected Recursion with Base Case**

#### Code:
```cpp
#include <iostream>
using namespace std;

void printOne(int count) {
    if (count == 0) return; // Base case
    cout << "1" << endl;
    printOne(count - 1); // Recursive call with decrement
}

int main() {
    int n = 5; // Number of times to print 1
    printOne(n);
    return 0;
}
```

#### Output:
```
1
1
1
1
1
```

#### Explanation:
- The function now includes a **base case** (`if (count == 0) return`).
- Recursion stops after `n` calls.

---

## 2. **Problems on Recursion**

### **Example 3: Print Name N Times**

#### Code:
```cpp
#include <iostream>
using namespace std;

void printName(int i, int n) {
    if (i > n) return; // Base case
    cout << "Raj" << endl;
    printName(i + 1, n); // Recursive call
}

int main() {
    int n;
    cout << "Enter the number of times to print name: ";
    cin >> n;
    printName(1, n);
    return 0;
}
```

#### Input:
```
3
```

#### Output:
```
Raj
Raj
Raj
```

#### Explanation:
- A simple recursion where the base case stops when `i > n`.
- `printName` prints "Raj" `n` times.

---

### **Example 4: Sum of First N Numbers**

#### Code:
```cpp
#include <iostream>
using namespace std;

void sumN(int i, int sum) {
    if (i < 1) { // Base case
        cout << "Sum: " << sum << endl;
        return;
    }
    sumN(i - 1, sum + i); // Recursive call
}

int main() {
    int n;
    cout << "Enter the number: ";
    cin >> n;
    sumN(n, 0);
    return 0;
}
```

#### Input:
```
3
```

#### Output:
```
Sum: 6
```

#### Explanation:
- This is **parameterized recursion** where `sum` carries the cumulative value.
- Base case stops when `i` becomes less than 1.

---

## 3. **Functional Recursion**

### **Example 5: Sum of First N Numbers - Functional Style**

#### Code:
```cpp
#include <iostream>
using namespace std;

int sumN(int n) {
    if (n == 0) return 0; // Base case
    return n + sumN(n - 1); // Recursive call
}

int main() {
    int n;
    cout << "Enter the number: ";
    cin >> n;
    cout << "Sum: " << sumN(n) << endl;
    return 0;
}
```

#### Input:
```
3
```

#### Output:
```
Sum: 6
```

#### Explanation:
- Instead of carrying a parameter, the function **returns** the sum directly.
- Recursion adds `n` to the result of `sumN(n-1)`.

---

## 4. **Reversing an Array Using Recursion**

### **Example 6: Reverse Array Using Two Pointers**

#### Code:
```cpp
#include <iostream>
using namespace std;

void reverseArray(int arr[], int l, int r) {
    if (l >= r) return; // Base case
    swap(arr[l], arr[r]); // Swap elements
    reverseArray(arr, l + 1, r - 1); // Recursive call
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original Array: ";
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;

    reverseArray(arr, 0, n - 1);

    cout << "Reversed Array: ";
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    cout << endl;

    return 0;
}
```

#### Output:
```
Original Array: 1 2 3 4 5
Reversed Array: 5 4 3 2 1
```

#### Explanation:
- Recursion swaps the first and last elements and moves pointers inward until they meet.

---

## 5. **Fibonacci Series Using Recursion**

### **Example 7: Find the Nth Fibonacci Number**

#### Code:
```cpp
#include <iostream>
using namespace std;

int fibonacci(int n) {
    if (n <= 1) return n; // Base case
    return fibonacci(n - 1) + fibonacci(n - 2); // Recursive call
}

int main() {
    int n;
    cout << "Enter the position: ";
    cin >> n;
    cout << "Fibonacci Number: " << fibonacci(n) << endl;
    return 0;
}
```

#### Input:
```
5
```

#### Output:
```
Fibonacci Number: 5
```

#### Explanation:
- The function finds the `nth` Fibonacci number using **multiple recursive calls**.

---

## 6. **Recursion Tree and Space Complexity**

### Key Concepts:
1. **Recursion Tree**: A visual representation of recursive calls.
   - Each node represents a function call.
   - Helps understand the flow of recursion.
2. **Time Complexity**: 
   - If a function calls itself `n` times, time complexity is **O(n)**.
3. **Space Complexity**: 
   - Depends on the **depth of the recursion stack**. For linear recursion, it is **O(n)**.

---

## Summary Table

| **Problem**                        | **Code**                            | **Output**                        |
|------------------------------------|-------------------------------------|-----------------------------------|
| Infinite Recursion                 | Example 1                           | Stack Overflow                    |
| Print Name N Times                 | Example 3                           | Name printed `n` times            |
| Sum of First N Numbers             | Example 4, 5                        | Sum of numbers                    |
| Reverse Array                      | Example 6                           | Reversed array                    |
| Fibonacci Nth Number               | Example 7                           | Nth Fibonacci number              |

---
