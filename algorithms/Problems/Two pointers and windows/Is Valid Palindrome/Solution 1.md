#solution
#two-pointers 
## Problem
___
[LINK](https://leetcode.com/problems/valid-palindrome/description/)

>[!Note]- Problem Description
>
> /*
> A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, 
> it reads the same forward and backward. Alphanumeric characters include letters and numbers.
> 
> Given a string s, return true if it is a palindrome, or false otherwise.
> 
>  
> 
> Example 1:
> 
> Input: s = "A man, a plan, a canal: Panama"
> Output: true
> Explanation: "amanaplanacanalpanama" is a palindrome.
> 
> Example 2:
> 
> Input: s = "race a car"
> Output: false
> Explanation: "raceacar" is not a palindrome.
> 
> Example 3:
> 
> Input: s = " "
> Output: true
> Explanation: s is an empty string "" after removing non-alphanumeric characters.
> Since an empty string reads the same forward and backward, it is a palindrome.
> 
>  
> 
> Constraints:
> 
>     1 <= s.length <= 2 * 105
>     s consists only of printable ASCII characters.
> 
> MyInput: s = "121"
> MyOutput: true
> 
> 
> How ASCII organized
> 
> non-alphanumeric
> numbers
> capital letters
> something?
> lowercase letters
> something?
> 
> Time: O(n)
> Space: O(1) or maybe O(0) ??
> */

## Valid palindrome solution
___
Use two pointers from left and right side and walk them towards each other. Check if a pointer points to an alphanumeric character and turn in into lowercase. Otherwise skip that character. 

## Special Test Cases
___
xxx

## Time Complexity
___
**O(n)** 
Because we use two pointers to walk over the array.

## Space Complexity
___
**O(1)**
Because we don't use any additional memory save pointers.


## My Code:
___
```go
const capitalDiff int32 = 'a' - 'A'

func toLower(r rune) rune {
    if 'A' <= r && r <= 'Z' {
        return capitalDiff + r
    }
    return r
}

func isAlphanumeric(r rune) bool {
    return ('0' <= r && r <= '9') || ('a' <= r && r <= 'z') || ('A' <= r && r <= 'Z')
}


func isPalindrome(s string) bool {
    l := 0
    r := len(s) - 1
    for l <= r {
        left := rune(s[l])
        right := rune(s[r])
        if ! isAlphanumeric(left) {
            l++
            continue
        }
        if ! isAlphanumeric(right) {
            r--
            continue
        }
        if toLower(left) != toLower(right) {
            return false
        }
        l++
        r--
    }
    return true
}
```

> [!Attention]-
> - My solution doesn't use standard library - that's a plus.
> - Make use of two variables declaration on one line


## Example solution:
___
[Video](https://kinescope.io/s9YYQkqxwKioSSPPXDNWrw)

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