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
    leftNode := nil // PROBLEM: declare nil type?
    midNode := head
    rightNode := midNode.Next
    for midNode.Next { // PROBLEM: add nil check
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

**SOLUTION:** use comparison to `nil`, I think. And also declare nil type for the first `leftNode`



## Second try
____
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    var leftNode *ListNode = nil
    midNode := head
    rightNode := midNode.Next
    for midNode.Next != nil {
        midNode.Next = leftNode
        leftNode = midNode
        midNode = rightNode
        rightNode = rightNode.Next
    }
    rightNode.Next = midNode
    return rightNode
}


```

**PROBLEM:** invalid memory address or nil pointer dereferenc

**SOLUTION:** use comparison to `nil`, I think. And also declare nil type for the first `leftNode`








