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

    // citat     [3, 0, 6, 1, 5]
    // amount    [0, 1, 0, 1, 0, 2]
    // citations  0  1  2  3  4  5

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
Ошибка: result всегда 0. Это значит, что если cit меньше amount, то cit меньше result. Либо это значит, что если cit больше либо равно amount, то amount меньше result. Но разве это всегда так?

Короче я подумал и понял: проверять надо было не с конца массива, а сначала (надо делать i++)