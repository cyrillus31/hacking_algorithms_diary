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
    fList := [209][]int  //! THIS IS A TYPE! DO PROPER INITIALIZATION WITH {}
    
    for fNumber := range numsCount {
        fFreq := numsCount[fNumber]
        fList[fFreq] = append(fList[fFreq], fNumber] //! CLOSE APPEND PROPERLY WITH )
    }
    
    // getting the answer
    result := []int //! THIS IS A TYPE! DO PROPER INITIALIZATION WITH {}
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


### Second attempt
```go
func TopKFrequent(nums []int, k int) []int {
    // counting elemetns into a map
    numsCount := make(map[int]int)
    for num := range nums {
        if _, ok := numsCount[num]; ok {
            numsCount[num]++
        } else {
            numsCount[num] = 1
        }
    }

    // transfering counts into Frequency list
    fList := [209][]int{}
    
    for fNumber := range numsCount {
        fFreq := numsCount[fNumber]
        fList[fFreq] = append(fList[fFreq], fNumber)
    }
    
    // getting the answer
    result := []int{}
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

>[!warning] Wrong answer
>Input:
> nums = [1,1,1,2,2,3]
> 
> k =2
> 
> Output:
> 
> [0,1,2,3,4,5]
> 
> Expected
> 
> [1,2]


