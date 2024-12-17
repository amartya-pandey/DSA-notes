# Implementations of recursion
The following examples showcase the versatility of recursive techniques. Recursion is not limited to simple problems like sum, Fibonacci, or reversing an array. Below are some **advanced and common recursive implementations** with their code, outputs, and explanations.

These examples demonstrate **different implementations of recursion** for:
1. Factorials
2. Exponentiation
3. Subsequences
4. Tower of Hanoi
5. Permutations
6. Palindrome check
---

## **1. Factorial of a Number**

### Concept:
The factorial of a number `n` is defined as:
\[
n! = n \times (n-1) \times (n-2) \dots 1
\]
Base case: `0! = 1`.

### Code:
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0 || n == 1) return 1; // Base case
    return n * factorial(n - 1); // Recursive call
}

int main() {
    int n;
    cout << "Enter a number: ";
    cin >> n;
    cout << "Factorial of " << n << " is: " << factorial(n) << endl;
    return 0;
}
```

### Input:
```
5
```

### Output:
```
Factorial of 5 is: 120
```

### Explanation:
- The function recursively multiplies `n` with the result of `factorial(n-1)`.
- When `n` reaches `0` or `1`, recursion terminates with `1` as the base case.

---

## **2. Power of a Number (Exponentiation)**

### Concept:
The power of a number `a` raised to `b` is:
\[
a^b = a \times a^{b-1} \quad (b > 0)
\]
Base case: `a^0 = 1`.

### Code:
```cpp
#include <iostream>
using namespace std;

int power(int a, int b) {
    if (b == 0) return 1; // Base case: anything to the power 0 is 1
    return a * power(a, b - 1); // Recursive call
}

int main() {
    int a, b;
    cout << "Enter base and exponent: ";
    cin >> a >> b;
    cout << a << "^" << b << " = " << power(a, b) << endl;
    return 0;
}
```

### Input:
```
2 4
```

### Output:
```
2^4 = 16
```

### Explanation:
- The function recursively multiplies `a` by `power(a, b-1)`.
- When `b == 0`, recursion terminates with `1` as the base case.

---

## **3. Print All Subsequences of a String**

### Concept:
A subsequence of a string is any combination of characters that maintain the relative order of the original string. For example:
- For "abc", the subsequences are: `"", "a", "b", "c", "ab", "ac", "bc", "abc"`.

### Code:
```cpp
#include <iostream>
using namespace std;

void printSubsequences(string str, string output, int index) {
    if (index == str.size()) { // Base case: end of string
        cout << output << endl;
        return;
    }
    
    // Include current character
    printSubsequences(str, output + str[index], index + 1);
    // Exclude current character
    printSubsequences(str, output, index + 1);
}

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;
    cout << "All Subsequences of \"" << str << "\":" << endl;
    printSubsequences(str, "", 0);
    return 0;
}
```

### Input:
```
abc
```

### Output:
```
All Subsequences of "abc":
abc
ab
ac
a
bc
b
c
```

### Explanation:
- At each character in the string:
   - Include the character in the output.
   - Exclude the character from the output.
- The recursion tree explores all possibilities for subsequences.

---

## **4. Tower of Hanoi Problem**

### Concept:
The Tower of Hanoi is a mathematical puzzle where you need to move `n` disks from **Source** to **Destination** using an **Auxiliary** rod. The rules are:
1. Only one disk can be moved at a time.
2. A larger disk cannot be placed on top of a smaller disk.

### Code:
```cpp
#include <iostream>
using namespace std;

void towerOfHanoi(int n, char source, char destination, char auxiliary) {
    if (n == 1) {
        cout << "Move disk 1 from " << source << " to " << destination << endl;
        return;
    }
    // Move n-1 disks from source to auxiliary using destination as buffer
    towerOfHanoi(n - 1, source, auxiliary, destination);
    cout << "Move disk " << n << " from " << source << " to " << destination << endl;
    // Move n-1 disks from auxiliary to destination using source as buffer
    towerOfHanoi(n - 1, auxiliary, destination, source);
}

int main() {
    int n;
    cout << "Enter the number of disks: ";
    cin >> n;
    towerOfHanoi(n, 'A', 'C', 'B');
    return 0;
}
```

### Input:
```
3
```

### Output:
```
Move disk 1 from A to C
Move disk 2 from A to B
Move disk 1 from C to B
Move disk 3 from A to C
Move disk 1 from B to A
Move disk 2 from B to C
Move disk 1 from A to C
```

### Explanation:
- The problem divides into smaller subproblems of moving `n-1` disks.
- The recursive steps:
   1. Move `n-1` disks from Source to Auxiliary.
   2. Move the largest disk to Destination.
   3. Move `n-1` disks from Auxiliary to Destination.

---

## **5. Generate Permutations of a String**

### Concept:
Permutations of a string are all possible arrangements of its characters. For example:
- For "abc", permutations are: `abc, acb, bac, bca, cab, cba`.

### Code:
```cpp
#include <iostream>
using namespace std;

void generatePermutations(string &str, int index) {
    if (index == str.size()) {
        cout << str << endl; // Base case: print when a permutation is formed
        return;
    }

    for (int i = index; i < str.size(); i++) {
        swap(str[index], str[i]); // Swap characters
        generatePermutations(str, index + 1); // Recursive call
        swap(str[index], str[i]); // Backtrack
    }
}

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;
    cout << "Permutations of \"" << str << "\":" << endl;
    generatePermutations(str, 0);
    return 0;
}
```

### Input:
```
abc
```

### Output:
```
Permutations of "abc":
abc
acb
bac
bca
cab
cba
```

### Explanation:
- The recursion swaps each character and explores all possibilities.
- **Backtracking** ensures the original string is restored after each recursion.

---

## **6. Check Palindrome Using Recursion**

### Concept:
A string is a palindrome if it reads the same backward as forward.

### Code:
```cpp
#include <iostream>
using namespace std;

bool isPalindrome(string str, int l, int r) {
    if (l >= r) return true; // Base case
    if (str[l] != str[r]) return false; // If mismatch found
    return isPalindrome(str, l + 1, r - 1); // Recursive call
}

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;
    if (isPalindrome(str, 0, str.size() - 1))
        cout << str << " is a palindrome." << endl;
    else
        cout << str << " is not a palindrome." << endl;
    return 0;
}
```

### Input:
```
madam
```

### Output:
```
madam is a palindrome.
```

### Explanation:
- The recursion checks the characters at the two ends and moves inward.

---

These problems showcase both **linear** and **tree-based recursion** with clear base cases and recursive steps.