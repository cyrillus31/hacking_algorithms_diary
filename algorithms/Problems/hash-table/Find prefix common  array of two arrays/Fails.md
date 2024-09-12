#solution
#hash-table

# First attempt
```go
func findPrefixCommonArray(A []int, B []int) []int {
    // create map to count repeated elements
    countMap := make(map[int]int)
    result := make([]int, len(A))
    
    // start walking over the array
    for i := 0; i < len(A); i++ {
        aElement := A[i]
        bElement := B[i]

        // if the element is in map and was encountered two times - add 1 to the result at the current index
        if val, ok := countMap[aElement]; ok {
            if val == 2 {
                result[i]++
            }
        } else {
            // if element was not in the map then say that it was ecountered for the first time
            countMap[aElement] = 1
        }
        if val, ok := countMap[bElement]; ok {
            if val == 2 {
                result[i]++
            }
        } else {
            countMap[bElement] = 1
        }
    }
    return result
}
```

>[!Warning] Mistakes
> Похоже, что я не увеличиваю счетчик в мапе. Result в конце оказывается массивом, заполненным 0. Не срабатывает val == 2 условие, очевидно. 