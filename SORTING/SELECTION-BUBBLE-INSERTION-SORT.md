# Sorting Algorithms Notes

## 1. **Selection Sort**
### Key Idea:
Selection Sort works by finding the **minimum element** from the unsorted portion of the array and swapping it with the **first element** of the unsorted portion. This process is repeated until the entire array is sorted.

- **Steps:**
  1. Iterate over the array.
  2. For each position, find the smallest element in the remaining unsorted part.
  3. Swap the smallest element with the current position.

- **Example:**
  Given the array `[64, 25, 12, 22, 11]`:
  - Find the smallest element (`11`) and swap it with `64`.
  - Then find the next smallest (`12`) and swap it with `25`.
  - Repeat until sorted.

- **Time Complexity:**
  - Best, Worst, and Average Case: \(O(n^2)\) because it involves nested loops to find the minimum and swap elements.

- **Space Complexity:**
  \(O(1)\), as it sorts the array in place without additional memory.
---

### Code
```python
# Selection Sort Implementation
def selection_sort(arr):
    n = len(arr)
    for i in range(n - 1):
        # Find the index of the minimum element in the unsorted portion
        min_index = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        # Swap the found minimum with the first element of the unsorted portion
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr

# Example Usage
array = [64, 25, 12, 22, 11]
print("Sorted Array:", selection_sort(array))
```

### Output
```
Sorted Array: [11, 12, 22, 25, 64]
```

---

## 2. **Bubble Sort**
### Key Idea:
Bubble Sort **compares adjacent elements** and swaps them if they are in the wrong order. The largest element "bubbles" to its correct position after each pass.

- **Steps:**
  1. Compare two adjacent elements.
  2. Swap them if they are out of order.
  3. After each complete pass, ignore the last element since it is already sorted.

- **Optimization:**
  If no swaps occur during a pass, the array is already sorted, and the algorithm can stop early. This gives it a **best-case time complexity of \(O(n)\)** for sorted arrays.

- **Example:**
  Given the array `[64, 34, 25, 12, 22, 11, 90]`:
  - After the first pass, `90` moves to its correct position.
  - Continue passes until all elements are sorted.

- **Time Complexity:**
  - Best Case: \(O(n)\) (optimized for already sorted arrays).
  - Worst and Average Case: \(O(n^2)\) due to nested loops.

- **Space Complexity:**
  \(O(1)\), as it also sorts the array in place.

---

### Code
```python
# Bubble Sort Implementation
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(n - i - 1):
            if arr[j] > arr[j + 1]:
                # Swap adjacent elements if they are in the wrong order
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        # Break if no elements were swapped, indicating the array is sorted
        if not swapped:
            break
    return arr

# Example Usage
array = [64, 34, 25, 12, 22, 11, 90]
print("Sorted Array:", bubble_sort(array))
```

### Output
```
Sorted Array: [11, 12, 22, 25, 34, 64, 90]
```

---

## 3. **Insertion Sort**
### Key Idea:
Insertion Sort treats the array as two parts: **sorted** and **unsorted**. It **picks the next element** from the unsorted portion and inserts it in its correct position in the sorted portion.

- **Steps:**
  1. Start with the first element, which is trivially sorted.
  2. Pick the next element.
  3. Shift elements in the sorted portion to the right until the correct position for the new element is found.
  4. Insert the element and repeat.

- **Example:**
  Given the array `[12, 11, 13, 5, 6]`:
  - Start with `[12]` (sorted).
  - Insert `11`, resulting in `[11, 12]`.
  - Then insert `13`, `[11, 12, 13]`.
  - Continue until sorted.

- **Time Complexity:**
  - Best Case: \(O(n)\) for already sorted arrays.
  - Worst and Average Case: \(O(n^2)\) due to nested iterations.

- **Space Complexity:**
  \(O(1)\), as it sorts in place.

---

### Code
```python
# Insertion Sort Implementation
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        # Move elements of the sorted portion that are greater than the key
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

# Example Usage
array = [12, 11, 13, 5, 6]
print("Sorted Array:", insertion_sort(array))
```

### Output
```
Sorted Array: [5, 6, 11, 12, 13]
```

---

## Summary Table of Sorting Algorithms

| Algorithm        | Best Time Complexity | Worst Time Complexity | Average Time Complexity | Space Complexity |
|-------------------|-----------------------|------------------------|--------------------------|-------------------|
| Selection Sort    | \(O(n^2)\)           | \(O(n^2)\)            | \(O(n^2)\)              | \(O(1)\)          |
| Bubble Sort       | \(O(n)\) (optimized) | \(O(n^2)\)            | \(O(n^2)\)              | \(O(1)\)          |
| Insertion Sort    | \(O(n)\)             | \(O(n^2)\)            | \(O(n^2)\)              | \(O(1)\)          |

---

This markdown file contains comprehensive notes with detailed explanations, examples, and outputs. Let me know if you need anything else!