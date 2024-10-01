#solution 
#binary-search 
## Problem
___
[LINK](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/submissions/1407881380/)

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Example 3:

Input: nums = [], target = 0
Output: [-1,-1]
 

Constraints:

0 <= nums.length <= 105
-109 <= nums[i] <= 109
nums is a non-decreasing array.
-109 <= target <= 109


My input:
nums = [123] target = 123



My output:
[0, 0]



## Solution Idea
___
Just do a regular binary with two pointers but keep in mind which pointer will have the answer in the end. Run binary search twice two find first and last element.

## Special Test Cases
___
```

```

## Time Complexity
___
**O(?)** 
Because

## Space Complexity
___
**O(?)**
Because

## My Code:
___
```go


```

> [!Attention]
> - 


## Example solution:
___
[Video](VIDEO_LINK)

```go


```