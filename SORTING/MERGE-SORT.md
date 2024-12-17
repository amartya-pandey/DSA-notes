# Merge Sort Notes

## Overview
**Merge Sort** is a **divide-and-conquer** sorting algorithm that:
1. **Divides** the array into two halves recursively until each half contains a single element.
2. **Merges** these halves back in sorted order.

---

## Features of Merge Sort
1. **Time Complexity**:
   - **Best, Worst, and Average Case**: \(O(n \log n)\)
   - Merge Sort consistently maintains \(O(n \log n)\) for all input cases due to its division and merging.
2. **Space Complexity**: \(O(n)\) (for the temporary array used in merging).
3. **Stable Sorting Algorithm**: Retains the relative order of equal elements.
4. **Non-In-Place Sorting**: Uses additional memory for merging.

---

## Algorithm Steps

### Step 1: Recursive Division
Divide the array into two halves until each half contains one or zero elements.

**Code Example**:
```cpp
void mergeSort(vector<int> &arr, int low, int high) {
    if (low >= high) return; // Base case: single element or empty

    int mid = low + (high - low) / 2; // Find the middle point
    mergeSort(arr, low, mid);         // Recursively sort the left half
    mergeSort(arr, mid + 1, high);    // Recursively sort the right half
    merge(arr, low, mid, high);       // Merge the two sorted halves
}
```

---

### Step 2: Merging Two Sorted Arrays
The merge operation combines two sorted subarrays into a single sorted array.

**Code Example**:
```cpp
void merge(vector<int> &arr, int low, int mid, int high) {
    vector<int> temp; // Temporary array to store sorted elements
    int left = low, right = mid + 1;

    // Compare elements from both halves and insert the smaller one
    while (left <= mid && right <= high) {
        if (arr[left] <= arr[right]) {
            temp.push_back(arr[left++]);
        } else {
            temp.push_back(arr[right++]);
        }
    }

    // Add remaining elements from the left half
    while (left <= mid) temp.push_back(arr[left++]);

    // Add remaining elements from the right half
    while (right <= high) temp.push_back(arr[right++]);

    // Copy the sorted elements back to the original array
    for (int i = low; i <= high; ++i) {
        arr[i] = temp[i - low];
    }
}
```

---

### Step 3: Full Implementation
Here’s the complete implementation of Merge Sort in C++.

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Merge function
void merge(vector<int> &arr, int low, int mid, int high) {
    vector<int> temp; // Temporary array
    int left = low, right = mid + 1;

    while (left <= mid && right <= high) {
        if (arr[left] <= arr[right]) {
            temp.push_back(arr[left++]);
        } else {
            temp.push_back(arr[right++]);
        }
    }

    while (left <= mid) temp.push_back(arr[left++]);
    while (right <= high) temp.push_back(arr[right++]);

    for (int i = low; i <= high; ++i) {
        arr[i] = temp[i - low];
    }
}

// Merge Sort function
void mergeSort(vector<int> &arr, int low, int high) {
    if (low >= high) return; // Base case

    int mid = low + (high - low) / 2;
    mergeSort(arr, low, mid);      // Sort left half
    mergeSort(arr, mid + 1, high); // Sort right half
    merge(arr, low, mid, high);    // Merge sorted halves
}

// Main function
int main() {
    vector<int> arr = {9, 5, 2, 7, 1, 6, 3, 8};
    cout << "Original Array: ";
    for (int num : arr) cout << num << " ";
    cout << endl;

    mergeSort(arr, 0, arr.size() - 1);

    cout << "Sorted Array: ";
    for (int num : arr) cout << num << " ";
    cout << endl;

    return 0;
}
```

---

## Example Execution
**Input**:  
Original Array: `9 5 2 7 1 6 3 8`

**Output**:  
Sorted Array: `1 2 3 5 6 7 8 9`

---

### Explanation of Key Components
1. **Recursive Nature**:
   - The array is divided recursively into two halves until each half contains one element.
   - Example:
     ```
     Divide: [9, 5, 2, 7, 1, 6, 3, 8]
     -> [9, 5, 2, 7] and [1, 6, 3, 8]
     -> [9, 5] and [2, 7] ... (continues)
     ```

2. **Merge Operation**:
   - Combines two sorted subarrays into one sorted array.
   - Example:  
     ```
     Left: [2, 7], Right: [1, 6]
     Merged: [1, 2, 6, 7]
     ```

3. **Space Usage**:
   - Temporary arrays are used to hold the merged results before copying them back into the original array.

---

## Assignment
Implement Merge Sort to sort an array in **descending order**. Modify the `merge` function to prioritize larger elements first during the merge step.

**Hint**: Reverse the comparison in the condition:  
```cpp
if (arr[left] >= arr[right]) { ... }
```
