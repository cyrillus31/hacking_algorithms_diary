#fails 
#two-pointers 
#windows #sliding-window
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

**PROBLEM:**  `r` goes out of bounds since `r+1` can be bigger than `len(nums)`
**SOLUTION:** limit the loop to `r < len(nums) - 1`



## Second try
____
```go
func findMaxAverage(nums []int, k int) float64 {
    maxSum := 0
    for _, num := range nums[0:k] {
        maxSum = maxSum + num
    }
    l := 0
    r := k - 1
    for r < len(nums) - 1 {
        newSum := maxSum - nums[l] + nums[r+1] // !PROBLEM: use current sum instead of maxSum
        maxSum = max(newSum, maxSum)
        l++
        r++
    }
    return float64(maxSum) / float64(k)
}
```

**PROBLEM:**  Wrong Answer: `[0,4,0,3,2]` the result returned is 7.0 when it was supposed to be 4.0. 
**SOLUTION:** It was due to the fact that newSum was calculated not using a previous sum but by using maxSum