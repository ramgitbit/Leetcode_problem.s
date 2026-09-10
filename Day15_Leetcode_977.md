# 977. Squares of a Sorted Array

**LeetCode:** [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given an integer array `nums` sorted in non-decreasing order, return an array containing the square of each number, also sorted in non-decreasing order.

### Examples

```text
Input:  nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
```

```text
Input:  nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

## Approach

I used the **Two Pointer** approach.

The array is already sorted, but after squaring, negative numbers can become larger.

- `left` starts from the beginning.
- `right` starts from the end.
- Compare `abs(nums[left])` and `abs(nums[right])`.
- The larger value will have the larger square.
- Put that square at the **end** of the answer array.
- Move the corresponding pointer.
- Continue until all elements are processed.

## C++ Solution

```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {

        int n = nums.size();

        vector<int> ans(n);

        int left = 0;
        int right = n - 1;

        for(int i = n - 1; i >= 0; i--) {

            if(abs(nums[left]) > abs(nums[right])) {
                ans[i] = nums[left] * nums[left];
                left++;
            }
            else {
                ans[i] = nums[right] * nums[right];
                right--;
            }
        }

        return ans;
    }
};
```

## Dry Run

For:

```text
nums = [-4,-1,0,3,10]
```

Initially:

```text
left = 0   → -4
right = 4  → 10
```

Compare:

```text
|-4| = 4
|10| = 10
```

`10` is larger, so:

```text
ans[4] = 100
right--
```

Next:

```text
left = -4
right = 3
```

Compare:

```text
|-4| = 4
|3| = 3
```

`-4` has the larger square:

```text
ans[3] = 16
left++
```

Continue similarly:

```text
ans = [0,1,9,16,100]
```

Final output:

```text
[0,1,9,16,100]
```

## Key Concept

After squaring, the **largest square will always come from either end** of the sorted array.

Example:

```text
[-4,-1,0,3,10]
 ↑             ↑
left          right
```

Compare the absolute values of both ends and place the larger square from the **back of the answer**.

## Complexity

- **Time:** `O(n)`
- **Space:** `O(n)`

## Key Learning

- Two Pointer Technique
- Working with negative numbers
- `abs()`
- In-place comparison
- Filling an array from the end
- `O(n)` solution

**LeetCode Journey 🚀 | Problem #977**