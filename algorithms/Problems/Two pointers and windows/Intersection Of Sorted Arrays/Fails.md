#fails 
#two-pointers 
#pointer-to-each
## First try
___
```go
func intersect(A []int , B []int )  ([]int) {
    aPointer := 0
    bPointer := 0
    result := []int{}
    for aPointer < len(A) || bPointer < len(B) { // !PROBLEM: SHOULD BE BOTH AT THE SAME TIME
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

**PROBLEM:** Index out of range \[9] with length 9

**SOLUTION:** pointer A and pointer B should be in bounds BOTH



## Second try
____
```go



```

**Explanation:**
