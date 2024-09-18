#solution #array


# My solution

## Task
An array is **monotonic** if it is either monotone increasing or monotone decreasing.

An array `nums` is monotone increasing if for all `i <= j`, `nums[i] <= nums[j]`. An array `nums` is monotone decreasing if for all `i <= j`, `nums[i] >= nums[j]`.

Given an integer array `nums`, return `true` _if the given array is monotonic, or_ `false` _otherwise_.

**Example 1:**

**Input:** nums = [1,2,2,3]
**Output:** true

**Example 2:**

**Input:** nums = [6,5,4,4]
**Output:** true

**Example 3:**

**Input:** nums = [1,3,2]
**Output:** false

**Constraints:**

- `1 <= nums.length <= 105`
- `-105 <= nums[i] <= 105`

## Solution Idea
Create two flags: `increasing` and `decreasing`, and set them to `true`. By the end of the program if either of those flags is true - the array is monotonic (since it was either non-decreasing or non-increasing; we don't even check for the equal elements). Walk over all of the elements comparing each two in a row, if one is larger than the other - adjust the flag.

## Solution
```go
```



