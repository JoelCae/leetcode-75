
# 334 Increasing Triplet Subsequence [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an integer array **nums**, return **true** if there exists a
triple of indices **(i, j, k)** such that **i \< j \< k** and
**nums\[i\] \< nums\[j\] \< nums\[k\]**. If no such indices exists,
return **false**.

**Examples**

- Example 1:
  - Input: nums = \[1,2,3,4,5\]
  - Output: true
- Example 2:
  - Input: nums = \[5,4,3,2,1\]
  - Output: false
- Example 3:
  - Input: nums = \[2,1,5,0,4,6\]
  - Output: true

**Constraints:**

- 1 ≤ **nums.length** ≤ 5\*$10^5$
- $-2^{31}$ ≤ **nums\[i\]** ≤ $2^{31}$ - 1

## SOLUTION [^3]

``` r
triple <- function(nums) {
  # possible triplets
  lxp <- length(nums) - 2 
  result <- FALSE
  for (i in 1:lxp)  {
    if(result == FALSE) {
      # in each iteration create a subvector
      vec_check <- nums[i:length(nums)]
      # there is i-elements > first element in the subvector
      vec_check <- vec_check[vec_check[1] < vec_check]
      lv = length(vec_check)
      # if at least 2 elements in the new vector -> check again
      if (lv > 1 ) {
        # repeating the first process
        for (i in 1:lv)  {
          if(result == FALSE) {
            vec_check1 <- vec_check[i:lv]
            vec_check1 <- vec_check1[vec_check1[1] < vec_check1]
            # if at least one element in the new vector -> condition is true
            result <-  ifelse(length(vec_check1) >= 1,TRUE,FALSE)
          } else {result <- TRUE} # maintain true 
        }
      }
    } else{result <- TRUE} # maintain true 
  }
  return(result)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
triple(c(1,2,3,4,5))
```

    ## [1] TRUE

``` r
triple(nums = c(5,4,3,2,1))
```

    ## [1] FALSE

``` r
triple(c(2,1,5,0,4,6))
```

    ## [1] TRUE

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/increasing-triplet-subsequence/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
