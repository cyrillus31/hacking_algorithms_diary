#solution 
#two-pointers 
## Problem
___
[LINK](PLACEHOLDER)

>[!Note]- Problem Description
> Placeholder


## Solution Idea
___


## Special Test Cases
___


## Time Complexity
___
**O(n)** 
Because

## Space Complexity
___
**O(?)**
Because

## My Code:
___
```go
func twoSum(numbers []int, target int) []int {
    l := 0
    r := len(numbers) - 1
    for l < r {
        left := numbers[l]
        right := numbers[r]
        want := target - left
        if right == want {
            return []int{l+1, r+1}
        }
        if right > want {
            r--
        } else {
            l++
        }
    }
    return []int{}
}

```

> [!Attention]-
> -  Don't forget to return in any case. Compiler doesn't know that there will be solution.


## Example solution:
___
[Video](VIDEO_LINK)

```go


```