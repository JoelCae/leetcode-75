
# 238 Product of Array Except Self [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an integer array **nums**, return an array **answer** such that
**answer\[i\]** is equal to the product of all the elements of **nums**
except **nums\[i\]**.

The product of any prefix or suffix of **nums** is guaranteed to fit in
a 32-bit integer.

You must write an algorithm that runs in **O(n)** time and without using
the division operation.

**Examples**

- Example 1:
  - Input: nums = \[1,2,3,4\]
  - Output: \[24,12,8,6\]
- Example 2:
  - Input: nums = \[-1,1,0,-3,3\]
  - Output: \[0,0,9,0,0\]

**Constraints:**

- 2 ≤ **nums.length** ≤ $10^5$
- -30 ≤ **nums\[i\]** ≤ 30

## SOLUTION [^3]

``` r
prod_array <- function(nums){
  # vector with the result
  result <- c()
  
  for (i in 1:length(nums)) {
    # in each iteration, delete the nums[i]
    alt_num <- nums[-i]
    # obtain the product 
    result[i] <- prod(alt_num)
  }
  return(result)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
prod_array(c(1,2,3,4))
```

    ## [1] 24 12  8  6

``` r
prod_array(nums = c(-1,1,0,-3,3))
```

    ## [1] 0 0 9 0 0

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/product-of-array-except-self/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
