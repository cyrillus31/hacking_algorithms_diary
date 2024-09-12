#solution
#hash-table

### Problem
You are given two **0-indexed** integer permutations `A` and `B` of length `n`.

A **prefix common array** of `A` and `B` is an array `C` such that `C[i]` is equal to the count of numbers that are present at or before the index `i` in both `A` and `B`.

Return _the **prefix common array** of_ `A` _and_ `B`.

A sequence of `n` integers is called a **permutation** if it contains all integers from `1` to `n` exactly once.

**Example 1:**

**Input:** A = [1,3,2,4], B = [3,1,2,4]
**Output:** [0,2,3,4]
**Explanation:** At i = 0: no number is common, so C[0] = 0.
At i = 1: 1 and 3 are common in A and B, so C[1] = 2.
At i = 2: 1, 2, and 3 are common in A and B, so C[2] = 3.
At i = 3: 1, 2, 3, and 4 are common in A and B, so C[3] = 4.

**Example 2:**

**Input:** A = [2,3,1], B = [3,1,2]
**Output:** [0,1,3]
**Explanation:** At i = 0: no number is common, so C[0] = 0.
At i = 1: only 3 is common in A and B, so C[1] = 1.
At i = 2: 1, 2, and 3 are common in A and B, so C[2] = 3.


## My solution idea
Walk over both arrays and each time count how many times we've encountered a certain number. 
If both 


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