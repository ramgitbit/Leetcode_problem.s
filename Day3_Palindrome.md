# Palindrome Number

**LeetCode Problem:** [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

## Problem

Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.

A palindrome number reads the same **forward and backward**.

### Example

```text
Input: 121
Output: true

Explanation:
121 → Reverse = 121
Therefore, 121 is a palindrome.
```

```text
Input: -121
Output: false

Explanation:
-121 → Reverse = 121
Therefore, -121 is not a palindrome.
```

## Approach

I used the **number reversal** approach.

1. If `x` is negative, return `False`.
2. Store the original number in `o`.
3. Reverse the number using a `while` loop.
4. Compare the original number with the reversed number.
5. If both are equal, return `True`; otherwise, return `False`.

## Solution

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:

        if x < 0:
            return False

        o = x
        rev = 0

        while x > 0:
            rev = rev * 10 + (x % 10)
            x = x // 10

        if o == rev:
            return True
        else:
            return False
```

## Dry Run

For:

```text
x = 121
```

```text
Original = 121
Reverse  = 121
```

Therefore:

```text
121 == 121 → True
```

## Complexity

- **Time Complexity:** `O(log n)`
- **Space Complexity:** `O(1)`

## Key Learning

This problem helped me practice:

- Number reversal
- `while` loop
- `%` operator
- `//` operator
- Comparing original and reversed numbers
- Handling negative numbers

**Day 2 of my LeetCode Journey 🚀**