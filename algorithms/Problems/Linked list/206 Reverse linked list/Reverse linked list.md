Leetcode 206

#solution 
#linked-list 
## Problem
___
[LINK](https://leetcode.com/problems/reverse-linked-list/description/)
Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

**Input:** head = [1,2,3,4,5]
**Output:** [5,4,3,2,1]

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)

**Input:** head = [1,2]
**Output:** [2,1]

**Example 3:**

**Input:** head = []
**Output:** []

**Constraints:**

- The number of nodes in the list is the range `[0, 5000]`.
- `-5000 <= Node.val <= 5000`

## Solution Idea
___

## Special Test Cases
___
```
Empty linked list

Single value linked list

```

## Time Complexity
___
**O(n)** 
Because it can not be faster

## Space Complexity
___
**O(1)**
Because we don't use any additional memory
## My Code:
___

## My cleanest solution

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    var left *ListNode
    right := head
    for right != nil {
        tmp := right
        right = right.Next
        tmp.Next = left
        left = tmp
    }
    return left
}
```
#### Dumb solution
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
    var rightNode *ListNode = nil
    if midNode == nil {
        return nil
    }
    if midNode.Next == nil {
        return midNode
    }
    for midNode.Next != nil {
        rightNode = midNode.Next
        midNode.Next = leftNode
        leftNode = midNode
        midNode = rightNode 
    }
    midNode.Next = leftNode
    return midNode
}


```

> [!Attention]
> -  Check for edge cases first!
> - Try to do without the third element


## Example solution:
___
[Video](https://kinescope.io/ikJozq5g6YAEmbRQXrRuNn)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */


// time: O(n)
// mem: O(1)
func reverseList(head *ListNode) *ListNode {
	// на каждом шаге curr двигаем по листу на 1 ноду вперед,
	// а prev - поддерживает массив в котором будет ответ, т е

	// если есть изначально массив
	// 1 -> 2 -> 3 -> 4 -> 5 -> None

	// то через несколько шагов он будет таким
	// None <- 1 <- 2      3 -> 4 -> 5 -> None
	//            prev    curr

	// таким образом в prev мы получим конечный ответ
	var prev *ListNode
	var curr *ListNode = head
	for curr != nil {
		tmp := curr
		curr = curr.Next
		tmp.Next = prev
		prev = tmp
	}
	return prev
}

```