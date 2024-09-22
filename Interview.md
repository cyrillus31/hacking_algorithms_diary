## Вопросы
- Всегда ли валидные данные?
- Сгенерируй краевые условия. 



 Если идут 0 и 1, то скорее всего можно математически избежать условия if
```go
func findMaxConsecutiveOnes(nums []int) int {
    count := 0
    maxCount := 0
    /*
    1 1 0 1 1
    1 2 0 1 2
    */ 
    for _, num := range nums {
        count = count*num + num
        if count > maxCount {
            maxCount = count
        }
    }
    return maxCount
}
```
Ошибка: я забыл про MaxCount

Расстояние редактирования.