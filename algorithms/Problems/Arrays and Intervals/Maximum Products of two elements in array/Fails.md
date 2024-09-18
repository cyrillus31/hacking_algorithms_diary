```go
func maxProduct(nums []int) int {
    min := 0
    max := 0
    for _, num := range nums {
        if num > max {
            if max > min {
                min = max
            }
            max = num
        } else if num < max && num > min {  # NOTE: здесь должно быть num <= max
            min = num
        }
    }
    return (min-1)*(max-1)
}
```

Для [1,5,4,5] получил 12 вместо 16. Подозреваю, что не учел ситуация >=, когда ну нас может быть и в min и в max два одинаковых числа.