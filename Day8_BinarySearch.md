# 704. Binary Search

**LeetCode:** [Binary Search](https://leetcode.com/problems/binary-search/description/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given a sorted array `nums` and an integer `target`, return the index of `target`.

If `target` does not exist in the array, return `-1`.

The solution must have **O(log n)** time complexity.

### Examples

```text
Input:  nums = [-1,0,3,5,9,12], target = 9
Output: 4

Input:  nums = [-1,0,3,5,9,12], target = 2
Output: -1
```

## Approach

I used **Binary Search**.

- Set `l` (left) to `0`.
- Set `right` to `nums.size() - 1`.
- Find the middle index using:
  `mid = l + (right - l) / 2`
- If `nums[mid] == target`, return `mid`.
- If `nums[mid] < target`, search in the right half.
- Otherwise, search in the left half.
- If the target is not found, return `-1`.

## C++ Solution

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {

        int l = 0, right = nums.size() - 1;

        while(l <= right) {

            int mid = l + (right - l) / 2;

            if(nums[mid] == target) {
                return mid;
            }
            else if(nums[mid] < target) {
                l = mid + 1;
            }
            else {
                right = mid - 1;
            }
        }

        return -1;
    }
};
```

## Dry Run

For:

```text
nums = [-1,0,3,5,9,12]
target = 9
```

```text
l = 0
right = 5

mid = 2 → nums[2] = 3
3 < 9 → search right half

l = 3
right = 5

mid = 4 → nums[4] = 9
9 == 9 → return 4
```

So the answer is:

```text
4
```

## Complexity

- **Time:** `O(log n)`
- **Space:** `O(1)`

## Key Learning

- Binary Search
- Two pointers (`left` and `right`)
- Finding the middle element
- Reducing the search space
- `O(log n)` time complexity

**LeetCode Journey 🚀 | Problem #704**