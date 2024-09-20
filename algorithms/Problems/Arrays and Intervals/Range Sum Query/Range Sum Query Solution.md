```go
type NumArray struct {
    prefix []int
}

func Constructor(nums []int) NumArray {
    prefix := make([]int, len(nums)+1)
    prefix[0] = 0
    runSum := 0
    for i := 1; i < len(prefix); i++ {
        cur := nums[i-1]
        runSum = runSum + cur
        prefix[i] = runSum
    }
    
    return NumArray{
        prefix: prefix,
    }
}

func (this *NumArray) SumRange(left int, right int) int {
    return this.prefix[right+1] - this.prefix[left]
}
```
