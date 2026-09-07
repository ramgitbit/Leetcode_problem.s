# 67. Add Binary

**LeetCode:** [Add Binary](https://leetcode.com/problems/add-binary/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given two binary strings `a` and `b`, return their sum as a binary string.

### Examples

```text
Input:  a = "11", b = "1"
Output: "100"
```

```text
Input:  a = "1010", b = "1011"
Output: "10101"
```

## Approach

I used the **Binary Addition with Carry** approach.

Just like normal binary addition, we start from the **rightmost digit**.

- `i` points to the last digit of `a`.
- `j` points to the last digit of `b`.
- `carry` stores the carry from the previous addition.
- Add the current digits and `carry`.
- `sum % 2` gives the current binary digit.
- `sum / 2` gives the next carry.
- Finally, reverse the answer because digits are added from right to left.

## C++ Solution

```cpp
class Solution {
public:
    string addBinary(string a, string b) {

        int i = a.size() - 1;
        int j = b.size() - 1;
        int carry = 0;

        string ans = "";

        while(i >= 0 || j >= 0 || carry) {

            int sum = carry;

            if(i >= 0)
                sum += a[i--] - '0';

            if(j >= 0)
                sum += b[j--] - '0';

            ans += (sum % 2) + '0';

            carry = sum / 2;
        }

        reverse(ans.begin(), ans.end());

        return ans;
    }
};
```

## Dry Run

For:

```text
a = "11"
b = "1"
```

Start from right to left:

```text
1 + 1 = 2
```

In binary:

```text
2 → digit = 0
carry = 1
```

Next:

```text
1 + 0 + 1 = 2
```

Again:

```text
digit = 0
carry = 1
```

After both strings are finished:

```text
carry = 1
```

So answer before reverse:

```text
"001"
```

After reverse:

```text
"100"
```

Therefore:

```text
Output = "100"
```

## Important Concept

For binary addition:

```text
sum % 2
```

gives the current digit.

```text
sum / 2
```

gives the carry.

For example:

```text
1 + 1 = 2

2 % 2 = 0   → digit
2 / 2 = 1   → carry
```

## Complexity

- **Time:** `O(max(n, m))`
- **Space:** `O(max(n, m))`

## Key Learning

- Binary addition
- Carry handling
- String traversal from right to left
- Character to integer conversion using `- '0'`
- `reverse()`

**LeetCode Journey 🚀 | Problem #67**