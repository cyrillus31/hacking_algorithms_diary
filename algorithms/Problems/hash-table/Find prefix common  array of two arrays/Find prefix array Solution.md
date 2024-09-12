#solution
#hash-table

>[!Note]- Time complexity
> O(n + n + n + n + n) = O(n)
> 1. Walk over each element in arrays (2n)
> 2. With each element seen write to a hash map (2n)
> 3. 

>[!Note] Space complexity
> O(n + n + n + n + n) = O(n)
> 1.  Walk over `n` elements to create a map
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


