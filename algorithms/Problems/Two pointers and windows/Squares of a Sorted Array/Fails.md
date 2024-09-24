#fails 
## First try
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
        rSquared := nums[l] * nums[r]  // PROBLEM: look at that typo!
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

**PROBLEM:** 
Input: [-4, -1, 0, 3, 10]
Returns \[0, 0, 0, 1, 16] 
Correct \[0, 1, 9, 16, 100]

**SOLUTION:**
I had a dumb typo when calculating rSquared



## Second try
____
```go



```

**Explanation:**
