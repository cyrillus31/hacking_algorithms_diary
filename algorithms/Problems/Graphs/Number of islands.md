#solution 
#graph
#dfs #bfs
## Problem
___
[LINK](https://leetcode.com/problems/number-of-islands/description/)

>[!Note]- Problem description
Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.
An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
Example 1:
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
Example 2:
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
Constraints:
m == grid.length
n == grid[i].length
1 <= m, n <= 300
grid[i][j] is '0' or '1'.

## Solution Idea
___
Apply bfs or dfs for every peace of land. 
- If original array can be changed - change land to water in place
- If original array can not be changed - create a \[]\[]bool array to store visited nodes.


## Special Test Cases
___
```
---

```

## Time Complexity
___
**O(n\*m)** where n\*m is the size of the original array
Because because we have to walk over each element once. 

## Space Complexity
___
**O(n\*m)** where n\*m is the size of the original array
Because stack or queue in worst case can take all in all of the origin elements.

## My Code:
___
```go
func dfs(grid [][]byte, x_start, y_start int) {
    stack := [][]int{[]int{x_start, y_start}}
    directions := [][]int{
        []int{1, 0},
        []int{0, 1},
        []int{-1, 0},
        []int{0, -1},
    }
    for len(stack) > 0 {
        // pop
        var point []int
        stack, point = stack[:len(stack)-1], stack[len(stack)-1] // ATTENTION! DON'T RECREATE 'stack' here again! Don't use :=
        // current point
        cur_x, cur_y := point[0], point[1]
        // make water
        grid[cur_x][cur_y] = '0'
        //neighbours
        for _, dir := range directions {
            x_dif, y_dif := dir[0], dir[1]
            new_x := cur_x + x_dif
            new_y := cur_y + y_dif
            if new_x < 0 || new_x > len(grid) - 1 {
                continue
            }
            if new_y < 0 || new_y > len(grid[0]) - 1 {
                continue
            }
            if grid[new_x][new_y] == '1' {
                // push on stack
                stack = append(stack, []int{new_x, new_y})
            }
        }
    }
}

func numIslands(grid [][]byte) int { 
    result := 0
    // check all cells from 0, 0 to n, m
    for x := 0; x < len(grid); x++ {
        for y := 0; y < len(grid[0]); y++ {
            if grid[x][y] == '1' {
                dfs(grid, x, y)
                result++
            }
        }
    }
    return result
}

```

> [!Attention]
> - Don't use walrus operator (:=) when popping from the slice! It will create a slice confined to the current !


## Example solution:
___
[Video](VIDEO_LINK)

```go


```