### First attempt
```go
func TopKFrequent(nums []int, k int) []int {
    // counting elemetns into a map
    numsCount := make(map[int]int)
    for num := range nums {
        if val, ok := numsCount[num]; ok { //! VAL DECLARED AND NOT USED
            numsCount[num]++
        } else {
            numsCount[num] = 1
        }
    }

    // transfering counts into Frequency list
    fList := [209][]int  // how this data looks like after initialization?
    
    for fNumber := range numsCount {
        fFreq := numsCount[fNumber]
        fList[fFreq] = append(fList[fFreq], fNumber] //! CLOSE APPEND PROPERLY WITH )
    }
    
    // getting the answer
    result := []int
    for i := len(fList) - 1; i >= 0; i-- {
        if len(fList[i]) > 0 {
            result = append(result, fList[i]...)
        }
        if len(result) == k {
            return result
        }
    }
    return result  // do i need this? just to satisfy the compiler?
}
```



