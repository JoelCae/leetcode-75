
# 1679 Max Number of K-Sum Pairs [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

You are given an integer array **nums** and an integer **k**.

In one operation, you can pick two numbers from the array whose sum
equals **k** and remove them from the array.

Return the maximum number of operations you can perform on the array.

**Examples**

- Example 1:
  - Input: nums = \[1,2,3,4\], k = 5
  - Output: 2
  - Explanation: Starting with nums = \[1,2,3,4\]:
    - Remove numbers 1 and 4, then nums = \[2,3\]
    - Remove numbers 2 and 3, then nums = \[\] There are no more pairs
      that sum up to 5, hence a total of 2 operations.
- Example 2:
  - Input: nums = \[3,1,3,4,3\], k = 6
  - Output: 1
  - Explanation: Starting with nums = \[3,1,3,4,3\]:
    - Remove the first two 3’s, then nums = \[1,4,3\] There are no more
      pairs that sum up to 6, hence a total of 1 operation.

**Constraints:**

- 1 ≤ **nums.length** ≤ $10^{5}$

- 1 ≤ **nums\[i\]** ≤ $10^{9}$

- 1 ≤ **k** ≤ $10^{9}$

## SOLUTION [^3]

``` r
ksum_pairs <- function(nums, k){
  nums1 <- nums
  count <- 0 # start the number of operations
  
  # in each iteration take the i-element and 
    # evaluate if satisfy the sum with other number in nums
  while (length(nums1) > 1) { # it is need at least 2 elements
    # check if i-element with other sum to k (in vector check)
    dif <- k - nums1[1] 
    nums1 <- nums1[-1] # drop the i-element
    check <- nums1 == dif 
    
    if(sum(check) > 0){ # if at least one element satisfies sum
      id <- c(1:length(check))
      # drop just the first element that satisfies the sum
       # others could be used in next iterations
      nums1 <- nums1[-id[check][1]]
      count <- count + 1 # sum 1 to the number of operations
    } 
  }
  return(count)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
ksum_pairs(nums = c(1,2,3,4), k = 5)
```

    ## [1] 2

``` r
ksum_pairs(c(3,1,3,4,3),6)
```

    ## [1] 1

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/max-number-of-k-sum-pairs/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
