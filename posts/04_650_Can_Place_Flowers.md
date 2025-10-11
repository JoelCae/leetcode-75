
# 605 Can Place Flowers [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

You have a long flowerbed in which some of the plots are planted, and
some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array **flowerbed** containing **0**’s and **1**’s,
where **0** means empty and **1** means not empty, and an integer **n**,
return **true** if **n** new flowers can be planted in the **flowerbed**
without violating the no-adjacent-flowers rule and **false** otherwise.

**Examples**

- Example 1:
  - Input: flowerbed = \[1,0,0,0,1\], n = 1
  - Output: true
- Example 2:
  - Input: flowerbed = \[1,0,0,0,1\], n = 2
  - Output: false

**Constraints:**

- 1 ≤ **flowerbed.length** ≤ 2 x $10^4$
- **flowerbed\[i\]** is 0 or 1
- There are no two adjacent flowers in flowerbed
- 0 ≤ **n** ≤ flowerbed.length

## SOLUTION [^3]

``` r
flowers <- function(flowerbed, n) {
  count <- 0  # count a flower planted 
  i <- 1 
  # in each iteration evaluate if a plant can be planted, and sum in the count
    # there are not a flower in i or i-1 or i+1
    # for the first element the check in i-1 is not needed
    # for the last element the check in i+1 is not needed
  while(i <= length(flowerbed)) {
    if(flowerbed[i] == 0 &&
       (i == 1 || flowerbed[i-1] == 0) &&
       (i == length(flowerbed) || flowerbed[i+1] == 0)){
      flowerbed[i] <- 1  
      count <- count + 1 
    }
    i <- i + 1 
  }
  return(count >= n)
}
```

**Examples using the function**

``` r
flowers(c(1,0,0,0,1), 1)
```

    ## [1] TRUE

``` r
flowers(flowerbed = c(1,0,0,0,1), n = 2)
```

    ## [1] FALSE

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/can-place-flowers/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
