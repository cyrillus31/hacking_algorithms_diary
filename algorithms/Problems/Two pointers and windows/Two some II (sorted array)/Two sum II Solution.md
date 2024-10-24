#solution 
#two-pointers 
## Problem
___
[LINK](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

>[!Note]- Problem Description
> Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, 
find two numbers such that they add up to a specific target number. 
Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.
> Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.
> 
> The tests are generated such that there is exactly one solution. You may not use the same element twice.
> 
> Your solution must use only constant extra space.
> 
>  
> 
> Example 1:
> 
> Input: numbers = [2,7,11,15], target = 9
> Output: [1,2]
> Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
> 
> Example 2:
> 
> Input: numbers = [2,3,4], target = 6
> Output: [1,3]
> Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
> 
> Example 3:
> 
> Input: numbers = [-1,0], target = -1
> Output: [1,2]
> Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
> 
>  
> 
> Constraints:
> 
>     2 <= numbers.length <= 3 * 104
>     -1000 <= numbers[i] <= 1000
>     numbers is sorted in non-decreasing order.
>     -1000 <= target <= 1000
>     The tests are generated such that there is exactly one solution.

## Solution Idea
___
Two pointer on the leftmost element and on the rightmost element. Left one is the smallest, right one is the largest. If we know our target and we know one element then we know what number we are missing. If the right pointer point to that number that we are missing we return the result. If it is bigger that the number that we are missing - we shift it to the left. If it is smaller - we shift the left pointer to the right. 

## Special Test Cases
___
```
[0,0,0] target = 0
[-2,0,2] target = 0
```


## Time Complexity
___
**O(n)** 
Because we walk over the whole array one time.

## Space Complexity
___
**O(1)**
Because we don't use any additional memory.

## My Code:
___
```go
func twoSum(numbers []int, target int) []int {
    l := 0
    r := len(numbers) - 1
    for l < r {
        left := numbers[l]
        right := numbers[r]
        want := target - left
        if right == want {
            return []int{l+1, r+1}
        }
        if right > want {
            r--
        } else {
            l++
        }
    }
    return []int{}
}

```

> [!Attention]
> -  Don't forget to return in any case. Compiler doesn't know that there will be solution.


## Example solution:
___
[Video](https://kinescope.io/c6yKmiiBWqYczvBVqsWDLx)

```go
func twoSum(nums []int, target int) []int {
	l := 0
	r := len(nums) - 1

	for l < r {
		currSum := nums[l] + nums[r]
		// если текущая сумма равна target
		// -> возвращаем индексы пары чисел
		if currSum == target {
			return []int{l + 1, r + 1}
		}
		// если текущая сумма больше target
		// -> сдвигаем правый указатель чтобы уменьшить общую сумму
		if currSum > target {
			r -= 1
		}
		// если текущая сумма больше target
		// -> сдвигаем левый указатель чтобы увеличить общую сумму
		if currSum < target {
			l += 1
		}
	}

	return []int{-1, -1}
}
```