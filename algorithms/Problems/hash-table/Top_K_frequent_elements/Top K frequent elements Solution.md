
#hash-table
#solution
#frequency-list

>[!Note] Time complexity
> O(n + n + n + n + n) = O(n)
> 1.  Walk over `n` elements to create a map
> 2. Create a frequency list of length `n` max
> 3. Insert into that list not more than `n` elements
> 4.  Walk over frequency list of `n` elements
> 5. Extract maximum `n` elements out of that frequency list



>[!Note] Space complexity
> O(n) = O(n)
> 1. Create a map that stores `n` key-value pairs
> 2. 

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

	// now we need to work with frequencies and therefore
    // create frequencyList out of that map
    fList := make([][]int, len(nums)+1)
    for num, freq := range countMap {
        fList[freq] = append(fList[freq], num)
    }

    // get the result
    result := make([]int, 0, k)
    for i := len(nums); i > 0; i-- {
        elems := fList[i]
        if len(elems) != 0 {
            result = append(result, elems...)
        }
        if len(result) == k {
            return result
        }
    }
    return result // just to saticfy a compiler who doesn't know that solution is guaranteed
}
```