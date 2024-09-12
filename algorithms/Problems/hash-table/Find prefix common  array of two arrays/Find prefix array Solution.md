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
>**Мой воперос:**
> > Привет! Решаю задачу про общий префикс массива и у меня назрело несколько вопросов. Сперва, вот мое решение:
>>Вопросы:
>>1) Что можете сказать по решению? Бот сказал все чисто, но порекомендовал использовать питонячий оператор get, чтобы проверить наличие ключа и достать значение в одну строку, с его слов 😅😅😅
>>2) @YFatMR в своем решении использует frequencyList, а я - мапу. Использовать слайс это неасимптотическая оптимизация, чтобы не тратить время на хэширование? Или есть другое преимущество использования фриквенси листа?
>>3) Я на го не пишу, только учу. Меня поругают за if countMap[aNum] == 2 {cur++} в одну строчку?
>>4) Constraints в условиях задач обычно для меня очень мало о чем говорят. Как их правильно использовать? На что вы обычно обращаете внимание, когда читаете ограничения?
>
>**Ответ Макса:**
>>1) главное, чтобы тебе было оно понятно - работает оптимально. Вполне чисто
>>2) Можно и мапу, там тоже будет фиксированная память. Какого-то четкого определения дать не могу. Просто для себя заметил, что лучше юзать явно массив вместо мапы просто чтобы было понятнее что фикс память, а так ничем - просто кому как понятнее
>>Есть небольшие накладни у Map в целом, но не критично
>>
>>3) Да ХЗ, зависит от интервьюера. У вас явно написано в гайде не придираться к синтаксису. Но для меня лично это не оч похоже на Go style
>>
>>4) На leetcode их особо никак не поиспользуешь - они там в одной задаче что-то говорят, а в другой нет. Так что в самом начале будет сложно понять что они означают. А вот на собесе просто можно поспрашивать про ограничения, чтобы понять какие есть, чтобы прийти к оптимальному решению быстрее


### Решение Макса
```go
func findThePrefixCommonArray(nums1 []int, nums2 []int) []int {
    result := make([]int, 0, len(nums1))
    frequency := make([]int, len(nums1)+1)

    common := 0
    for i := 0; i < len(nums1); i++ {
        frequency[nums1[i]]++
        frequency[nums2[i]]++

        // если общий элемент, то +1 к общим элементам на префиксе
        if nums1[i] == nums2[i] {
            common++
            result = append(result, common)
            continue
        }

        // если до этого уже встречали nums1[i], то +1
        if frequency[nums1[i]] == 2 {
            common++
        }
        // если до этого уже встречали nums2[i], то +1
        if frequency[nums2[i]] == 2 {
            common++
        }

        result = append(result, common)
    }
    return result
}
>```