#fails #array 

```go
func isMonotonic(nums []int) bool {
    nonDecreasing := true
    nonIncreasing := true
    
    l := len(nums)
    if l <= 2 {
        return true
    }
    prev := nums[0]
    for i := 1; i < l; i++ {
        next := nums[i]
        if next >= prev {
            nonIncreasing = false
        } else if next <= prev {
            nonDecreasing = false
        }
        prev = next
    }
    return nonDecreasing || nonIncreasing
}
```

On input [6,5,4,4] it wrongly returns `false` instead of correct `true` since the array is obviously nonIncreasing. 

The problem was that when two numbers are equal in a row `nonDecreasing` and `nonIncreasing` both become false.