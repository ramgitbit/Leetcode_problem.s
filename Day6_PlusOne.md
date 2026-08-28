# Missing Number

**LeetCode Problem:** [Missing Number](https://leetcode.com/problems/missing-number/)

## Problem

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the **only number** that is missing from the array.

### Example 1

```text
Input:
nums = [3,0,1]

Output:
2
```

### Explanation

`n = 3` because the array contains 3 numbers.

Therefore, the complete range is:

```text
[0, 1, 2, 3]
```

The number `2` is missing from the array.

### Example 2

```text
Input:
nums = [0,1]

Output:
2
```

The complete range is:

```text
[0, 1, 2]
```

So `2` is missing.

## Approach

I used the **Sorting + Index Comparison** approach.

The main idea is:

1. Find the size of the array and store it in `n`.
2. Sort the array.
3. Traverse the array from index `0`.
4. At every index `i`, check:

   ```cpp
   i != nums[i]
   ```
5. If they are different, then `i` is the missing number.
6. If every index matches, then the missing number is `n`.

### Why does this work?

After sorting, every number should ideally be at its corresponding index.

For example:

```text
nums = [3,0,1]
```

After sorting:

```text
[0,1,3]
```

Now compare index and value:

```text
index:  0  1  2
value:  0  1  3
```

At index `2`:

```text
2 != 3
```

Therefore, `2` is the missing number.

## Solution

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {

        int n = nums.size();

        sort(nums.begin(), nums.end());

        for(int i = 0; i < n; i++) {

            if(i != nums[i]) {
                return i;
            }
        }

        return n;
    }
};
```

## Dry Run

For:

```text
nums = [3,0,1]
```

### Step 1: Size

```text
n = 3
```

### Step 2: Sort

```text
[0,1,3]
```

### Step 3: Compare index with element

```text
i = 0 → nums[0] = 0 → 0 == 0 ✓

i = 1 → nums[1] = 1 → 1 == 1 ✓

i = 2 → nums[2] = 3 → 2 != 3 ✗
```

Therefore:

```text
return 2
```

## Previous Brute Force Approach

Before this solution, I also tried a **Brute Force** approach.

For every number from `0` to `n`, I searched whether that number existed in the array.

The idea was:

```text
For every i:
    Search i inside nums
    If i is not found:
        return i
```

This approach works, but it takes more time because it uses nested loops.

The sorting approach is more efficient in terms of time.

## Complexity

* **Time Complexity:** `O(n log n)` because of sorting.
* **Space Complexity:** `O(1)` auxiliary space (ignoring the internal implementation details of `sort`).

## Key Learning

This problem helped me practice:

* Sorting an array
* Array indexing
* Comparing index with element
* Finding missing elements
* Brute Force vs optimized approaches

**Day 5 of my LeetCode Journey 🚀**
