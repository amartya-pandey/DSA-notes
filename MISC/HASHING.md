# Hashing Notes

## 1. **Introduction to Hashing**
Hashing is a technique that involves **storing and fetching data efficiently** by mapping values to a hash table.  
It is particularly useful for solving problems like frequency counting, fast lookups, and duplicate detection.

### Key Concept:
- **Precomputation:** Store values in a hash table for quick retrieval.
- **Hash Table:** A data structure (array or map) used for hashing.

---

## 2. **Number Hashing**
### Problem:
Given an array of integers, determine the frequency of each number and answer queries about how many times specific numbers appear.

### Approach:
Use an array or map to store the frequency of each number.

### Example 1: Hashing with Arrays
#### C++ Code:
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> arr = {1, 2, 1, 3, 2};
    int max_value = *max_element(arr.begin(), arr.end()); // Find max value
    vector<int> hash_array(max_value + 1, 0); // Initialize hash array

    // Precompute frequencies
    for (int num : arr) {
        hash_array[num]++;
    }

    // Queries
    vector<int> queries = {1, 4, 2, 3};
    for (int query : queries) {
        cout << query << " appears " << hash_array[query] << " times.\n";
    }

    return 0;
}
```
#### Explanation:
1. **Find Maximum Value:** The `max_element` function determines the maximum value in the array. This is essential to size the hash array appropriately.
2. **Initialize Hash Array:** A vector of size `max_value + 1` is created to ensure it can accommodate all numbers from 0 to `max_value`.
3. **Frequency Calculation:** Each number in the input array increments its corresponding index in the hash array.
4. **Querying Frequencies:** For each query, the program retrieves the precomputed frequency from the hash array in constant time.

#### Key Points:
- **`max_element`:** Finds the maximum value in the array to determine hash array size.
- **Hash Array:** Initialized with zeros to store frequencies.
- **Queries:** Frequencies are retrieved in constant time.

**Output:**
```
1 appears 2 times.
4 appears 0 times.
2 appears 2 times.
3 appears 1 time.
```

---

### Example 2: Hashing with Maps
#### C++ Code:
```cpp
#include <iostream>
#include <unordered_map>
#include <vector>
using namespace std;

int main() {
    vector<int> arr = {1, 2, 1, 3, 2};
    unordered_map<int, int> hash_map;

    // Precompute frequencies
    for (int num : arr) {
        hash_map[num]++;
    }

    // Queries
    vector<int> queries = {1, 4, 2, 3};
    for (int query : queries) {
        cout << query << " appears " << hash_map[query] << " times.\n";
    }

    return 0;
}
```
#### Explanation:
1. **Initialize Hash Map:** An unordered map is used to dynamically store the frequency of each number.
2. **Frequency Calculation:** For each number in the input array, the value associated with the key in the hash map is incremented.
3. **Querying Frequencies:** Each query retrieves the corresponding frequency from the hash map. If a key is not present, its value defaults to 0.

#### Key Points:
- **`unordered_map`:** Efficient hash map implementation in C++.
- **Dynamic Key Addition:** Frequencies are stored directly during traversal.
- **Query Efficiency:** Average \(O(1)\) retrieval for hash maps.

**Output:**
```
1 appears 2 times.
4 appears 0 times.
2 appears 2 times.
3 appears 1 time.
```

---

## 3. **Character Hashing**
### Problem:
Given a string, find the frequency of characters and answer queries about their occurrences.

### Approach:
Use an array or hash map. For lowercase letters, an array of size 26 is sufficient. Map `'a'` to index 0, `'b'` to 1, and so on.

### Example 1: Character Hashing with Arrays
#### C++ Code:
```cpp
#include <iostream>
#include <string>
#include <vector>
using namespace std;

int main() {
    string str = "abac";
    vector<int> hash_array(26, 0); // For lowercase letters

    // Precompute frequencies
    for (char c : str) {
        int index = c - 'a'; // Map 'a' to 0, 'b' to 1, ..., 'z' to 25
        hash_array[index]++;
    }

    // Queries
    vector<char> queries = {'a', 'b', 'c', 'z'};
    for (char query : queries) {
        int index = query - 'a';
        cout << query << " appears " << hash_array[index] << " times.\n";
    }

    return 0;
}
```
#### Explanation:
1. **Mapping Characters to Indices:** Each character is mapped to an index in the hash array using its ASCII value minus the ASCII value of `'a'`.
2. **Precompute Frequencies:** Each occurrence of a character increments the corresponding index in the hash array.
3. **Query Frequencies:** For each query, the frequency is retrieved from the hash array in constant time.

#### Key Points:
- **`c - 'a'`:** Maps each character to an array index.
- **Hash Array Size:** Fixed at 26 for lowercase English letters.
- **Efficient Retrieval:** Frequencies accessed in \(O(1)\).

**Output:**
```
a appears 2 times.
b appears 1 time.
c appears 1 time.
z appears 0 times.
```

---

### Example 2: Character Hashing with Maps
#### C++ Code:
```cpp
#include <iostream>
#include <unordered_map>
#include <string>
#include <vector>
using namespace std;

int main() {
    string str = "abac";
    unordered_map<char, int> hash_map;

    // Precompute frequencies
    for (char c : str) {
        hash_map[c]++;
    }

    // Queries
    vector<char> queries = {'a', 'b', 'c', 'z'};
    for (char query : queries) {
        cout << query << " appears " << hash_map[query] << " times.\n";
    }

    return 0;
}
```
#### Explanation:
1. **Dynamic Key Storage:** Each character is dynamically added to the hash map as a key, with its frequency as the value.
2. **Precompute Frequencies:** Each occurrence of a character increments its corresponding value in the hash map.
3. **Query Frequencies:** Queries check the presence of a character and return its frequency. If the character is absent, the frequency defaults to 0.

#### Key Points:
- **`unordered_map`:** Handles dynamic character frequency storage.
- **No Fixed Size:** Works for both lowercase and uppercase letters or special characters.
- **General Applicability:** Suitable for more complex scenarios.

**Output:**
```
a appears 2 times.
b appears 1 time.
c appears 1 time.
z appears 0 times.
```

---

## 4. **Time Complexity Analysis**
- **Precomputation:** \(O(n)\), where \(n\) is the size of the input array or string.
- **Query:** \(O(1)\) for both arrays and maps (on average).
- **Overall:** \(O(n + q)\), where \(q\) is the number of queries.

---

## 5. **Global vs Local Array Constraints**
### Problem:
Handling constraints with very large arrays.

### Key Points:
1. Arrays declared **inside functions** can hold up to \(10^6\) elements.
2. Arrays declared **globally** can hold up to \(10^7\) elements.
3. For inputs larger than \(10^7\), use hash maps to avoid memory limitations.

---

## 6. **ASCII Values in Character Hashing**
### Key Concept:
Characters can be mapped to integers using their ASCII values:
- `'a'` has ASCII value 97.
- `'z'` has ASCII value 122.

#### Formula:
To map a character to its corresponding array index:
```cpp
int index = character - 'a';
```

---

## 7. **Applications of Hashing**
### Common Use Cases:
1. **Number Hashing:** Frequency counting, duplicate detection, or efficient queries.
2. **Character Hashing:** String problems like anagrams, frequency counts, and pattern matching.
3. **General Hash Maps:** More flexible with key types (e.g., strings, large integers).

---

## 8. **Advanced Hashing with Maps**
Hash maps are versatile and handle large datasets or complex keys like strings.

### Example: Map for String Hashing
#### C++ Code:
```cpp
#include <iostream>
#include <unordered_map>
#include <string>
#include <vector>
using namespace std;

int main() {
    string str = "aabcc";
    unordered_map<char, int> hash_map;

    // Precompute frequencies
    for (char c : str) {
        hash_map[c]++;
    }

    // Queries
    vector<char> queries = {'a', 'b', 'c', 'd'};
    for (char query : queries) {
        cout << query << " appears " << hash_map[query] << " times.\n";
    }

    return 0;
}
```
#### Explanation:
1. **Dynamic Key Handling:** Each character is added to the hash map with its frequency as a value.
2. **Efficient Precomputation:** Each character incrementally updates its frequency during traversal.
3. **Flexible Querying:** Allows queries for any character, even if it does not exist in the input string (defaulting to 0).

#### Key Points:
- **Dynamic Key Handling:** Works with strings, characters, and numbers.
- **Scalability:** Can handle large datasets efficiently.
- **Flexibility:** Supports custom key types.

**Output:**
```
a appears 2 times.
b appears 1 time.
c appears 2 times.
d appears 0 times.
```

---

## 9. **Advantages of Hashing**
1. **Efficiency:** Hashing reduces time complexity for lookups and updates.
2. **Flexibility:** Hash maps allow keys of various types, like strings or objects.
3. **Applicability:** Used in caching, searching, and data deduplication.

---

