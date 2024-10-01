#fails 
## First try
___
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    leftNode := nil
    midNode := head
    rightNode := midNode.Next
    for midNode.Next {
        midNode.Next = leftNode
        leftNode = midNode
        midNode = rightNode
        rightNode = rightNode.Next
    }
    rightNode.Next = midNode
    return rightNode
}
```

**PROBLEM:** use of untyped nil in assignment + non-boolean condition in for statement

**SOLUTION:**



## Second try
____
```go



```

**Explanation:**
