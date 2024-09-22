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

**Explanation:**
Time limit exceeded. Obviously, I am stuck in a infinite loop here. Let's try and figure ou



## Second try
____
```go



```

**Explanation:**
