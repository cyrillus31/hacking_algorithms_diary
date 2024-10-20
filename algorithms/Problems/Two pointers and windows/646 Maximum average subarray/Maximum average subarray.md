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
Calculate the sum for the first array of length `k`. Remember it as maximum. Then move the window to the right and calculate maximums for each next window. Calculating the sum for the next window is simpler if you take the previous array and remove the first element and push the next element to the right of the array.
## Special Test Cases
___
```
[0,4,0,3,2]
k = 1
result = 4
```

## Time Complexity
___
**O(n)**  or to be more precise O(k(n-k+1))
Because we just walk over the array one time.
## Space Complexity
___
**O(1)**
Because we don't any memory save the storing of the maxSum and curSum

## My Code:
___
```go
# First solution. First move pointers outside the loop.
func findMaxAverage(nums []int, k int) float64 {
    maxSum := 0
    for _, num := range nums[0:k] {
        maxSum = maxSum + num
    }
    prevSum := maxSum
    l := 1
    r := k
    for r < len(nums) {
        prevSum = prevSum - nums[l-1] + nums[r]
        maxSum = max(maxSum, prevSum)
        l++
        r++
    }
    return float64(maxSum) / float64(k)
}
```

```Python
# First solution but in python
class Solution:
    def findMaxAverage(self, nums: list[int], k: int) -> float:
        max_sum = sum(nums[0:k])
        l = 0
        r = k - 1
        prev_sum = max_sum
        l += 1
        r += 1
        while r < len(nums):
            prev_sum = prev_sum - nums[l-1] + nums[r]
            max_sum = max(max_sum, prev_sum)
            l += 1
            r += 1
        return max_sum / k

```

```go
// Second solution. Move pointers inside the loop always
func findMaxAverage(nums []int, k int) float64 {
    maxSum := 0
    for _, num := range nums[0:k] {
        maxSum = maxSum + num
    }
    l := 0
    r := k - 1
    curSum := maxSum
    for r < (len(nums) - 1) {
        curSum = curSum - nums[l] + nums[r+1] // BEWARE NOT TO USE := HERE
        maxSum = max(curSum, maxSum)
        l++
        r++
    }
    return float64(maxSum) / float64(k)
}
```

> [!Attention]
> -  Make sure that while using golang you don't create a loop-scoped variable prevSum instead of using 'global' prevSum!!! That's the most important tip.

## Example solution:
___
[Video](VIDEO_LINK)

```go


```