
# 1493 Longest Subarray of 1’s After Deleting One Element [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given a binary array **nums**, you should delete one element from it.

Return the size of the longest non-empty subarray containing only
**1**’s in the resulting array. Return **0** if there is no such
subarray.

**Examples**

- Example 1:
  - Input: nums = \[1,1,0,1\]
  - Output: 3
  - Explanation: After deleting the number in position 2, \[1,1,1\]
    contains 3 numbers with value of 1’s.
- Example 2:
  - Input: nums = \[0,1,1,1,0,1,1,0,1\]
  - Output: 5
  - Explanation: After deleting the number in position 4,
    \[0,1,1,1,1,1,0,1\] longest subarray with value of 1’s is
    \[1,1,1,1,1\].
- Example 3:
  - Input: nums = \[1,1,1\]
  - Output: 2
  - Explanation: You must delete one element.

**Constraints:**

- 1 ≤ **nums.length** ≤ $10^{5}$
- **nums\[i\]** is either **0** or **1**.

## SOLUTION [^3]

``` r
long_sub <- function(nums){
  max_val <- 0 # the default value
  
  # in each iteration, drop i-element and get the 
    # length of the longest subarray of 1s
  for (i in 1:length(nums)) {
    nums_alt <- nums[-i]
    
    # create vector where i-element is 0 
    vector_1 <- c(0)  
    for (i in 1:length(nums_alt)) {
      if (nums_alt[i] == 0) {
        vector_1 <- c(vector_1, i) }
    }
    vector_1 <- c(vector_1, length(nums_alt) + 1)
    
    # auxiliary vector to count the subarrays
    count_1 <- c()
    
    for (i in 2:length(vector_1)) {
      count_1[i -1] <- vector_1[i] - vector_1[i - 1] - 1
    }
    
    # Get the length of the longest subarray of 1s
    max_count <- max(count_1) 
    
    # compare to get the maximum
    max_val <- ifelse(max_val > max_count, max_val, max_count)
  }
  return(max_val)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
long_sub(nums = c(1,1,0,1))
```

    ## [1] 3

``` r
long_sub(nums = c(0,1,1,1,0,1,1,0,1))
```

    ## [1] 5

``` r
long_sub(nums = c(1,1,1))
```

    ## [1] 2

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
