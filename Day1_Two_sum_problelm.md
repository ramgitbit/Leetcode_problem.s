# Two Sum

**LeetCode Problem:** [Two Sum](https://leetcode.com/problems/two-sum/)

## Problem

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to `target`.

### Example

```text
Input:
nums = [2, 7, 11, 15]
target = 9

Output:
[0, 1]
```

Because:

```text
nums[0] + nums[1] = 2 + 7 = 9
```

## Approach _ :

I used the **Brute Force** approach.

- Use two nested loops.
- First loop selects the first element.
- Second loop checks every element after it.
- If `nums[i] + nums[j] == target`, return `{i, j}`.

## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {

        for(int i = 0; i < nums.size(); i++) {

            for(int j = i + 1; j < nums.size(); j++) {

                if(nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }

        return {};
    }
};
```

## Complexity

- **Time Complexity:** `O(n²)`
- **Space Complexity:** `O(1)`

## Key Learning

This problem helped me practice:

- Nested loops
- Array traversal
- Index handling
- Returning multiple values using `vector<int>`
- Brute Force problem-solving

**Day 1 of my LeetCode Journey 🚀**