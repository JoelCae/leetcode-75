
# 724 Find Pivot Index [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an array of integers **nums**, calculate the pivot index of this
array.

The pivot index is the index where the sum of all the numbers strictly
to the left of the index is equal to the sum of all the numbers strictly
to the index’s right.

If the index is on the left edge of the array, then the left sum is
**0** because there are no elements to the left. This also applies to
the right edge of the array.

Return the leftmost pivot index. If no such index exists, return **-1**.

**Examples**

- Example 1:
  - Input: nums = \[1,7,3,6,5,6\]
  - Output: 3
  - Explanation: The pivot index is 3. Left sum = nums\[0\] +
    nums\[1\] + nums\[2\] = 1 + 7 + 3 = 11. Right sum = nums\[4\] +
    nums\[5\] = 5 + 6 = 11
- Example 2:
  - Input: nums = \[1,2,3\]
  - Output: -1
  - Explanation: There is no index that satisfies the conditions in the
    problem statement.
- Example 3:
  - Input: nums = \[2,1,-1\]
  - Output: -1
  - Explanation: The pivot index is 0.Left sum = 0 (no elements to the
    left of index 0). Right sum = nums\[1\] + nums\[2\] = 1 + -1 = 0

**Constraints:**

- 1 ≤ **nums.length** ≤ $10^4$
- -1000 ≤ **nums\[i\]** ≤ 1000

## SOLUTION [^3]

``` r
find_pivot <- function(nums){
  vec_pivot <- c()
  
  # To consider the pivot for the first and last element, 
   # aggregate 0 in the extremes of nums this don't alter the sums 
  nums_alt <- c(0,nums,0)
  
  max_pivot <- length(nums_alt)-1 #omit the last element
  for (i in 2:max_pivot){ # omit the first element 
    # get the left and the right sum
    i_left <- i-1
    i_right <- i+1
    left_sum <-  sum(nums_alt[1:i_left])
    right_sum <- sum(nums_alt[i_right:length(nums_alt)])
    
    # if the sums are equal, save this element as pivot index
    if(left_sum == right_sum) {
      vec_pivot <- c(vec_pivot,i)
    }
  }
  
  # if there are not pivot indexes, return -1
  if(length(vec_pivot) == 0){
    return(-1)
  } 
  # if there are pivot indexes, return the  leftmost
  else {return(vec_pivot[1]- 2)}
}
```

**Examples using the function**

We can use the examples presented before.

``` r
find_pivot(c(1,7,3,6,5,6))
```

    ## [1] 3

``` r
find_pivot(c(1,2,3))
```

    ## [1] -1

``` r
find_pivot(c(2,1,-1))
```

    ## [1] 0

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/find-pivot-index/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
