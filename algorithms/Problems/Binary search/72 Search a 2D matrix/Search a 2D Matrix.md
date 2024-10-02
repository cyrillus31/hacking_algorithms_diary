Leetcode 74
#solution 
#binary-search 
## Problem
___
[LINK](PLACEHOLDER)
You are given an m x n integer matrix matrix with the following two properties:

    Each row is sorted in non-decreasing order.
    The first integer of each row is greater than the last integer of the previous row.

Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

 

Example 1:

Input: matrix = \[[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true

Example 2:

Input: matrix = \[[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false

 

Constraints:

    m == matrix.length
    n == matrix[i].length
    1 <= m, n <= 100
    -104 <= matrix[i][j], target <= 104



## Solution Idea
___
1. Do a binary search over the first element of each row to find which row might include the target.
2. Do a binary search over that row to find the target.

## Special Test Cases
___
```

```

## Time Complexity
___
**O(log(n) + log(m)) = log(n\*m)*** 
Because we do a binary search over `n` elements. And then do a binary search over a row `m` elements.

## Space Complexity
___
**O(1)**
Because we don't use any additional memeory

## My Code:
___
```go
func searchMatrix(matrix [][]int, target int) bool {
    // First off search the rows by looking at the frist element
    up := 0
    down := len(matrix)
    for (down - up) > 1 {
        m := (up + down) / 2
        if matrix[m][0] <= target {
            up = m
        } else {
            down = m
        }
    }
    row := up
    
    // Search the row
    l := 0  // left pointer included
    r := len(matrix[row])  // right pointer excluded
    for (r - l) > 1 {
        m := (l + r) / 2
        fmt.Println(m)
        if matrix[row][m] <= target {
            l = m
        } else {
            r = m
        }
    }
    return matrix[row][l] == target
}   
```

> [!Attention]
> - 


## Example solution:
___
[Video](https://kinescope.io/0GboubeRnaMB9Mmajrex4p)

```go
// time: O(log (N * M))
// mem:  O(1)
func searchMatrix(matrix [][]int, target int) bool {
	// чтобы работать с 2-D массивом как с 1-D
	elementFromMatrix := func(i int) int {
		n := len(matrix[0])
		return matrix[i/n][i%n]
	}

	good := func(i int) bool {
		return elementFromMatrix(i) <= target
	}

	// обычный бинарный поиск как для 1-D массива
	l, r := 0, len(matrix)*len(matrix[0])
	for r-l > 1 {
		m := (l + r) / 2
		if good(m) {
			l = m
		} else {
			r = m
		}
	}
	return elementFromMatrix(l) == target
}

```