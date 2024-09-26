#fails 
#two-pointers 
#fast-and-slow-pointers
## First try
___
```go
func moveZeroes(nums []int) {
    slow := 0
    fast := -1
    for slow < len(nums) - 1 {
        // move fast pointer on every iteration
        fast++
        left := nums[slow]
        right := nums[fast]
        // move slow pointer when switch WAS done
        if left == 0 && right != 0 {
            nums[slow], nums[fast] = nums[fast], nums[slow]
            slow++
        // move slow pointer when switch CAN NOT be done
        } else if left != 0 && right != 0 {
            slow++
        }
        // when switch is possible but can't be done right now, keep the slow pointer in place
    }
}
```

**PROBLEM:** Fast pointer goes out of bounds of the array.

**SOLUTION:** Just care about the fast pointer position.

## Second try
____
```go



```

**Explanation:**
