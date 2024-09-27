#solution 
#two-pointers 
#pointer-to-each
## Problem
___
[LINK](https://www.interviewbit.com/problems/intersection-of-sorted-arrays/)

>[!Note]- Problem Description
> /*
> Problem Description
>  
> 
> Find the intersection of two sorted arrays OR in other words, given 2 sorted arrays, find all the elements which occur in both arrays.
> 
> NOTE: For the purpose of this problem ( as also conveyed by the sample case ), 
> assume that elements that appear more than once in both arrays should be included multiple times in the final output.
> 
> 
> Problem Constraints
> 1 <= |A| <= 106
> 1 <= |B| <= 106
> 
> 
> Input Format
> The first argument is an integer array A.
> The second argument is an integer array B.
> 
> 
> Output Format
> Return an array of intersection of the two arrays.
> 
> 
> Example Input
> Input 1:
> A: [1 2 3 3 4 5 6]
> B: [3 3 5]
> 
> Input 2:
> A: [1 2 3 3 4 5 6]
> B: [3 5]
> 
> 
> Example Output
> Output 1: [3 3 5]
> 
> Output 2: [3 5]
> 
> 
> Example Explanation
> Explanation 1:
> 
> 3, 3, 5 occurs in both the arrays A and B
> 
> Explanation 2:
> 
> Only 3 and 5 occurs in both the arrays A and B
> 
> 
> 
> */
> 
> // My input: 0 0 1 3 10 11
> // My output: 0 3 11
> 
> 
> // Time: O(n)
> // Space: O(n)



## Solution Idea ___
Get two pointers. If numbers are equal - move both pointers. If one is smaller - move that pointer.

## Special Test Cases
___
```
xxx
```

## Time Complexity
___
**O(n)** - where n is the amount of elements in both arrays.
Because we walk over both arrays.

## Space Complexity
___
**O(n)**
Because at the end we will store an 

## My Code:
___
```go


```

> [!Attention]
> - 


## Example solution:
___
[Video](VIDEO_LINK)

```go


```