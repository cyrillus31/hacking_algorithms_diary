#solution 
#binary-search
#leetcode
## Problem
___
[LINK](https://leetcode.com/problems/binary-search/description/)

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
 

Constraints:

1 <= nums.length <= 104
-104 < nums[i], target < 104
All the integers in nums are unique.
nums is sorted in ascending order.


## Solution Idea
___
Divide our array into two parts. One which suffices a condition `<= target` and the other that doesn't. Pick a left pointer inside the array. Pick a right pointer outside the array so that a left pointer can potentially find the result.
Pick a middle index. If an element at the middle index satisfies the condition - move left pointer to `m`. If it doesn't - move the right pointer to `m`. Do it until `l < r`.
Since in our condition we decided that our left pointer can potentially find the target (and the right pointer can not find it), at the end we check if the left pointer points to our target. If it does - return `l`. If it doesn't - return `-1`.

## Special Test Cases
___
```

```

## Time Complexity
___
**O(log(n))** 
Because we do a binary search. How many times can we divide 8 in half and then divide that half in half? Three times. And log(8) is 3.

## Space Complexity
___
**O(1)**
Because we use constant space.

## My Code:
___
```go
func search(nums []int, target int) int {
    result := -1
    l := 0
    r := len(nums)
    for l < r {
        m := (l + r) / 2
        if nums[m] == target {
            return m
        } else if nums[m] < target {
            l = m + 1
        } else {
            r = m
        }
    }
    return result
}

```

> [!Attention]
> - Beware of the condition of the loop. If you don't check the `nums[m] == target` on every step - you have stop exactly when pointers are next to each other. (why?)

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        def is_good(value: int) -> bool:
            return value <= target

        l = 0
        r = len(nums)
        while l < r - 1:
            m = (l + r) // 2
            if is_good(nums[m]):
                l = m
            else:
                r = m
        if nums[l] == target:
            return l
        return -1
```

## Example solution:
___
[Video](VIDEO_LINK)

```go
// time: O(log n)
// mem:  O(1)
func search(nums []int, target int) int {
	// ответ будет находится в элементе указывающим на l
	// поэтому сдвигаем r на 1 вправо, чтобы l мог принимать
	// значения [0, len(nums) - 1] т е от первого и до последнего
	// индекса включительно
	l, r := 0, len(nums)
	for r-l > 1 {
		m := (l + r) / 2
		if good(nums[m], target) {
			l = m
		} else {
			r = m
		}
	}
	if nums[l] == target {
		return l
	}
	return -1
}

func good(val, target int) bool {
	return val <= target
}

```