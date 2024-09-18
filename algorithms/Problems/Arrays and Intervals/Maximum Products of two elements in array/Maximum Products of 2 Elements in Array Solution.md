
*Time: O(n)*
Because we walk over all elements.

*Space: O(1)*
Because we only store two elements at a time.

## Solution
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