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

**PROBLEM:** if the first element is ']' then we check for -1 element on the stack

**SOLUTION:** account for the size of the stack during execution
## Second try
____
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
    return true  // !PROBLEM: didn't take size of the array into account }
```

**PROBLEM:** when input '\[' we return true
**SOLUTION:** Didn't account for the size of the array in the end