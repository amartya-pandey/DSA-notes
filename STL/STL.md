
---


# C++ STL Notes with Code Examples

### 1. Overview of STL
- **What is STL?**
  - STL (Standard Template Library) is a collection of pre-defined classes and functions for data structures and algorithms.
  - Key components:
    - **Containers**: Store data (e.g., vector, list, set).
    - **Iterators**: Access elements in containers.
    - **Algorithms**: Common operations like sorting or searching.
    - **Functions**: Utility functions for operations.

---

### 2. Skeleton of a C++ Code
```cpp
#include <bits/stdc++.h> // Includes all libraries
using namespace std;

int main() {
    cout << "Hello, STL!" << endl;
    return 0;
}
```
**Output**:
```
Hello, STL!
```

---

### 3. Containers

#### 3.1 Pair
- Stores two related values.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    pair<int, string> p = {1, "STL"};
    cout << "First: " << p.first << ", Second: " << p.second << endl;

    // Nested pairs
    pair<int, pair<int, int>> nested = {1, {2, 3}};
    cout << "Nested: " << nested.first << ", (" << nested.second.first << ", " << nested.second.second << ")" << endl;
    return 0;
}
```
**Output**:
```
First: 1, Second: STL
Nested: 1, (2, 3)
```

---

#### 3.2 Vector
- Dynamic array that resizes automatically.
- **Key Functions**:
  - `push_back(x)`, `emplace_back(x)`, `pop_back()`, `insert(pos, x)`, `erase(pos)`, `clear()`, `size()`.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30};
    v.push_back(40); // Add 40 to the end

    // Access elements
    for (int i : v) cout << i << " "; // Output: 10 20 30 40

    v.erase(v.begin() + 1); // Remove 20
    cout << "\nAfter erase: ";
    for (int i : v) cout << i << " "; // Output: 10 30 40

    cout << "\nSize: " << v.size() << endl; // Output: 3
    return 0;
}
```
**Output**:
```
10 20 30 40 
After erase: 10 30 40
Size: 3
```

---

#### 3.3 List
- Doubly linked list allowing fast insertions/deletions at both ends.
- **Key Functions**:
  - `push_front(x)`, `push_back(x)`, `pop_front()`, `pop_back()`.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    list<int> l = {10, 20, 30};
    l.push_front(5);  // Add 5 to the front
    l.push_back(40);  // Add 40 to the back

    for (int x : l) cout << x << " "; // Output: 5 10 20 30 40

    l.pop_front(); // Remove 5
    l.pop_back();  // Remove 40

    cout << "\nAfter pop: ";
    for (int x : l) cout << x << " "; // Output: 10 20 30
    return 0;
}
```
**Output**:
```
5 10 20 30 40 
After pop: 10 20 30
```

---

#### 3.4 Stack
- **LIFO** (Last-In-First-Out) structure.
- **Key Functions**:
  - `push(x)`, `pop()`, `top()`.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    stack<int> s;
    s.push(10);
    s.push(20);
    s.push(30);

    cout << "Top element: " << s.top() << endl; // Output: 30

    s.pop(); // Remove 30
    cout << "After pop, Top element: " << s.top() << endl; // Output: 20
    return 0;
}
```
**Output**:
```
Top element: 30
After pop, Top element: 20
```

---

#### 3.5 Queue
- **FIFO** (First-In-First-Out) structure.
- **Key Functions**:
  - `push(x)`, `pop()`, `front()`, `back()`.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    queue<int> q;
    q.push(10);
    q.push(20);
    q.push(30);

    cout << "Front: " << q.front() << ", Back: " << q.back() << endl; // Output: Front: 10, Back: 30

    q.pop(); // Remove 10
    cout << "After pop, Front: " << q.front() << endl; // Output: 20
    return 0;
}
```
**Output**:
```
Front: 10, Back: 30
After pop, Front: 20
```

---

#### 3.6 Priority Queue
- A **heap-based structure**.
  - Default: Max-Heap (largest element at the top).
  - Min-Heap can be created using:
    ```cpp
    priority_queue<int, vector<int>, greater<int>> minHeap;
    ```
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    priority_queue<int> pq;
    pq.push(10);
    pq.push(20);
    pq.push(15);

    cout << "Top element: " << pq.top() << endl; // Output: 20
    pq.pop();
    cout << "After pop, Top element: " << pq.top() << endl; // Output: 15
    return 0;
}
```
**Output**:
```
Top element: 20
After pop, Top element: 15
```

---

#### 3.7 Set
- Stores unique elements in sorted order.
- **Key Functions**:
  - `insert(x)`, `erase(x)`, `count(x)`.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    set<int> s = {10, 20, 30};
    s.insert(20); // Duplicate, won't be added
    s.insert(15); // Added in sorted order

    for (int x : s) cout << x << " "; // Output: 10 15 20 30

    s.erase(20); // Remove 20
    cout << "\nAfter erase: ";
    for (int x : s) cout << x << " "; // Output: 10 15 30
    return 0;
}
```
**Output**:
```
10 15 20 30
After erase: 10 15 30
```

---

### 4. Algorithms

#### **Sorting**
- Sort elements in a container.
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {30, 10, 20};
    sort(v.begin(), v.end()); // Ascending order
    for (int x : v) cout << x << " "; // Output: 10 20 30
    return 0;
}
```
**Output**:
```
10 20 30
```

#### **Searching**
- Binary search (container must be sorted).
- **Code Example**:
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30};
    bool found = binary_search(v.begin(), v.end(), 20);
    cout << (found ? "Found" : "Not Found") << endl; // Output: Found
    return 0;
}
```
**Output**:
```
Found
```

---

