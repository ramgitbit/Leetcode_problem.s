# 344. Reverse String

**LeetCode:** [Reverse String](https://leetcode.com/problems/reverse-string/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Write a function that reverses a string.

The input is given as an array of characters `s`.

The reversal must be done **in-place**, using `O(1)` extra memory.

### Examples

```text
Input:  s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

```text
Input:  s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

## Approach

I used the **Two Pointer** approach.

- `left` pointer starts from the beginning.
- `right` pointer starts from the end.
- Swap the characters at `left` and `right`.
- Move `left` forward and `right` backward.
- Continue until `left < right`.

This reverses the string **in-place** without using another array.

## C++ Solution

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {

        int left = 0;
        int right = s.size() - 1;

        while(left < right) {

            swap(s[left], s[right]);

            left++;
            right--;
        }
    }
};
```

## Dry Run

For:

```text
s = ["h","e","l","l","o"]
```

Initially:

```text
left = 0
right = 4
```

### Step 1

Swap:

```text
h ↔ o
```

Array:

```text
["o","e","l","l","h"]
```

Move pointers:

```text
left = 1
right = 3
```

### Step 2

Swap:

```text
e ↔ l
```

Array:

```text
["o","l","l","e","h"]
```

Move pointers:

```text
left = 2
right = 2
```

Now:

```text
left < right
```

is false, so the loop stops.

Final answer:

```text
["o","l","l","e","h"]
```

## Key Concept

The main idea is to swap elements from **both ends**:

```text
h e l l o
↑       ↑
L       R

o e l l h
  ↑   ↑
  L   R
```

Continue until the two pointers meet.

## Complexity

- **Time:** `O(n)`
- **Space:** `O(1)`

## Key Learning

- Two Pointer Technique
- `swap()`
- In-place array manipulation
- Reversing a string
- `O(1)` extra space

**LeetCode Journey 🚀 | Problem #344**
