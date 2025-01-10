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

---

### **Websites for Practice**
1. **LeetCode** – [Sqrt(x)](https://leetcode.com/problems/sqrtx/)
2. **GeeksforGeeks** – [Floor square root of a number](https://practice.geeksforgeeks.org/problems/square-root/0)
3. **Codeforces** – Search for square root problems in their archive.

These solutions cover multiple approaches with different complexities for better understanding and optimization.
