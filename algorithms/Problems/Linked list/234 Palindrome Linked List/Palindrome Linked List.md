#solution 
## Problem
___
[LINK](https://leetcode.com/problems/palindrome-linked-list/submissions/)

Given the head of a singly linked list, return true if it is a
palindrome
or false otherwise.

 

Example 1:

Input: head = [1,2,2,1]
Output: true

Example 2:

Input: head = [1,2]
Output: false

 

Constraints:

    The number of nodes in the list is in the range [1, 105].
    0 <= Node.val <= 9

 
Follow up: Could you do it in O(n) time and O(1) space?

## Solution Idea
___
Split linked list in two. Reverse the right part. Compare them one by one.

## Special Test Cases
___
```
Empty list
One element list
```

## Time Complexity
___
**O(n)** 
Because we just walk over the linked list a few times.

## Space Complexity
___
**O(1)**
Because we don't use any additional memeory.

## My Code:
___
```go
func isPalindrome(head *ListNode) bool {
    if head == nil || head.Next == nil {
        return true
    }
    // Find the middle node
    slow := head
    fast := head
    for fast != nil && fast.Next != nil {
        if fast.Next.Next != nil {
            slow = slow.Next
        }
        fast = fast.Next.Next
    }
    leftEndNode := slow // mid or left of mid
    rightStartNode := slow.Next
    leftEndNode.Next = nil
    fmt.Println(leftEndNode.Val, rightStartNode)

    // reverse the rightList
    var prev *ListNode = nil
    next := rightStartNode
    for next != nil {
        tmp := next
        next = next.Next
        tmp.Next = prev
        prev = tmp
    }
    rightHead := prev

    // compare
    left := head
    right := rightHead
    fmt.Println(left, right)
    for right != nil {
        if right.Val != left.Val {
            return false
        }
        left, right = left.Next, right.Next
    }
    return true
}

```

> [!Attention]
> - 


## Example solution:
___
[Video](VIDEO_LINK)

```go


```