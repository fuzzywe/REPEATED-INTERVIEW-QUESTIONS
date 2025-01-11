 Find square root of an integer
You are given a positive integer ‘N’. Your task is to find and return its square root. If ‘N’ is not a perfect square, then return the floor value of sqrt(N).

Here are the **brute-force**, **better**, and **optimal** solutions for finding the square root of an integer \(N\) in **C++**:

### **1. Brute Force Solution**  
**Approach:**
- Increment `i` starting from `1` until `i * i > N`.  
- The largest `i` for which `i * i <= N` is the floor of the square root.

```cpp
#include <iostream>
using namespace std;

int squareRootBrute(int N) {
    int i = 1;
    while (i * i <= N) {
        i++;
    }
    return i - 1;
}

int main() {
    cout << squareRootBrute(16) << endl;  // Output: 4
    cout << squareRootBrute(10) << endl;  // Output: 3
    return 0;
}
```

---

### **2. Better Solution (Binary Search)**  
**Approach:**
- Apply binary search between `1` and `N / 2`.  
- Update `mid` and adjust the range based on the condition `mid * mid <= N`.

```cpp
#include <iostream>
using namespace std;

int squareRootBinarySearch(int N) {
    if (N == 0 || N == 1) return N;
    int low = 1, high = N, ans = 0;
    
    while (low <= high) {
        long long mid = low + (high - low) / 2;
        if (mid * mid == N)
            return mid;
        else if (mid * mid < N) {
            ans = mid;
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return ans;
}

int main() {
    cout << squareRootBinarySearch(16) << endl;  // Output: 4
    cout << squareRootBinarySearch(10) << endl;  // Output: 3
    return 0;
}
```

---

### **3. Optimal Solution (Newton-Raphson Method)**  
**Approach:**  
- Start with an initial guess and iteratively improve the approximation.  
- `x = (x + N / x) / 2` until convergence.

```cpp
#include <iostream>
using namespace std;

int squareRootNewton(int N) {
    double x = N;
    double root;
    while (true) {
        root = 0.5 * (x + N / x);
        if (abs(root - x) < 1) break;
        x = root;
    }
    return (int)root;
}

int main() {
    cout << squareRootNewton(16) << endl;  // Output: 4
    cout << squareRootNewton(10) << endl;  // Output: 3
    return 0;
}
```

### **Websites for Practice**
1. **LeetCode** – [Sqrt(x)](https://leetcode.com/problems/sqrtx/)
2. **GeeksforGeeks** – [Floor square root of a number](https://practice.geeksforgeeks.org/problems/square-root/0)
3. **Codeforces** – Search for square root problems in their archive.
4. 
---

Q4. Implement strstr() function in C
You are given two strings A and B. Find the index of the first occurrence of A in B. If A is not present in B, then return -1.
For Example:
A = “bc”, B = “abcddbc”. String “A” is present at index 1, and 5(0-based index), but we will return 1 as it is the first occurrence of “A” in string “B”.
Here's how you can implement the `strstr()` function in **C** to find the index of the first occurrence of a substring \( A \) in a string \( B \). If \( A \) is not found, return `-1`.

### **Approach**
- Loop through each character of string \( B \).  
- Check if the substring starting at each position matches string \( A \).  
- Return the index immediately upon finding the first match.

### **Code (C)**

```c
#include <stdio.h>
#include <string.h>

int strstrCustom(const char *A, const char *B) {
    int lenA = strlen(A);
    int lenB = strlen(B);
    
    if (lenA == 0) return 0;  // Empty string A is found at index 0 by definition
    
    for (int i = 0; i <= lenB - lenA; i++) {
        int j;
        for (j = 0; j < lenA; j++) {
            if (B[i + j] != A[j]) {
                break;
            }
        }
        if (j == lenA) {
            return i;  // Found match at index i
        }
    }
    return -1;  // No match found
}

int main() {
    const char *A = "bc";
    const char *B = "abcddbc";
    
    int result = strstrCustom(A, B);
    printf("The first occurrence of \"%s\" in \"%s\" is at index: %d\n", A, B, result);
    
    return 0;
}
```

### **Explanation**
1. `strlen(A)` and `strlen(B)` calculate the lengths of strings \( A \) and \( B \).
2. We loop from `0` to `lenB - lenA` to avoid going out of bounds.
3. The inner loop checks character by character if substring \( A \) matches part of \( B \).
4. If `j == lenA`, it means the whole substring matches, and we return the starting index.
5. If no match is found, return `-1`.

### **Time Complexity**
- **Best case:** O(lenA) — when a match is found at the beginning.  
- **Worst case:** O(lenA * lenB) — when no match is found.

This approach is simple, but for larger inputs or repeated search patterns, more advanced algorithms like **KMP (Knuth-Morris-Pratt)** or **Rabin-Karp** could be used.


These solutions cover multiple approaches with different complexities for better understanding and optimization.

Here’s how to implement **Knuth-Morris-Pratt (KMP)** and **Rabin-Karp (RK)** algorithms for solving the `strstr()` function in **C**.

---

### **1. Knuth-Morris-Pratt (KMP) Algorithm**
The **KMP** algorithm preprocesses the pattern \( A \) to build a longest prefix suffix (LPS) array that helps skip unnecessary comparisons.

#### **Code (C)**
```c
#include <stdio.h>
#include <string.h>

void computeLPSArray(const char *A, int lenA, int *lps) {
    int length = 0;
    lps[0] = 0;  // LPS[0] is always 0
    int i = 1;
    
    while (i < lenA) {
        if (A[i] == A[length]) {
            length++;
            lps[i] = length;
            i++;
        } else {
            if (length != 0) {
                length = lps[length - 1];
            } else {
                lps[i] = 0;
                i++;
            }
        }
    }
}

int strstrKMP(const char *A, const char *B) {
    int lenA = strlen(A);
    int lenB = strlen(B);
    if (lenA == 0) return 0;
    
    int lps[lenA];
    computeLPSArray(A, lenA, lps);
    
    int i = 0, j = 0;
    while (i < lenB) {
        if (A[j] == B[i]) {
            i++;
            j++;
        }
        
        if (j == lenA) {
            return i - j;  // Found the match
        } else if (i < lenB && A[j] != B[i]) {
            if (j != 0) {
                j = lps[j - 1];
            } else {
                i++;
            }
        }
    }
    return -1;
}

int main() {
    const char *A = "bc";
    const char *B = "abcddbc";
    
    int result = strstrKMP(A, B);
    printf("KMP: The first occurrence of \"%s\" in \"%s\" is at index: %d\n", A, B, result);
    
    return 0;
}
```

---

### **2. Rabin-Karp (RK) Algorithm**
The **Rabin-Karp** algorithm uses a rolling hash to match substrings efficiently.

#### **Code (C)**
```c
#include <stdio.h>
#include <string.h>
#define PRIME 101

int createHash(const char *str, int len) {
    int hash = 0;
    for (int i = 0; i < len; i++) {
        hash = hash * 256 + str[i];
        hash %= PRIME;
    }
    return hash;
}

int recalculateHash(const char *str, int oldIndex, int newIndex, int oldHash, int patternLen) {
    oldHash = (oldHash - str[oldIndex] * 256 * (patternLen - 1)) % PRIME;
    oldHash = (oldHash * 256 + str[newIndex]) % PRIME;
    if (oldHash < 0) {
        oldHash += PRIME;
    }
    return oldHash;
}

int strstrRK(const char *A, const char *B) {
    int lenA = strlen(A);
    int lenB = strlen(B);
    if (lenA > lenB) return -1;

    int patternHash = createHash(A, lenA);
    int textHash = createHash(B, lenA);
    
    for (int i = 0; i <= lenB - lenA; i++) {
        if (patternHash == textHash && strncmp(B + i, A, lenA) == 0) {
            return i;  // Found the match
        }
        if (i < lenB - lenA) {
            textHash = recalculateHash(B, i, i + lenA, textHash, lenA);
        }
    }
    return -1;
}

int main() {
    const char *A = "bc";
    const char *B = "abcddbc";
    
    int result = strstrRK(A, B);
    printf("Rabin-Karp: The first occurrence of \"%s\" in \"%s\" is at index: %d\n", A, B, result);
    
    return 0;
}
```

---

### **Explanation of Algorithms**
1. **KMP**  
   - Uses an LPS (Longest Prefix Suffix) array to skip redundant comparisons.  
   - Time Complexity: **O(lenA + lenB)**.  
   - Space Complexity: **O(lenA)** for LPS array.

2. **Rabin-Karp**  
   - Computes a hash value for substring comparisons to detect matches efficiently.  
   - Time Complexity: **O(lenA + lenB)** on average, but can be **O(lenA * lenB)** in worst-case (with hash collisions).  
   - Space Complexity: **O(1)** (rolling hash).

These efficient algorithms provide different approaches to solving substring search problems depending on the context and input characteristics.


To find the **maximum** number from a stream of **1 million numbers** with constraints:

- Numbers are entered **one-by-one** (first case).
- Numbers are provided **1000 at a time** (second case).

Here’s how to handle both scenarios efficiently.

---
**have a million numbers, how will u find the maximum number from them if → the input is given on the fly i.e. the numbers are entered one by one. → numbers are given 1000 at a time**

### **1. One-by-One Input (Streaming Input)**
#### Approach:
- Maintain a variable `maxNum` initialized to a very small value (e.g., `INT_MIN` in C/C++).
- Iterate through the numbers as they are given one at a time.
- Update `maxNum` if the current number is larger.

#### Pseudo-Code (for single-stream input):
```cpp
#include <iostream>
#include <climits>
using namespace std;

int main() {
    int num, maxNum = INT_MIN;  // Initialize maxNum to smallest possible value
    while (cin >> num) {  // Continue until input ends
        if (num > maxNum) {
            maxNum = num;  // Update maxNum if current number is larger
        }
    }
    cout << "Maximum number is: " << maxNum << endl;
    return 0;
}
```

**Explanation**:
- `cin >> num` takes input until EOF. For real-time streams, data can be processed without waiting for all inputs.
- Time Complexity: **O(n)** (linear scan over all numbers).
- Space Complexity: **O(1)**.

---

### **2. Batch Input (1000 Numbers at a Time)**
#### Approach:
- Process each batch separately, updating the global maximum after processing each batch.
- Maintain a global `maxNum` and update it with the maximum from each batch.

#### Pseudo-Code (for batch input):
```cpp
#include <iostream>
#include <climits>
using namespace std;

int main() {
    int maxNum = INT_MIN;  // Initialize global maximum
    int batchSize = 1000;
    int numbers[batchSize];

    while (true) {
        int count = 0;
        for (int i = 0; i < batchSize && cin >> numbers[i]; i++) {
            count++;
        }
        if (count == 0) break;  // Exit loop if no numbers are read

        // Find the maximum in the current batch
        int batchMax = INT_MIN;
        for (int i = 0; i < count; i++) {
            if (numbers[i] > batchMax) {
                batchMax = numbers[i];
            }
        }
        if (batchMax > maxNum) {
            maxNum = batchMax;  // Update global maximum
        }
    }
    cout << "Maximum number is: " << maxNum << endl;
    return 0;
}
```

**Explanation**:
- Process `1000` numbers at a time using an array.
- Find the maximum in the batch, then update the global maximum.
- Time Complexity: **O(n)** (linear scan for all numbers, with constant time comparisons).
- Space Complexity: **O(batchSize)**.

---

### **Optimization Considerations**
- **One-Pass Approach**: Regardless of the input format (single or batch), only one pass through the numbers is needed to find the maximum.
- **Memory Efficiency**: In batch input, only one small array of size 1000 is used, making it scalable for very large inputs.

This strategy works efficiently even for **very large streams** or **real-time data processing**.
