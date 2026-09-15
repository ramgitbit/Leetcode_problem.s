# 169. Majority Element

**LeetCode:** [Majority Element](https://leetcode.com/problems/majority-element/description/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given an array `nums` of size `n`, return the **majority element**.

The majority element is the element that appears more than:

```text
n / 2
```

times in the array.

You may assume that the majority element always exists.

### Examples

```text
Input:  nums = [3,2,3]
Output: 3
```

```text
Input:  nums = [2,2,1,1,1,2,2]
Output: 2
```

## Approach

I used the **Sorting** approach.

- First, sort the array.
- After sorting, all same elements come together.
- Since the majority element appears more than `n/2` times, it must occupy the **middle position** of the sorted array.
- Therefore, simply return:

```cpp
nums[n / 2]
```

## C++ Solution

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {

        sort(nums.begin(), nums.end());

        int n = nums.size();

        return nums[n / 2];
    }
};
```

## Dry Run

For:

```text
nums = [2,2,1,1,1,2,2]
```

After sorting:

```text
[1,1,1,2,2,2,2]
```

Size:

```text
n = 7
```

Middle index:

```text
n / 2 = 7 / 2 = 3
```

Element at index `3`:

```text
nums[3] = 2
```

Therefore:

```text
Output = 2
```

## Key Concept

After sorting, the majority element will always be present at:

```cpp
nums[n / 2]
```

For example:

```text
[1,1,1,2,2,2,2]
       ↑
     n / 2
```

So we don't need to count every element.

## Complexity

- **Time:** `O(n log n)` — due to sorting
- **Space:** `O(1)` auxiliary space

## Key Learning

- Sorting
- Array indexing
- Understanding majority element
- Using `n / 2`
- STL `sort()`

**LeetCode Journey 🚀 | Problem #169**