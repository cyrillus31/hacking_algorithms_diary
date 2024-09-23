#fails #array #prefix_array 
## First try (wrong idea)
___
```go
func subarraySum(nums []int, k int) int {
    prefix := make([]int, len(nums)+1)
    result := 0
    // calculate prefix sum array
    for i := 1; i < len(prefix); i++ {
        prefix[i] = prefix[i-1] + nums[i-1]
    }
    l := 0
    r := 1
    for l <= r && l < len(nums) && r < len(nums) {
        sum := prefix[r+1] - prefix[l]
        if sum == k { // PROBLEM: this condition should also change pointers
            result++
        } else if sum < k && r < len(nums) {
            r++
        } else if sum > k && l < len(nums) {
            l++
        }
    }
    return result
}
```

**PROBLEM:** Time limit exceeded. Obviously, I am stuck in a infinite loop here. Let's try and figure out what's wrong with my condition here. 

**SOLUTION:** I wasn't increasing `l` or `r` on each condition inside the loop! First condition didn't move any pointer!

## Second try (still wrong idea)
____
```go
func subarraySum(nums []int, k int) int {
    prefix := make([]int, len(nums)+1)
    result := 0
    // calculate prefix sum array
    for i := 1; i < len(prefix); i++ {
        prefix[i] = prefix[i-1] + nums[i-1]
    }
    l := 0
    r := 1 //PROBLEM: this should be 0
    for l <= r && l < len(nums) && r < len(nums) {
        sum := prefix[r+1] - prefix[l]
        if sum == k {
            result++
            if l == r {
                r++
            } else {
                l++
            }
        } else if sum < k {
            r++
        } else if sum > k {
            l++
        }
    }
    return result
}
```

**PROBLEM:** when nums = \[1\] it was returning 0

**SOLUTION:** I was not accounting for the fact that the sum can  be created out of the first element itself.












