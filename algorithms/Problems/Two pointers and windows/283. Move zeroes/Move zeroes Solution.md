#solution 
#two-pointers 
#fast-and-slow-pointers
## Problem
___
[LINK](https://leetcode.com/problems/move-zeroes/description/)

>[!Note]- Problem Description
/*
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
> Note that you must do this in-place without making a copy of the array.
> 
>  
> 
> Example 1:
> 
> Input: nums = [0,1,0,3,12]
> Output: [1,3,12,0,0]
> 
> Example 2:
> 
> Input: nums = [0]
> Output: [0]
> 
>  
> 
> Constraints:
> 
>     1 <= nums.length <= 104
>     -231 <= nums[i] <= 231 - 1
> 
>  
> Follow up: Could you minimize the total number of operations done?
> */
> 
> // My input: [1,0,2,0,0,3,4,0]
> // My output: [1,2,3,4,0,0,0,0]
> 
> 
> // Time: O(n)
> // Space: O(1)


## Solution Idea
___


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
func moveZeroes(nums []int) {
    slow := 0
    fast := -1
    for fast < len(nums) - 1 {
        // move fast pointer on every iteration
        fast++
        right := nums[fast]
        // move slow pointer when switch WAS done
        if right != 0 {
            nums[slow], nums[fast] = nums[fast], nums[slow]
            slow++
        }
    }
}
```

> [!Attention]
> -  You just have to check if the faster pointer points to zero or not. If not - swap. Seems counterintueti


## Example solution:
___
[Video](VIDEO_LINK)

```go


```