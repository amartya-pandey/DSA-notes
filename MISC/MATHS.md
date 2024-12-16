# Basic Maths for DSA Notes

## 1. **Extraction of Digits**
### Explanation
This technique is used to **break down a number into its individual digits**. By repeatedly applying modulus (`%`) and integer division (`//`), we can extract digits from the least significant (rightmost) to the most significant (leftmost).

### Process:
1. Use `n % 10` to extract the last digit of the number.
2. Use `n // 10` to remove the last digit from the number.
3. Repeat until the number becomes 0.

**Example Use Case:** Checking properties like palindrome numbers or Armstrong numbers.


### Code
```python
# Python Example
n = 7789
while n > 0:
    digit = n % 10
    print(digit, end=" ")  # Prints digits in reverse order
    n //= 10
```

### Output
```
9 8 7 7
```

---

## 2. **Counting Digits**
### Explanation
Counting the number of digits in a number is essential in problems like determining the length of a number or for digit-based comparisons.

### Process:
1. Repeatedly divide the number by 10 (`n //= 10`).
2. Keep a counter to track the number of divisions.

**Example Use Case:** In identifying the number of digits to perform operations like radix sort or digit summation.

### Code
```python
# Python Example
n = 156
count = 0
while n > 0:
    n //= 10
    count += 1
print("Number of digits:", count)
```

### Output
```
Number of digits: 3
```

---

## 3. **Reversing a Number**
### Explanation
Reversing a number is common in problems like determining if a number is a palindrome or reordering digits for other computations.

### Process:
1. Extract the last digit using `n % 10`.
2. Append it to a new number (`reverse = reverse * 10 + digit`).
3. Remove the last digit (`n //= 10`) and repeat.

**Example Use Case:** Useful for problems involving digit manipulation or palindrome checking.
### Code
```python
# Python Example
n = 7789
reverse = 0
while n > 0:
    digit = n % 10
    reverse = reverse * 10 + digit
    n //= 10
print("Reversed Number:", reverse)
```

### Output
```
Reversed Number: 9877
```

---

## 4. **Palindrome Check**
### Explanation
A **palindrome number** reads the same forward and backward (e.g., 121, 1331). To check:
1. Reverse the number.
2. Compare the reversed number with the original.

**Example Use Case:** Identifying palindromic numbers in sequences or solving related problems.

### Code
```python
# Python Example
n = 121
original = n
reverse = 0
while n > 0:
    digit = n % 10
    reverse = reverse * 10 + digit
    n //= 10
print("Palindrome:", original == reverse)
```

### Output
```
Palindrome: True
```

---

## 5. **Armstrong Numbers**
### Explanation
An **Armstrong number** is a number equal to the sum of the cubes of its digits. For example, \(371 = 3^3 + 7^3 + 1^3\).

### Process:
1. Extract each digit.
2. Compute the cube of the digit and sum it up.
3. Compare the sum with the original number.

**Example Use Case:** Used in coding puzzles and algorithmic challenges.

### Code
```python
# Python Example
n = 371
original = n
sum_of_cubes = 0
while n > 0:
    digit = n % 10
    sum_of_cubes += digit ** 3
    n //= 10
print("Armstrong:", original == sum_of_cubes)
```

### Output
```
Armstrong: True
```

---

## 6. **Finding Divisors**
### Explanation
Divisors of a number are integers that divide the number completely (no remainder). For example, divisors of 36 are \(1, 2, 3, 4, 6, 9, 12, 18, 36\).

### Process:
1. Iterate from \(1\) to \(\sqrt{n}\).
2. Check divisibility using `n % i == 0`.
3. Add both \(i\) and \(n/i\) if they are divisors.

**Example Use Case:** Efficient divisor calculation for problems in number theory or optimization.

### Code
```python
# Python Example
n = 36
divisors = []
for i in range(1, int(n ** 0.5) + 1):
    if n % i == 0:
        divisors.append(i)
        if i != n // i:
            divisors.append(n // i)
divisors.sort()
print("Divisors:", divisors)
```

### Output
```
Divisors: [1, 2, 3, 4, 6, 9, 12, 18, 36]
```

---

## 7. **Prime Number Check**
### Explanation
A **prime number** is a number greater than 1 with no divisors other than 1 and itself. For example, 2, 3, 5, 7 are primes.

### Process:
1. Iterate from 2 to \(\sqrt{n}\).
2. If any number divides \(n\), it is not a prime.
3. Otherwise, it is a prime number.

**Example Use Case:** Key in cryptographic algorithms, primality tests, and sieve algorithms.

### Code
```python
# Python Example
n = 29
is_prime = True
if n < 2:
    is_prime = False
else:
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            is_prime = False
            break
print("Prime:", is_prime)
```

### Output
```
Prime: True
```

---
### Why These Topics Are Important
- These operations form the **building blocks** for more complex DSA concepts like modular arithmetic, hash functions, and digit-based algorithms.
- They **optimize algorithms** for tasks involving number manipulation, such as checking properties or solving mathematical problems efficiently.