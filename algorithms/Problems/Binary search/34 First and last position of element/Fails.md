#fails 
#binary-search 
## First try
___
```go
func searchRange(nums []int, target int) []int {
    result := []int{-1, -1}
    l := -1
    r := len(nums) - 1
    for l < r - 1 {
        m := (l + r) / 2
        if nums[m] < target {
            l = m
        } else {
            r = m
        }
    }
    if nums[r] == target {
        result[0] = r
    }
    
    l = 0
    r = len(nums)
    for l < r - 1 {
        m := (l + r) / 2
        if nums[m] <= target {
            l = m
        } else {
            r = m
        }
    }
    if nums[l] == target {
        result[1] = l
    }    
    return result
}
```

**PROBLEM:**

**SOLUTION:**



## Second try
____
```go



```

**Explanation:**
