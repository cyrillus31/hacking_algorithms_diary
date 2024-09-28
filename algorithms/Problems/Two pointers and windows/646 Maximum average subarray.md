#fails 
## First try
___
```go
func findMaxAverage(nums []int, k int) float64 {
    maxSum := 0
    for _, num := range nums[0:k] {
        maxSum = maxSum + num
    }
    l := 0
    r := k - 1
    for r < len(nums) {
        newSum := maxSum - nums[l] + nums[r+1]
        maxSum = max(newSum, maxSum)
        l++
        r++
    }
    return float64(maxSum) / float64(k)
}
```

**PROBLEM:**  `r` goes out of bounds since r+1 can be bigger than len(nums)

**SOLUTION:**



## Second try
____
```go



```

**Explanation:**
