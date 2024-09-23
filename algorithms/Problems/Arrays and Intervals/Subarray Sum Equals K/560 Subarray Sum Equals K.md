#solution
## Problem
___
[LINK](https://leetcode.com/problems/subarray-sum-equals-k/description/)

>[!Note]- Problem Description
> Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.
>
>A subarray is a contiguous non-empty sequence of elements within an array.
>
> 
>
>Example 1:
>
>Input: nums = [1,1,1], k = 2
>Output: 2
>
>Example 2:
>
>Input: nums = [1,2,3], k = 3
>Output: 2
>
> 
>
>Constraints:
>
>    1 <= nums.length <= 2 * 104
>    -1000 <= nums[i] <= 1000
>    -107 <= k <= 107

## Solution Idea
___
We are going to use prefix array to calculate how many times we have encountered subarrays subtracting which will result in a needed sum.




## Time Complexity
___
O(n)
Because  

## Time Complexity
___
O(?) - where 
Because 


## Code:
___
```go



```