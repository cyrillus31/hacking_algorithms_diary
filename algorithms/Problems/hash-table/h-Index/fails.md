# First fail

```go
func hIndex(citations []int) int {
    hList := make([]int, len(citations) + 1)
    result := 0
    for _, cit := range citations {
        if cit > len(citations) {
            cit = len(citations)
        }
        hList[cit]++
    }
    // amount    [0, 0, 3, 0, 0, 2, 5]
    // citations  0  1  2  3  4  5  6
    for i := len(citations); i < 0; i-- {
        cit = i
        amount := hList[cit]
        if cit < amount {
            if cit > result {
                result = cit
            }
        } else {
            if amount > result {
                result = amount
            }
        }
    }
    return result
}
```

Ошибка: на строках 13-17 (во втором цикле) используется переменная cit, которая не была объявлена! 


# Second attempt

```go
func hIndex(citations []int) int {
    hList := make([]int, len(citations) + 1)
    result := 0
    for _, cit := range citations {
        if cit > len(citations) {
            cit = len(citations)
        }
        hList[cit]++
    }
    // amount    [0, 0, 3, 0, 0, 2, 5]
    // citations  0  1  2  3  4  5  6
    for i := len(citations); i < 0; i-- {
        cit := i
        amount := hList[cit]
        if cit < amount {
            if cit > result {
                result = cit
            }
        } else {
            if amount > result {
                result = amount
            }
        }
    }
    return result
}
```
Ошибка: result всегда 0. Это значит, что cit и 