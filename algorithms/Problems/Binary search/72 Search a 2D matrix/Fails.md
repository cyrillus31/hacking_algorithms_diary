#fails 
#binary-search 
## First try
___
```go
func searchMatrix(matrix [][]int, target int) bool {
    // First off search the rows by looking at the frist element
    up := 0
    down := len(matrix)
    for down - up > 1 {
        m := (up + down) / 2
        if matrix[m][0] <= target {
            up = target // !PROBLEM: switch to m, not target!
        } else {
            down = target // !PROBLEM: switch to m, not target!
        }
    }
    row := up
    
    // Search the row
    l := 0  // left pointer included
    r := len(matrix[row])  // right pointer excluded
    for r - l > 1 {
        m := (l + r) / 2
        if matrix[row][l] <= target {  // !PROBLEM: use m pointer not l
            l = m
        } else {
            r = m
        }
    }
    return matrix[row][l] == target
}   


```

**PROBLEM:** Time limit exceeded. Obviously we are stuck in an infinite loop here somehow.

**SOLUTION:** Beware which pointers you use where! 
1) You are checking an element at m
2) You are moving l or r pointers to m



## Second try
____
```go



```

**Explanation:**
