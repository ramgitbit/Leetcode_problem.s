# Reverse Integer

**LeetCode Problem:** [Reverse Integer](https://leetcode.com/problems/reverse-integer/description/)

## Problem

Given a signed 32-bit integer `x`, return `x` with its digits reversed.

If reversing `x` causes the value to go outside the signed 32-bit integer range:

```text
[-2³¹, 2³¹ - 1]
```

return `0`.

### Examples

```text
Input:  x = 123
Output: 321
```

```text
Input:  x = -123
Output: -321
```

```text
Input:  x = 120
Output: 21
```

## Approach

I used the **digit extraction and reversal** approach.

1. First, store the sign of the number.
2. Convert the number to positive using `abs()`.
3. Extract the last digit using `% 10`.
4. Add the extracted digit to `rev`.
5. Remove the last digit using `// 10`.
6. Restore the original sign.
7. Check whether the reversed number is outside the 32-bit integer range.
8. If it is outside the range, return `0`.

## Solution

```python
class Solution:
    def reverse(self, n: int) -> int:

        sign = -1 if n < 0 else 1
        n = abs(n)
        rev = 0

        while n > 0:
            rev = rev * 10 + n % 10
            n //= 10

        rev *= sign

        if rev < -2**31 or rev > 2**31 - 1:
            return 0

        return rev
```

## Dry Run

For:

```text
n = 123
```

### Step 1

```text
sign = 1
n = 123
rev = 0
```

### Step 2

```text
123 % 10 = 3
rev = 0 * 10 + 3
rev = 3

n = 123 // 10
n = 12
```

### Step 3

```text
12 % 10 = 2
rev = 3 * 10 + 2
rev = 32

n = 12 // 10
n = 1
```

### Step 4

```text
1 % 10 = 1
rev = 32 * 10 + 1
rev = 321

n = 1 // 10
n = 0
```

Loop ends.

```text
321
```

So the answer is:

```text
Output: 321
```

## Important Concepts

### `% 10`

Gets the **last digit**:

```python
123 % 10 = 3
```

### `// 10`

Removes the **last digit**:

```python
123 // 10 = 12
```

### `rev * 10`

Makes space for the new digit:

```text
rev = 3

3 * 10 = 30
30 + 2 = 32
```

## Complexity

- **Time Complexity:** `O(log n)`
- **Space Complexity:** `O(1)`

## Key Learning

This problem helped me practice:

- Number reversal
- `%` operator
- `//` operator
- `while` loop
- Handling negative numbers
- 32-bit integer overflow
- Building a reversed number mathematically

**Day 3 of my LeetCode Journey 🚀**