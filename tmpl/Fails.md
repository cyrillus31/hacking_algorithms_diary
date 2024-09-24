#fails 
#two
## First try
___
```go
const capitalDiff byte = byte('a') - byte('A')

func toLower(r byte) byte {
    if byte('A') <= r && r <= byte('Z') {
        return capitalDiff + r
    }
    return r
}

func isAlphanumeric(r byte) bool {
    return (byte('0') <= r && r <= byte('9')) || (byte('a') <= r && r <= byte('z'))  // PROBLEM: this doesn't check for upper case
}


func isPalindrome(s string) bool {
    l := 0
    r := len(s) - 1
    for l <= r {
        left := s[l]
        right := s[r]
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

**PROBLEM:** "A man, a plan, a canal: Panama"
Wrongly returns *false*

**SOLUTION:** forgot about uppercase check in *isAlphanumeric* funciton



## Second try
____
```go



```

**Explanation:**
