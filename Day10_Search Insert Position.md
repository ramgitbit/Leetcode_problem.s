# 35. Search Insert Position

**LeetCode:** [Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given a sorted array of distinct integers and a target value, return the index if the target is found.

If the target is not found, return the index where it would be inserted so that the array remains sorted.

The solution must have **O(log n)** time complexity.

### Examples

```text
Input:  nums = [1,3,5,6], target = 5
Output: 2
```

```text
Input:  nums = [1,3,5,6], target = 2
Output: 1
```

```text
Input:  nums = [1,3,5,6], target = 7
Output: 4
```

## Approach

I used **Binary Search**.

Since the array is already sorted, we can repeatedly divide the search range into two halves.

- `low` points to the starting index.
- `high` points to the ending boundary.
- Find the middle index using:
  ```cpp
  mid = (low + high) / 2;
  ```
- If `nums[mid] == target`, return `mid`.
- If `target < nums[mid]`, search in the left half.
- Otherwise, search in the right half.
- If the target is not found, `low` will point to the correct insertion position.

## C++ Solution

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {

        int low = 0;
        int high = nums.size();

        if(target > nums[high - 1]) {
            return high;
        }

        while(low <= high) {

            int mid = (low + high) / 2;

            if(nums[mid] == target) {
                return mid;
            }

            if(target < nums[mid]) {
                high = mid - 1;
            }
            else {
                low = mid + 1;
            }
        }

        return low;
    }
};
```

## Dry Run

For:

```text
nums = [1,3,5,6]
target = 2
```

Initially:

```text
low = 0
high = 4
```

### Step 1

```text
mid = (0 + 4) / 2
mid = 2

nums[2] = 5
```

Since:

```text
2 < 5
```

Move to the left:

```text
high = mid - 1
high = 1
```

### Step 2

```text
mid = (0 + 1) / 2
mid = 0

nums[0] = 1
```

Since:

```text
2 > 1
```

Move to the right:

```text
low = mid + 1
low = 1
```

Now:

```text
low > high
```

So the target is not present.

Finally:

```text
return low;
```

Therefore:

```text
Output = 1
```

Because `2` should be inserted at index `1`:

```text
[1, 2, 3, 5, 6]
    ↑
   index 1
```

## Key Concept

The most important idea is:

> **If the target is not found, `low` gives the position where the target should be inserted.**

For example:

```text
nums = [1,3,5,6]
target = 4
```

After binary search:

```text
low = 2
```

So `4` should be inserted at index `2`.

## Complexity

- **Time:** `O(log n)`
- **Space:** `O(1)`

## Key Learning

- Binary Search
- `low`, `high`, and `mid`
- Searching in sorted arrays
- Finding insertion position
- Reducing search space
- `O(log n)` time complexity

**LeetCode Journey 🚀 | Problem #35**