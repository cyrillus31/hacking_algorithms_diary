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
**O(n)**
Because we just walk over the main arrays.

## Space Complexity
___
O(n)
Because if each prefix sum in unique  - the length of prefix sum array will be at max  `n`


## Code:
___
```go
func subarraySum(nums []int, k int) int {
    curSum := 0
    count := 0
    prefix := map[int]int{0: 1}
    for _, num := range nums {
        curSum = curSum + num
        diff := curSum - k
        if encounters, ok := prefix[diff]; ok {
            count = count + encounters
        }
        prefix[curSum]++
    }
    return count
}
```
