#fails 
## First try
___
```go
func intersect(A []int , B []int )  ([]int) {
    aPointer := 0
    bPointer := 0
    result := []int{}
    for aPointer < len(A) || bPointer < len(B) {
        aElem := A[aPointer]
        bElem := B[bPointer]
        if aElem == bElem {
            aPointer, bPointer = aPointer + 1, bPointer + 1
            result = append(result, aElem)
        } else if aElem < bElem {
            aPointer++
        } else {
            bPointer++
        }
    }
    return result
}
```

**PROBLEM:**

**SOLUTION:**



## Second try
____
```go



```

**Explanation:**
