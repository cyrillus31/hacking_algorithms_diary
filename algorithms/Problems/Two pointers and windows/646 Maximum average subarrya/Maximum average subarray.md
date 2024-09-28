#solution 
#two-pointers 
#windows #sliding-window 
## Problem
___
[LINK](https://leetcode.com/problems/maximum-average-subarray-i/submissions/1404833619/)

>[!Note]- Problem Description
> 
/*
You are given an integer array nums consisting of n elements, and an integer k.
> 
> Find a contiguous subarray whose length is equal to k that has the maximum average value and return this value. Any answer with a calculation error less than 10-5 will be accepted.
> 
>  
> 
> Example 1:
> 
> Input: nums = [1,12,-5,-6,50,3], k = 4
> Output: 12.75000
> Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
> 
> Example 2:
> 
> Input: nums = [5], k = 1
> Output: 5.00000
> 
>  
> 
> Constraints:
> 
>     n == nums.length
>     1 <= k <= n <= 105
>     -104 <= nums[i] <= 104
> 
> */
> 
> // My input: [-3, -5, 0, -3, 0, 2], k = 3
> // My output: result = 0.33333 from [-3, 0, 2] 
> 
> 
> // Time: O(n)
> // Space: O(1)

## Solution Idea
___
Calculate the sum for the first array of length `k`. Remember it as maximum. 


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