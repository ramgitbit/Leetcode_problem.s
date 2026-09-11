# 283. Move Zeroes

**LeetCode:** [Move Zeroes](https://leetcode.com/problems/move-zeroes/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given an integer array `nums`, move all `0`s to the end of the array while maintaining the relative order of the non-zero elements.

The operation must be done **in-place**, without making a copy of the array.

### Examples

```text
Input:  nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

```text
Input:  nums = [0]
Output: [0]
```

## Approach

I used the **Two Pointer** approach.

- `j` keeps track of the position where the next non-zero element should go.
- Traverse the array using `i`.
- Whenever `nums[i]` is non-zero, swap it with `nums[j]`.
- Increment `j`.
- This automatically moves all zeroes towards the end while keeping the order of non-zero elements.

## C++ Solution

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {

        int j = 0;

        for(int i = 0; i < nums.size(); i++) {

            if(nums[i] != 0) {
                swap(nums[i], nums[j]);
                j++;
            }
        }
    }
};
```

## Dry Run

For:

```text
nums = [0,1,0,3,12]
```

Initially:

```text
j = 0
```

### Step 1

`nums[0] = 0`

Nothing happens.

```text
[0,1,0,3,12]
 j
```

### Step 2

`nums[1] = 1` → non-zero.

Swap `nums[i]` and `nums[j]`:

```text
[1,0,0,3,12]
```

Move `j`:

```text
j = 1
```

### Step 3

`nums[2] = 0`

Nothing happens.

### Step 4

`nums[3] = 3` → non-zero.

Swap:

```text
[1,3,0,0,12]
```

```text
j = 2
```

### Step 5

`nums[4] = 12` → non-zero.

Swap:

```text
[1,3,12,0,0]
```

Final answer:

```text
[1,3,12,0,0]
```

## Key Concept

The important idea is:

```text
j = position for next non-zero element
```

`i` scans the complete array, while `j` only moves when we find a non-zero element.

Example:

```text
[0, 1, 0, 3, 12]
   ↑
   i

j = 0
```

When `1` is found, it is placed at position `j`.

This keeps all non-zero elements in their original order.

## Complexity

- **Time:** `O(n)`
- **Space:** `O(1)`

## Key Learning

- Two Pointer Technique
- In-place array manipulation
- `swap()`
- Maintaining relative order
- Moving zeroes efficiently

**LeetCode Journey 🚀 | Problem #283**