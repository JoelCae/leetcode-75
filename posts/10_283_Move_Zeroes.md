
# 283 Move Zeroes [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an integer array **nums**, move all **0**’s to the end of it while
maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

**Examples**

- Example 1:
  - Input: nums = \[0,1,0,3,12\]
  - Output: \[1,3,12,0,0\]
- Example 2:
  - Input: nums = \[0\]
  - Output: nums = \[0\]

**Constraints:**

- 1 ≤ **nums.length** ≤ $10^4$
- \-$2^{31}$ ≤ **nums\[i\]** ≤ $2^{31}$ - 1

## SOLUTION [^3]

``` r
zeroes <- function(nums){
  # vectors: zeroes and non zeroes
  nums1 <- nums[nums != 0]
  nums0 <- nums[nums == 0]
  
  # add in the final vector
  return(c(nums1, nums0))
}
```

**Examples using the function**

We can use the examples presented before.

``` r
zeroes(c(0,1,0,3,12))
```

    ## [1]  1  3 12  0  0

``` r
zeroes(c(0))
```

    ## [1] 0

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/move-zeroes/description/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
