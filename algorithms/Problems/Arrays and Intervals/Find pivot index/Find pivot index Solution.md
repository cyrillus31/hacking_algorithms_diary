## Problem
___
https://leetcode.com/problems/find-pivot-index/submissions/1396174907/
>[!Note}]- Problem description
> Given an array of integers nums, calculate the pivot index of this array.
> 
> The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.
> 
> If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.
> 
> Return the leftmost pivot index. If no such index exists, return -1.
> 
>  
> 
> Example 1:
> 
> Input: nums = [1,7,3,6,5,6]
> Output: 3
> Explanation:
> The pivot index is 3.
> Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
> Right sum = nums[4] + nums[5] = 5 + 6 = 11
> Example 2:
> 
> Input: nums = [1,2,3]
> Output: -1
> Explanation:
> There is no index that satisfies the conditions in the problem statement.
> Example 3:
> 
> Input: nums = [2,1,-1]
> Output: 0
> Explanation:
> The pivot index is 0.
> Left sum = 0 (no elements to the left of index 0)
> Right sum = nums[1] + nums[2] = 1 + -1 = 0
>  
> 
> Constraints:
> 
> 1 <= nums.length <= 104
> -1000 <= nums[i] <= 1000
## Solution Idea
___
Prefix array. Simple.

## Time Complexity
___
O(n + n +  C) = O(n)

Because we walk over the array to create a prefix array and walk over once more to check for every pivot.

## Time Complexity
___
O(n)
Because  we store the whole prefix array.
## Code (first try!):
___
```go
func pivotIndex(nums []int) int {
    prefix := make([]int, len(nums) + 1) // to have one more at the start
    
    // fill out the prefix array; first element is 0 by default
    for i := 1; i < len(prefix); i++ {
        prefix[i] = prefix[i-1] + nums[i-1]
    }
    
    // check every pivot
    for i := 0; i < len(nums); i++ {
        leftSum := prefix[i]
        rightSum := prefix[len(prefix)-1] - prefix[i+1]
        if leftSum == rightSum {
            return i
        }
    } 
    return -1
}
```