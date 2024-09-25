#solution 
#two-pointers 
## Problem
___
 [LINK](https://leetcode.com/problems/container-with-most-water/description/)
 
>[!Note]- Problem Description
> Placeholder
> /*
> You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).
> 
> Find two lines that together with the x-axis form a container, such that the container contains the most water.
> 
> Return the maximum amount of water a container can store.
> 
> Notice that you may not slant the container.
> 
>  
> 
> Example 1:
> 
> Input: height = [1,8,6,2,5,4,8,3,7]
> Output: 49
> Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
> 
> Example 2:
> 
> Input: height = [1,1]
> Output: 1
> 
>  
> 
> Constraints:
> 
>     n == height.length
>     2 <= n <= 105
>     0 <= height[i] <= 104
> 
> */
> 
> // My input: [3,2,2,2,2,1]
> // My output: ...
> 
> 
> // Time: O(n)
> // Space: O(1)

## Solution Idea
___
Two pointers, one on the left and the other on the right. Calculate new area based on the smallest height. If this area is bigger that previous max area then overwrite it.
What about the pointers? If the height of at those pointers is equal then move them towards each other - it can't get any worse. Otherwise move the pointer to the smallest height to increase chances of increasing the amount of water you can fill in.


## Special Test Cases
___
```
[2,2,3,5,2,2]
result: 10
```

## Time Complexity
___
**O(n)** 
Because we just walk over our array with two pointers.

## Space Complexity
___
**O(n)**
Because the only memory we use is just storing the max area.

## My Code:
___
```go
func maxArea(hight []int) int {
    l := 0
    r := len(hight) - 1
    maxResult := 0
    for l < r {
        left := hight[l]
        right := hight[r]
        dist := r - l
        newArea := min(left, right) * dist
        maxResult = max(maxResult, newArea)
        if left == right {
            l++
            r--
        } else if left < right {
            l++
        } else if left > right {
            r--
        }
    }
    return maxResult
}

```

> [!Attention]
> - N


## Example solution:
___
[Video](VIDEO_LINK)

```go


```