#fails 
#stack  
## First try
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
        } else {  // !PROBLEM: didn't account for the length of the stack here
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
        }
    }
    return len(stack) == 0
}
```

**PROBLEM:** if the first element is ']' the

**SOLUTION:**



## Second try
____
```go



```

**PROBLEM:**

**SOLUTION:**