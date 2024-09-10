```go
/*
Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

Example 1:

Input: s = "egg", t = "add"

Output: true

Explanation:

The strings s and t can be made identical by:

Mapping 'e' to 'a'.
Mapping 'g' to 'd'.
Example 2:

Input: s = "foo", t = "bar"

Output: false

Explanation:

The strings s and t can not be made identical as 'o' needs to be mapped to both 'a' and 'r'.

Example 3:

Input: s = "paper", t = "title"

Output: true

 

Constraints:

1 <= s.length <= 5 * 104
t.length == s.length
s and t consist of any valid ascii character.



Additional test cases:
Input: s = "massageq", t = "boggoreq"

Output: true

{
    m: b,
    a: o,
    s: g,
    g: r,
    e: e,
    q: q,
}

Time complexity: O(n) - where n is the amount of letters in a word
Because we have as many steps as there are letters in a single word.

Space complexity: O(1)
Beause we know the amount of possible symbols and therefore we know the size of hash tables.

Space complexity(general): O(k) - where k is the amount of all possible symbols 
This is a more general answer.

*/

// SOLUTION:
func isIsomorphic(s string, t string) bool {
    if len(s) != len(t) {return false}

    sMap := make(map[byte]byte)
    tMap := make(map[byte]byte)
    for i := 0; i < len(s); i++ {
        sLetter := s[i]
        tLetter := t[i]
        if value, ok := sMap[sLetter]; !ok {
            sMap[sLetter] = tLetter
        } else {
            if value != tLetter {return false}
        }

        if value, ok = tMap[tLetter]; !ok {
            tMap[tLetter] = sLetter
        } else {
            if value != sLetter {return false}
        }
    }
    return true
}
```