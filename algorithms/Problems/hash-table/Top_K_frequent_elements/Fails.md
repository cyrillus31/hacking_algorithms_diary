#hash-table
#fails
#frequency-list
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


### Third attempt

```go
func topKFrequent(nums []int, k int) []int {
    // count elements with a map
    countMap := make(map[int]int)
    for _, elem := range nums {
        if _, ok := countMap[elem]; ok {
            countMap[elem]++
        } else {
            countMap[elem] = 1
        }
    }

    // create frequencyList
    fList := make([][]int, len(nums)+1)
    for num, freq := range countMap {
        fList[freq] = append(fList[freq], num)
    }

    // get the result
    result := make([]int, 0, k)
    for i := len(nums) - 1; i >= 0; i-- {
        elems := fList[i]
        if len(elems) != 0 {
            result = append(result, elems...)
        }
        if len(result) == k {
            return result
        }
    }
    return result
}
```

>[!warning] Mistakes
> Ошибся, полагая, что резльтаты нужно искать во фриквенси листе в диапазоне индексов от 0 до len - 1, когда на самом деле по первому индексу ничего не лежит! Потому, что у нас не может быть элемента с частотой 1. 
> Важно помнить, что во Frequency List по нулевому индексу будет пусто и его не надо брать в расчет!
