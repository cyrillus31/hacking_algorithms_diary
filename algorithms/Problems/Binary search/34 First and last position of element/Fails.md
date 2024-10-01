#fails 
#binary-search 
## First try
___
```go
func searchRange(nums []int, target int) []int {
    result := []int{-1, -1}
	// !PROBLEM don't account for edge case: 
	// if len(nums) == 0 {return result}
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

**PROBLEM:** with input array length equal to zero

**SOLUTION:** just add an edge case



## Second try
____
```go



```

**Explanation:**
