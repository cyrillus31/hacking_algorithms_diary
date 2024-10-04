#solution 
#linked-list 
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
#### Not the best example!
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
> -  THERE HAS TO BE A PRETTIER WAY


## Example solution:
___
[Video](https://kinescope.io/bFfUgWxXRCEKjYFu6tgdLx)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
	// in:  1 -> 2 -> 3 -> None
	// out: 3 -> 2 -> 1 -> None
	// time: O(n)
	// mem: O(1)
	prev := (*ListNode)(nil)
	curr := head
	for curr != nil {
		tmp := curr
		curr = curr.Next
		tmp.Next = prev
		prev = tmp
	}
	return prev
}

// in:     1  ->  2  ->  3
// out:          mid

// in:     1  ->  2  ->  3  ->  4
// out:                 mid

// time: O(n)
// mem: O(1)
func middleNode(head *ListNode) *ListNode {
	// изначально ставим slow и fast на голову
	slow := head // будем двигать на 1 вперед
	fast := head // будем двигать на 2 вперед

	for fast != nil && fast.Next != nil {
		slow = slow.Next
		fast = fast.Next.Next
	}
	return slow
}

// time: O(n)
// mem: O(1)
func isPalindrome(head *ListNode) bool {
	firstHalfEndNode := middleNode(head)
	secondHalfBeginNode := reverseList(firstHalfEndNode)

	p1 := head
	p2 := secondHalfBeginNode
	// тут важно понимать как будет выглядеть связный список после манипуляций c поворотом
	
	//      p1            p2
	// in:  1  ->  2  ->  3
	// out: 1  ->  2  <-  3
	//            /
	//     None <|
	// т е из "2" идет в None

	//      p1                   p2
	// in:  1  ->  2  ->  3  ->  4
	// out: 1  ->  2  <-  3  <-  4
	//                   /
	//            None <|

	// теперь очевидно, что мы должны сравнивать значения в
	// нодах p1 и p2 пока p2 не станет None
	for p2 != nil && p1 != nil {
		if p1.Val != p2.Val {
			return false
		}
		p1 = p1.Next
		p2 = p2.Next
	}
	// по желанию можно вернуть список в изначальное состояние
	return true
}

```