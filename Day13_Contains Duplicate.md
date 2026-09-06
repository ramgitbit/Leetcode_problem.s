# 217. Contains Duplicate

**LeetCode:** [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)  
**Difficulty:** Easy  
**Language:** C++

## Problem

Given an integer array `nums`, return `true` if any value appears at least twice in the array.

Return `false` if every element is distinct.

### Examples

```text
Input:  nums = [1,2,3,1]
Output: true
```

Because `1` appears twice.

```text
Input:  nums = [1,2,3,4]
Output: false
```

Because every element is distinct.

## Approach

I used an **Unordered Set** to keep track of the elements that have already appeared.

- Traverse the array one by one.
- Check if the current element is already present in the set.
- If it is present, a duplicate exists → return `true`.
- Otherwise, insert the element into the set.
- If the complete array is traversed without finding a duplicate, return `false`.

## C++ Solution

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {

        unordered_set<int> st;

        for(int i = 0; i < nums.size(); i++) {

            if(st.find(nums[i]) != st.end()) {
                return true;
            }

            st.insert(nums[i]);
        }

        return false;
    }
};
```

## Dry Run

For:

```text
nums = [1,2,3,1]
```

Initially:

```text
st = {}
```

### Step 1

`1` is not present:

```text
st = {1}
```

### Step 2

`2` is not present:

```text
st = {1,2}
```

### Step 3

`3` is not present:

```text
st = {1,2,3}
```

### Step 4

`1` is already present in the set.

```text
1 → duplicate found
```

Therefore:

```text
return true
```

## Key Concept

The important part is:

```cpp
if(st.find(nums[i]) != st.end())
```

This checks whether the current element already exists in the set.

If it exists → **duplicate found**.

Otherwise:

```cpp
st.insert(nums[i]);
```

adds the element to the set.

## Complexity

- **Time:** `O(n)` average
- **Space:** `O(n)`

## Key Learning

- `unordered_set`
- `find()`
- `insert()`
- Detecting duplicates
- Hashing

**LeetCode Journey 🚀 | Problem #217**
