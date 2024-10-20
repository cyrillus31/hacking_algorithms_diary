#solution
## Problem
___
[LINK](https://leetcode.com/problems/squares-of-a-sorted-array/description/)

>[!Note]- Problem Description
>/*
> Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.
> Example 1:
> 
> Input: nums = [-4,-1,0,3,10]
> Output: [0,1,9,16,100]
> Explanation: After squaring, the array becomes [16,1,0,9,100].
> After sorting, it becomes [0,1,9,16,100].
> 
> Example 2:
> 
> Input: nums = [-7,-3,2,3,11]
> Output: [4,9,9,49,121]
> 
> 
> My test  case:
> Input: nums = [1] 
> Output: 1
> Input: nums = [-9, -10]
> Output: [81, 100]
> Input: nums = [0, 0, 0]
> Output: [0, 0, 0]
> 
> Constraints:
> 
>     1 <= nums.length <= 104
>     -104 <= nums[i] <= 104
>     nums is sorted in non-decreasing order.
> 
>  
> Follow up: Squaring each element and sorting the new array is very trivial, could you find an O(n) solution using a different approach?
> 
> */
> 
> Time: O(n)
> Space: O(n)



## Solution Idea
___
Two pointers here. Since the leftmost number is the smallest one (and can be negative) and the rightmost one is the biggest we will use two pointers: one on the left side and one on the right. We will calculate squares for both of those numbers and compare them. The biggest one we will write to the rightmost empty position in the resulting array. Move one pointer. Repeat.



## Time Complexity
___
**O(n)**
Because  we just walk over an array.

## Space Complexity
___
**O(n)**
Because  we store the result in the same size array.


## Code:
___
```go
func sortedSquares(nums []int) []int {
    // init variables to use
    result := make([]int, len(nums))
    l := 0
    r := len(nums) - 1
    insertAt := r
    // walk over the array with two pointers while they do not cross
    for insertAt >= 0 {
        lSquared := nums[l] * nums[l]
        rSquared := nums[l] * nums[r]
        // if pointers point to the same element 
        if l == r {
            result[insertAt] = lSquared
            return result
        } else if lSquared > rSquared {
            result[insertAt] = lSquared
            l++
        } else {
            result[insertAt] = rSquared
            r--
        }
        insertAt--
    }
    return result
}
```