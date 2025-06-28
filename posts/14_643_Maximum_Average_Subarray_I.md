
# 643 Maximum Average Subarray I [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

You are given an integer array **nums** consisting of **n** elements,
and an integer **k**.

Find a contiguous subarray whose length is equal to **k** that has the
maximum average value and return this value. Any answer with a
calculation error less than $10^{-5}$ will be accepted.

**Examples**

- Example 1:
  - Input: nums = \[1,12,-5,-6,50,3\], k = 4
  - Output: 12.75000
  - Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 =
    12.75
- Example 2:
  - Input: nums = \[5\], k = 1
  - Output: 5.00000

**Constraints:**

- **n** == **nums.length**

- 1 ≤ **k** ≤ **n** ≤ $10^{5}$

- $-10^{4}$ ≤ **nums\[i\]** ≤ $10^{4}$

## SOLUTION [^3]

``` r
max_ave <- function(nums,k){
  max_v <- mean(nums[1:k]) # define the first max for the k-first elements in nums
  # case if the k == length of nums
  if (k == length(nums)){
    return(max_v) 
  } else {
    # in each iteration, calculate the mean for the subarray nums[i:i+k-1]
    max_ext <- length(nums) - k + 1 
    for (i in 2:max_ext) { # max_ext: max value to get a k-length subarray 
      ext <- i+k-1
      # calculate the mean 
      value <- mean(nums[i:ext])
      # and compare the mean with the max 
      max_v <- ifelse(max_v > value, max_v, value)
    }
    return(max_v)
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
max_ave(nums = c(5,2), k = 1)
```

    ## [1] 5

``` r
max_ave(nums = c(1,12,-5,-6,50,3), k = 4)
```

    ## [1] 12.75

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/maximum-average-subarray-i/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
