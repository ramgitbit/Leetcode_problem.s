# 7. Reverse Integer

**LeetCode:** [Reverse Integer](https://leetcode.com/problems/reverse-integer/)  
**Difficulty:** Medium  
**Language:** C++

## Problem

Given a signed 32-bit integer `x`, return its digits reversed.  
If the reversed number goes outside the 32-bit integer range, return `0`.

### Examples

```text
Input:  123
Output: 321

Input:  -123
Output: -321

Input:  120
Output: 21
```

## Approach

I used **digit extraction** to reverse the number.

- `x % 10` → extracts the last digit.
- `x / 10` → removes the last digit.
- `rev * 10 + digit` → builds the reversed number.
- Before updating `rev`, I check for **integer overflow**.

## C++ Solution

```cpp
class Solution {
public:
    int reverse(int x) {

        int rev = 0;

        while(x != 0) {

            int digit = x % 10;
            x = x / 10;

            // Check for overflow
            if(rev > INT_MAX / 10 ||
               (rev == INT_MAX / 10 && digit > 7)) {
                return 0;
            }

            if(rev < INT_MIN / 10 ||
               (rev == INT_MIN / 10 && digit < -8)) {
                return 0;
            }

            rev = rev * 10 + digit;
        }

        return rev;
    }
};
```

## Dry Run

For `x = 123`:

```text
123 % 10 = 3  → rev = 3
12  % 10 = 2  → rev = 32
1   % 10 = 1  → rev = 321
```

So:

```text
123 → 321
```

## Complexity

- **Time:** `O(log n)`
- **Space:** `O(1)`

## Key Learning

- Digit extraction
- `%` and `/` operators
- Number reversal
- `while` loop
- Integer overflow handling

**LeetCode Journey 🚀 | Problem #7**