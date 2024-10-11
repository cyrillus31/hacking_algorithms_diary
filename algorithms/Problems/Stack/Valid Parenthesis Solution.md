#solution 
#stack 
## Problem
___
[LINK](https://leetcode.com/problems/valid-parentheses/description/)

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

Example 1:

Input: s = "()"

Output: true

Example 2:

Input: s = "()[]{}"

Output: true

Example 3:

Input: s = "(]"

Output: false

Example 4:

Input: s = "([])"

Output: true

 

Constraints:

1 <= s.length <= 104
s consists of parentheses only '()[]{}'.

My input: '(){[}]'
My output: 'false'

## Solution Idea
___
USE STACK

## Special Test Cases
___
```
"["
"]"
```

## Time Complexity
___
**O(n)** 
Because we do some action on every element in the input array.

## Space Complexity
___
**O(n)**
Because at worst we will put all elements on the stack and that's it.

## My Code:
___
```go
func isValid(s string) bool {
    stack := make([]rune, 0)
    par := map[rune]rune{
        '(': ')',
        '{': '}',
        '[': ']',
    }

    for _, char := range s {
        // if char is open - push onto the stack
        if _, ok := par[char]; ok {
            stack = append(stack, char)
        } else if len(stack) > 0 {
            // else check the stack
            // if stack has valid - pop
            last := stack[len(stack)-1]
            if char == par[last] {
                // POP
                stack = stack[:len(stack)-1]
            } else {
                // if invalid - return false 
                return false
            }
        } else {
            return false
        }
    }
    return len(stack) == 0
}

```

> [!Attention]
> - Check the size of the stack during execution
> - Check the size of the stack at the end
> - Pop from stack in go is `stack = stack[:len(stack)-1]`




## Example solution:
___
[Video](VIDEO_LINK)

```go


```