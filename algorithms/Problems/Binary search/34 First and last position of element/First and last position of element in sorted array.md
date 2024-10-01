#solution 
#binary-search 
## Problem
___
[LINK](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/submissions/1407881380/)

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Example 3:

Input: nums = [], target = 0
Output: [-1,-1]
 

Constraints:

0 <= nums.length <= 105
-109 <= nums[i] <= 109
nums is a non-decreasing array.
-109 <= target <= 109


My input:
nums = [123] target = 123



My output:
[0, 0]



## Solution Idea
___
Just do a regular binary with two pointers but keep in mind which pointer will have the answer in the end. Run binary search twice two find first and last element.

## Special Test Cases
___
```
[] //  VERY IMPORTANT TEST CASE!
(-1, -1)
```

## Time Complexity
___
**O(log(n))** 
Because just binary search twice

## Space Complexity
___
**O(1)**
Because just binary search twice

## My Code:
___
```go
func searchRange(nums []int, target int) []int {
    result := []int{-1, -1}
    l := -1
    r := len(nums) - 1
    for l < r - 1 {
        m := (l + r) / 2
        if nums[m] < target {
            l = m
        } else {
            r = m
        }
    }
    if nums[r] == target {
        result[0] = r
    }
    
    l = 0
    r = len(nums)
    for l < r - 1 {
        m := (l + r) / 2
        if nums[m] <= target {
            l = m
        } else {
            r = m
        }
    }
    if nums[l] == target {
        result[1] = l
    }    
    return result
}
```

> [!Attention]
> -  Don't forget to process edge case where `nums` length is zero!!!
> - Beware which pointer will have the answer. 
> -  Beware that the pointer that is going to have the answer should be able to walk over the whole array (start included). The other pointer shall start outside the array.


## Example solution:
___
[Video](VIDEO_LINK)

```go
func searchLastTarget(nums []int, target int) int {
	// ответ будет находится в элементе указывающим на l
	// поэтому сдвигаем r на 1 вправо, чтобы l мог принимать
	// значения [0, len(nums) - 1] т е от первого и до последнего
	// индекса включительно
	l, r := 0, len(nums)
	for r-l > 1 {
		m := (l + r) / 2
		if nums[m] <= target {
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

func searchFirstTarget(nums []int, target int) int {
	// ответ будет находится в элементе указывающим на r
	// поэтому сдвигаем l на 1 влево, чтобы r мог принимать
	// значения [0, len(nums) - 1] т е от первого и до последнего
	// индекса включительно
	l, r := -1, len(nums)-1
	for r-l > 1 {
		m := (l + r) / 2
		if nums[m] < target {
			l = m
		} else {
			r = m
		}
	}
	if nums[r] == target {
		return r
	}
	return -1
}

func searchRange(nums []int, target int) []int {
	if len(nums) == 0 {
		return []int{-1, -1}
	}
	l := searchFirstTarget(nums, target)
	r := searchLastTarget(nums, target)
	return []int{l, r}
}
```