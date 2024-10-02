Leetcode 74
#solution 
#binary-search 
## Problem
___
[LINK](PLACEHOLDER)
You are given an m x n integer matrix matrix with the following two properties:

    Each row is sorted in non-decreasing order.
    The first integer of each row is greater than the last integer of the previous row.

Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

 

Example 1:

Input: matrix = \[[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true

Example 2:

Input: matrix = \[[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false

 

Constraints:

    m == matrix.length
    n == matrix[i].length
    1 <= m, n <= 100
    -104 <= matrix[i][j], target <= 104



## Solution Idea
___
1. Do a binary search over the first element of each row to find which row might include the target.
2. Do a binary search over that row to find the target.

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