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
        if right == target { // PROBLEM: you compare with target instead of WANT
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

**PROBLEM:** Input \[2,7,11,15] Return: \[]
That could only mean that right == target condition is never triggered. How could that be?

**SOLUTION:** The condition was comparing `right` with `target` instead of `want`.



## Second try
____
```go



```

**Explanation:**
