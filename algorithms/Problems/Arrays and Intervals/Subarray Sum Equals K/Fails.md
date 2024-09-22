#fails #array #prefix_array 
## First try
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
        if sum == k {
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

## Second try
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
    r := 1
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

**SOLUTION:** I wasn't increasing `l` or `r` on each condition inside the loop! First condition didn't move any pointer!












