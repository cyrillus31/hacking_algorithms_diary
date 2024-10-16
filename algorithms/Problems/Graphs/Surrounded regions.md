#solution 
#THEME
## Problem
___
[LINK](https://leetcode.com/problems/surrounded-regions/description/)

PROBLEM_DESCRIPTION...

## Solution Idea
___


## Special Test Cases
___
```

```

## Time Complexity
___
**O(?)** 
Because

## Space Complexity
___
**O(?)**
Because

## My Code:
___
>[!Error] Too slow
![[Pasted image 20241016085433.png]]

```go
func solve(board [][]byte) {
    // capturable
    // captured
    // dfs && currentIsland
    // apply captured to currentIsland
    isCapturable := func(x, y int) bool {
        return x >= 1 && y >= 1 && x < len(board) - 1 && y < len(board[0]) - 1 && board[x][y] == 'O'
    }
    captured := make([][]bool, len(board))
    for i, _ := range captured {
       captured[i] = make([]bool, len(board[0]))
    }
    directions := [][]int{
        []int{1, 0},
        []int{0, 1},
        []int{-1, 0},
        []int{0, -1},
    }
    dfs := func(x, y int) {
        visited := make([][]bool, len(board))
        for i, _ := range visited {
            visited[i] = make([]bool, len(board[0]))
        }
        stack := [][]int{[]int{x, y}}
        // pop
        for len(stack) > 0 {
            var point []int
            stack, point = stack[:len(stack)-1], stack[len(stack)-1]
            if ! isCapturable(point[0], point[1]) {
                return
            }
            visited[point[0]][point[1]] = true
            for _, dir := range directions {
                new_x, new_y := point[0] + dir[0], point[1] + dir[1]  // ATTENTION I was adding to x and y always.
                if isCapturable(new_x, new_y) && visited[new_x][new_y] == false {
                    visited[new_x][new_y] = true
                    stack = append(stack, []int{new_x, new_y})
                } else if board[new_x][new_y] == 'X'{ // ATTENTION!
                    continue
                } else if ! isCapturable(new_x, new_y) {
                    return
                }
            }
        }
        for x := 0; x < len(board); x++ {
            for y := 0; y < len(board[0]); y++ {
                if visited[x][y] == true {
                    captured[x][y] = true
                }
            }
        }
    }
    // run dfs
    for x := 0; x < len(board); x++ {
        for y := 0; y < len(board[0]); y++ {
            if captured[x][y] == false {  // ATTENTION don't forget to check if the point was already visited.
                dfs(x, y)
            }
        }
    }
    // change the board according to captured
    for x := 0; x < len(board); x++ {
        for y := 0; y < len(board[0]); y++ {
            if captured[x][y] == true {
                board[x][y] = 'X'
            }
        }
    }
}

```

> [!Attention]
> - 


## Example solution:
___
[Video](VIDEO_LINK)

```go


```