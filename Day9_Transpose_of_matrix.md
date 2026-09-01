# Matrix Transpose — Quick Note

## Problem

Given a 2D matrix, return its **transpose**.
**LeetCode:** [Transpose](https://leetcode.com/problems/transpose-matrix/submissions/2127126605/)  

### Example

Original:

```text
1  2  3
4  5  6
```

Transpose:

```text
1  4
2  5
3  6
```

---

## 1. What I Initially Thought

Maine socha:

* Matrix ki rows (`m`) aur columns (`n`) nikalunga.
* Ek new vector `v` banaunga.
* `arr` ke elements ko `v` mein copy karunga.
* Last mein `v` return kar dunga.

Mera main logic tha:

```cpp
v[i][j] = arr[i][j];
```

### Problem

Ye **copy** karega, transpose nahi.

Transpose mein **row aur column swap** karna hota hai:

```cpp
v[j][i] = arr[i][j];
```

---

## 2. My Initial Code

```cpp
class Solution {
public:
    vector<vector<int>> transpose(vector<vector<int>>& arr) {

        int m = arr.size(), n = arr[0].size();

        vector<vector<int>> v;

        for(int j = 0; j <= n; j++) {
            for(int i = 0; i <= m; i++) {
                v[i][j] = arr[i][j];
            }
        }

        return v;
    }
};
```

---

## 3. Mistakes

### ❌ Mistake 1: `<=` ki jagah `<`

Maine:

```cpp
i <= m
j <= n
```

likha.

Valid indexes hamesha:

```cpp
i < m
j < n
```

honge.

For example, agar `m = 2`, valid row indexes:

```text
0, 1
```

hain, `2` nahi.

---

### ❌ Mistake 2: `v` Empty Tha

Maine:

```cpp
vector<vector<int>> v;
```

likha.

Isme initially koi row/column nahi hai.

Isliye directly:

```cpp
v[i][j] = ...
```

nahi kar sakte.

Transpose ke liye original matrix `m × n` hai, to new matrix `n × m` hogi.

```cpp
vector<vector<int>> v(n, vector<int>(m));

```
v naam ka 2D vector banao jisme n rows aur har row mein m integers honge.

---

### ❌ Mistake 3: Index Swap Nahi Kiya

Maine:

```cpp
v[i][j] = arr[i][j];
```

likha tha.

Transpose ke liye:

```cpp
v[j][i] = arr[i][j];
```

hona chahiye.

---

# 4. Actual Solution

Agar original matrix:

```text
m × n
```

hai, to transpose:

```text
n × m
```

hoga.

So:

```cpp
vector<vector<int>> v(n, vector<int>(m));
```

Then:

```cpp
for(int i = 0; i < m; i++) {
    for(int j = 0; j < n; j++) {
        v[j][i] = arr[i][j];
    }
}
```

---

# 5. Complete Correct Code

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    vector<vector<int>> transpose(vector<vector<int>>& arr) {

        int m = arr.size();
        int n = arr[0].size();

        // Transpose will be n × m
        vector<vector<int>> v(n, vector<int>(m));

        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {

                // Swap row and column
                v[j][i] = arr[i][j];
            }
        }

        return v;
    }
};
```

---

# 6. Easy Way to Remember

### Original

```cpp
arr[i][j]
```

### Transpose

```cpp
v[j][i] = arr[i][j];
```

Simply **row and column swap**:

```text
arr[i][j]
    ↓
  swap
    ↓
v[j][i]
```

---

# 7. Important Points

| Concept         | Meaning              |
| --------------- | -------------------- |
| `arr.size()`    | Number of rows       |
| `arr[0].size()` | Number of columns    |
| `m × n`         | Original matrix size |
| `n × m`         | Transpose size       |
| `i < m`         | Row traversal        |
| `j < n`         | Column traversal     |
| `v[j][i]`       | Transpose position   |

### ⭐ Main Formula

```cpp
v[j][i] = arr[i][j];
```

**Transpose = Row ↔ Column**
