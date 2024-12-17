# QUICK SORT DSA Notes

### **What is Quick Sort?**
Quick Sort is a **divide-and-conquer** algorithm that sorts an array efficiently. It works by repeatedly partitioning the array around a selected pivot element. After placing the pivot in its correct position, the array is divided into two subarrays:
1. Elements smaller than the pivot (to the left).
2. Elements larger than the pivot (to the right).

The process is repeated recursively for each subarray until the entire array is sorted.

---
### Features of Quick Sort
1. **Time Complexity**:  
   - **Best and Average Case**: \(O\(n log n)\)  
   - **Worst Case**: \(O(n^2)\) (occurs when the pivot is the smallest or largest element repeatedly).  
2. **Space Complexity**: \(O(log n)\) (due to recursion stack).  
3. **In-place Sorting**: Quick Sort does not use additional memory for sorting the array.

---

### **Steps of Quick Sort**

#### 1. **Choosing the Pivot**
The pivot is an element used to partition the array. In our implementation:
- We choose the **first element** as the pivot (`arr[low]`).
- Other strategies for choosing a pivot:
  - Last element.
  - Median element.
  - Random element.

---

#### 2. **Partitioning the Array**
The partition function rearranges the array such that:
- All elements smaller than or equal to the pivot are placed on its left.
- All elements greater than the pivot are placed on its right.
- Finally, the pivot is placed in its correct position in the sorted array.

**Partition Logic**:
1. **Two Pointers**:
   - `i` starts from the second element (`low + 1`).
   - `j` starts from the last element (`high`).
2. **Move Pointers**:
   - Move `i` until you find an element greater than the pivot.
   - Move `j` until you find an element smaller than or equal to the pivot.
3. **Swap**:
   - Swap the elements at `i` and `j` if `i < j`.
4. **Stop Swapping**:
   - Stop when `i` and `j` cross.
5. **Place Pivot**:
   - Swap the pivot with the element at `j`. This ensures the pivot is in its correct position.

**Code**:
```cpp
int partition(vector<int> &arr, int low, int high) {
    int pivot = arr[low]; // Choosing the first element as the pivot
    int i = low + 1;      // Pointer for left
    int j = high;         // Pointer for right

    while (i <= j) {
        while (i <= j && arr[i] <= pivot) i++; // Find element > pivot
        while (i <= j && arr[j] > pivot) j--; // Find element <= pivot
        if (i < j) swap(arr[i], arr[j]);      // Swap if valid
    }

    // Place the pivot in its correct position
    swap(arr[low], arr[j]);
    return j; // Return the pivot index
}
```

---

#### 3. **Recursive Sorting**
After partitioning, two recursive calls are made:
1. Quick Sort the left subarray (`low` to `pivotIndex - 1`).
2. Quick Sort the right subarray (`pivotIndex + 1` to `high`).

**Code**:
```cpp
void quickSort(vector<int> &arr, int low, int high) {
    if (low < high) { // Base condition: at least 2 elements
        int pivotIndex = partition(arr, low, high); // Partition the array
        quickSort(arr, low, pivotIndex - 1);        // Sort left half
        quickSort(arr, pivotIndex + 1, high);      // Sort right half
    }
}
```

---

### **Full Example Walkthrough**

**Input Array**: `{6, 3, 8, 5, 2, 7, 4, 1}`  

1. **First Partition**:
   - Pivot: `6`.
   - Rearrange: After swapping, the array becomes: `{4, 3, 1, 5, 2, 6, 7, 8}`.
   - Pivot position: Index `5`.

2. **Left Subarray**: `{4, 3, 1, 5, 2}`  
   - Pivot: `4`.
   - Rearrange: After swapping: `{2, 3, 1, 4, 5}`.
   - Pivot position: Index `3`.

3. **Right Subarray**: `{7, 8}`  
   - Pivot: `7`.
   - Rearrange: `{7, 8}` (already sorted).
   - Pivot position: Index `6`.

4. **Recursively Sort Subarrays**:
   - Left Subarray of `{4, 3, 1, 5, 2}`: `{2, 3, 1}` and `{5}`.
   - Repeat the process until the array is fully sorted.

**Final Output**: `{1, 2, 3, 4, 5, 6, 7, 8}`.

---

### **Why Quick Sort is Efficient**
1. **Divide-and-Conquer**:
   - Splits the problem into smaller, independent subproblems.
2. **In-place Sorting**:
   - Requires no additional memory for temporary arrays.
3. **Efficient on Average**:
   - \(O(n \log n)\) in most cases, faster than Merge Sort due to no copying of arrays.

---

### **Advantages**
- Simple and fast for large datasets.
- Space-efficient due to in-place sorting.

### **Disadvantages**
- Worst-case time complexity of \(O(n^2)\), which occurs when:
  - The pivot is repeatedly chosen poorly, e.g., smallest or largest element in sorted or reverse-sorted arrays.

---

### **Run the Full C++ Code**
```cpp
#include <iostream>
#include <vector>
using namespace std;

// Partition function
int partition(vector<int> &arr, int low, int high) {
    int pivot = arr[low];
    int i = low + 1, j = high;

    while (i <= j) {
        while (i <= j && arr[i] <= pivot) i++;
        while (i <= j && arr[j] > pivot) j--;
        if (i < j) swap(arr[i], arr[j]);
    }
    swap(arr[low], arr[j]);
    return j;
}

// Quick Sort function
void quickSort(vector<int> &arr, int low, int high) {
    if (low < high) {
        int pivotIndex = partition(arr, low, high);
        quickSort(arr, low, pivotIndex - 1);
        quickSort(arr, pivotIndex + 1, high);
    }
}

// Main function
int main() {
    vector<int> arr = {6, 3, 8, 5, 2, 7, 4, 1};

    cout << "Original Array: ";
    for (int num : arr) cout << num << " ";
    cout << endl;

    quickSort(arr, 0, arr.size() - 1);

    cout << "Sorted Array: ";
    for (int num : arr) cout << num << " ";
    cout << endl;

    return 0;
}
```

---

### **Output**
```plaintext
Original Array: 6 3 8 5 2 7 4 1
Sorted Array: 1 2 3 4 5 6 7 8
```

---

## Key Observations
1. **Pivot Selection**:
   - This implementation uses the first element as the pivot.
   - Pivot selection affects the performance. Other strategies include:
     - Picking the last element.
     - Picking a random element.
     - Choosing the median.

2. **Stability**: Quick Sort is not stable by default because it swaps elements.

3. **In-place Sorting**: Quick Sort sorts the array without additional memory, making it space-efficient.

---

## Assignment
Write the Quick Sort algorithm to sort an array in **descending order**. Replace the comparison logic in the `partition` function to ensure larger elements are on the left.

**Hint**: Change `<=` to `>=` in the partitioning logic.

--- 