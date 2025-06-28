
# 1004 Max Consecutive Ones III [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given a binary array **nums** and an integer **k**, return the maximum
number of consecutive **1**’s in the array if you can flip at most **k
0**’s.

**Examples**

- Example 1:
  - Input: nums = \[1,1,1,0,0,0,1,1,1,1,0\], k = 2
  - Output: 6
  - Explanation: \[1,1,1,0,0,<u>**1**,1,1,1,1,**1**</u>\] <br> Bolded
    numbers were flipped from 0 to 1. The longest subarray is
    underlined.
- Example 2:
  - Input: nums = \[0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1\], k = 3
  - Output: 10
  - Explanation:
    \[0,0,<u>1,1,**1**,**1**,1,1,1,**1**,1,1</u>,0,0,0,1,1,1,1\] <br>
    Bolded numbers were flipped from 0 to 1. The longest subarray is
    underlined.

**Constraints:**

- 1 ≤ **nums.length** ≤ $10^{5}$
- **nums\[i\]** is either **0** or **1**.
- 0 ≤ **k** ≤ **nums.length**

## SOLUTION [^3]

``` r
max_cons1 <- function(nums,k){
  # identify the position of 0s
  nums_i <- 1:length(nums)
  nums_0 <- nums_i[nums == 0]
  
  max_val <- k 
  
  # in each iteration, flip k-0s, and get the length of the 1s longest subarray 
  # this process only flip the nums[i] with 0
  max_ext <- length(nums_0) - k + 1 # consider to get k flips
  for (j in 1:max_ext) {
    ext <- j + k - 1
    flip <- nums_0[j:ext] # positions to flip
    
    # create the new nums with the flipped positions
    nums_alt <- nums
    nums_alt[flip] <- 1
    
    # auxiliar vectors to count the 1s longest subarray 
    nums_0_alt <- c(0,nums_i[nums_alt == 0], length(nums)+1)
    count_1 <- c()
    
    # get the length of the 1s longest subarray
    for (i in 1:length(nums_0_alt)) {
      count_1[i -1] <- nums_0_alt[i] - nums_0_alt[i - 1] - 1
    }
    max_count <- max(count_1) 
    
    # compare to get the maximun
    max_val <- ifelse(max_val > max_count, max_val, max_count)
    
  }
  return(max_val)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
max_cons1(c(1,1,1,0,0,0,1,1,1,1,0), 2)
```

    ## [1] 6

``` r
max_cons1(nums = c(0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1), k =3)
```

    ## [1] 10

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/max-consecutive-ones-iii/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
