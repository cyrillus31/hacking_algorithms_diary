#solution
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
**O(?)** - where 
Because 

## Space Complexity
___
**O(?)** - where 
Because 


## My Code:
___
```go
func isPalindrome(s string) bool {
    l, r := 0, len(s) - 1
    for l < r {
        // в условии сказано, что у нас ASCII символы, поэтому так делать можно
        leftRune, rightRune := rune(s[l]), rune(s[r])

        // переходим к следующей букве пока l и r
        // не будут указывать на буквы или цифры
        if !unicode.IsLetter(leftRune) && !unicode.IsDigit(leftRune) {
            l++
            continue
        }
        if !unicode.IsLetter(rightRune) && !unicode.IsNumber(rightRune) {
            r--
            continue
        }

        // оба символа - буквы или цифры
        if unicode.ToLower(leftRune) != unicode.ToLower(rightRune) {
            return false
        }
        l++
        r--
    }
    return true
}
```

## What to improve:
___


## Example solution:
___
```go

```