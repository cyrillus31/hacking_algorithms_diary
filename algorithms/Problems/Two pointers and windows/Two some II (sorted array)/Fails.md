#fails 
## First try
___
```go
func twoSum(numbers []int, target int) []int {
    l := 0
    r := len(numbers) - 1
    for l < r {
        left := numbers[l]
        right := numbers[r]
        want := target - left
        if right == target {
            return []int{l+1, r+1}
        }
        if right > want {
            r--
        } else {
            l++
        }
    }
    return []int{}
}
```

**PROBLEM:** 

**SOLUTION:**



## Second try
____
```go



```

**Explanation:**
