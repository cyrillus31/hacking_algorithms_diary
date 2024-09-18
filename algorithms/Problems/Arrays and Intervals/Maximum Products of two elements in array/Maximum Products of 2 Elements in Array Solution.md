## Porblem
Given the array of integers `nums`, you will choose two different indices `i` and `j` of that array. _Return the maximum value of_ `(nums[i]-1)*(nums[j]-1)`.

**Example 1:**

**Input:** nums = [3,4,5,2]
**Output:** 12 
**Explanation:** If you choose the indices i=1 and j=2 (indexed from 0), you will get the maximum value, that is, (nums[1]-1)*(nums[2]-1) = (4-1)*(5-1) = 3*4 = 12. 

**Example 2:**

**Input:** nums = [1,5,4,5]
**Output:** 16
**Explanation:** Choosing the indices i=1 and j=3 (indexed from 0), you will get the maximum value of (5-1)*(5-1) = 16.

**Example 3:**

**Input:** nums = [3,7]
**Output:** 12

**Constraints:**

- `2 <= nums.length <= 500`
- `1 <= nums[i] <= 10^3`


## Complexity

*Time: O(n)*
Because we walk over all elements.

*Space: O(1)*
Because we only store two elements at a time.

## Solution Idea
To solve this we will need to find two biggest elements. To do this we will have to walk over all of the elements storing the biggest element and the second biggest. 
1) If a new element is bigger than the biggest - put it as a biggest.
	1) ATTENTION: but put the one that was the biggest in place of the second biggest!
2) If a new element is smaller than the biggest check if it is bigger than the second biggest.

## My solution
```go
func maxProduct(nums []int) int {
    min := 0
    max := 0
    for _, num := range nums {
        if num > max {
            if max > min {
                min = max
            }
            max = num
        } else if num <= max && num > min {
            min = num
        }
    }
    return (min-1)*(max-1)
}
```



## Max's solution
```go
func maxProduct(nums []int) int {
  // time: O(n)
  // mem: O(1)
	maxNum := 0
	secondMaxNum := 0
	for _, num := range nums {
		if num > maxNum {
			secondMaxNum = maxNum
			maxNum = num
		} else {
			secondMaxNum = max(secondMaxNum, num)
		}
	}

	return (maxNum - 1) * (secondMaxNum - 1)
}
```