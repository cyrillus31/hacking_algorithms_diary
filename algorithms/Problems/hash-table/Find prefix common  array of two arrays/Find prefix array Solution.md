#solution
#hash-table

>[!Note] Time complexity
> **O(n)**
> 1. Walk over each element in arrays (2n)
> 2. With each element seen write to a hash map (2n)
> 3. Increment current value n times at worst
> 4. With each element write to the result array (n)

>[!Note] Space complexity
> **O(n)**
> 1. Create a map for `n` elements tops.
> 2. Write the result to a slice of `n` elements.

#### My solution:
```go
func findThePrefixCommonArray(A []int, B []int) []int {
    countMap := make(map[int]int)
    result := make([]int, len(A))
    cur := 0
    for i := 0; i < len(A); i++ {
        aNum := A[i]
        bNum := B[i]
        if _, ok := countMap[aNum]; ok {
            countMap[aNum]++
        } else {
            countMap[aNum] = 1
        }
        if _, ok := countMap[bNum]; ok {
            countMap[bNum]++
        } else {
            countMap[bNum] = 1
        }
        if aNum == bNum {cur++} else {
            if countMap[aNum] == 2 {cur++}
            if countMap[bNum] == 2 {cur++}         
        }
        result[i] = cur
    }
    return result
}
```


>[!Note] Комментарии Макса
> > Привет! Решаю задачу про общий префикс массива и у меня назрело несколько вопросов. Сперва, вот мое решение:

func findThePrefixCommonArray(A []int, B []int) []int {
    countMap := make(map[int]int)
    result := make([]int, len(A))
    cur := 0
    for i := 0; i < len(A); i++ {
        aNum := A[i]
        bNum := B[i]
        if _, ok := countMap[aNum]; ok {
            countMap[aNum]++
        } else {
            countMap[aNum] = 1
        }
        if _, ok := countMap[bNum]; ok {
            countMap[bNum]++
        } else {
            countMap[bNum] = 1
        }
        if aNum == bNum {cur++} else {
            if countMap[aNum] == 2 {cur++}
            if countMap[bNum] == 2 {cur++}         
        }
        result[i] = cur
    }
    return result
}

Вопросы:
1) Что можете сказать по решению? Бот сказал все чисто, но порекомендовал использовать питонячий оператор get, чтобы проверить наличие ключа и достать значение в одну строку, с его слов 😅😅😅
2) @YFatMR в своем решении использует frequencyList, а я - мапу. Использовать слайс это неасимптотическая оптимизация, чтобы не тратить время на хэширование? Или есть другое преимущество использования фриквенси листа?
3) Я на го не пишу, только учу. Меня поругают за if countMap[aNum] == 2 {cur++} в одну строчку?
4) Constraints в условиях задач обычно для меня очень мало о чем говорят. Как их правильно использовать? На что вы обычно обращаете внимание, когда читаете ограничения?
