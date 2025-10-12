
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
  - Explanation: Any triplet where i \< j \< k is valid.
- Example 2:
  - Input: nums = \[5,4,3,2,1\]
  - Output: false
  - Explanation: No triplet exists.
- Example 3:
  - Input: nums = \[2,1,5,0,4,6\]
  - Output: true
  - Explanation: The triplet (3, 4, 5) is valid because nums\[3\] == 0
    \< nums\[4\] == 4 \< nums\[5\] == 6.

**Constraints:**

- 1 ≤ **nums.length** ≤ $5*10^5$
- $-2^{31}$ ≤ **nums\[i\]** ≤ $2^{31}$ - 1

## SOLUTION [^3]

``` r
triple<- function(nums) {
  first <- Inf
  second <- Inf
  
  for (i in 1:length(nums)){
    # is nums[i] less than first element in subsequence?
    if(nums[i] <= first){
      first <- nums[i]
    #  is nums[i] less than first element in subsequence?
    } else if(nums[i] <= second){
      second <- nums[i]
    # then nums[i] is greater than first and second element in subsequence
    } else {return(TRUE)}
  }
  return(FALSE)
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
