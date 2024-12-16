
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
```python
# Array Hashing Example
arr = [1, 2, 1, 3, 2]
max_value = max(arr)  # Find the maximum number in the array
hash_array = [0] * (max_value + 1)  # Create a hash array

# Precompute frequencies
for num in arr:
    hash_array[num] += 1

# Queries
queries = [1, 4, 2, 3]
for query in queries:
    print(f"{query} appears {hash_array[query]} times.")
```

**Output:**
```
1 appears 2 times.
4 appears 0 times.
2 appears 2 times.
3 appears 1 time.
```

---

### Example 2: Hashing with Maps
```python
# Hash Map Example
arr = [1, 2, 1, 3, 2]
hash_map = {}

# Precompute frequencies
for num in arr:
    hash_map[num] = hash_map.get(num, 0) + 1

# Queries
queries = [1, 4, 2, 3]
for query in queries:
    print(f"{query} appears {hash_map.get(query, 0)} times.")
```

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
```python
# Character Hashing Example
string = "abac"
hash_array = [0] * 26  # For lowercase letters

# Precompute frequencies
for char in string:
    index = ord(char) - ord('a')  # Map 'a' to 0, 'b' to 1, ..., 'z' to 25
    hash_array[index] += 1

# Queries
queries = ['a', 'b', 'c', 'z']
for query in queries:
    index = ord(query) - ord('a')
    print(f"{query} appears {hash_array[index]} times.")
```

**Output:**
```
a appears 2 times.
b appears 1 time.
c appears 1 time.
z appears 0 times.
```

---

### Example 2: Character Hashing with Maps
```python
# Character Hashing Using Hash Map
string = "abac"
hash_map = {}

# Precompute frequencies
for char in string:
    hash_map[char] = hash_map.get(char, 0) + 1

# Queries
queries = ['a', 'b', 'c', 'z']
for query in queries:
    print(f"{query} appears {hash_map.get(query, 0)} times.")
```

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
```
index = ord(character) - ord('a')
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
```python
# String Hashing Using Map
string = "aabcc"
hash_map = {}

# Precompute frequencies
for char in string:
    hash_map[char] = hash_map.get(char, 0) + 1

# Queries
queries = ['a', 'b', 'c', 'd']
for query in queries:
    print(f"{query} appears {hash_map.get(query, 0)} times.")
```

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