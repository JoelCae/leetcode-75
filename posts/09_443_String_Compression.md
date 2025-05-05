
# 443 String Compression [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an array of characters **chars**, compress it using the following
algorithm:

Begin with an empty string **s**. For each group of consecutive
repeating characters in **chars**:

- If the group’s length is **1**, append the character to **s**.
- Otherwise, append the character followed by the group’s length.

The compressed string **s** should not be returned separately, but
instead, be stored in the input character array **chars**. Note that
group lengths that are **10** or longer will be split into multiple
characters in **chars**.

After you are done modifying the input array, return the new length of
the array.

You must write an algorithm that uses only constant extra space.

**Examples**

- Example 1:
  - Input: chars = \[“a”,“a”,“b”,“b”,“c”,“c”,“c”\]
  - Output: Return 6, and the first 6 characters of the input array
    should be: \[“a”,“2”,“b”,“2”,“c”,“3”\]
- Example 2:
  - Input: chars = \[“a”\]
  - Output: Return 1, and the first character of the input array should
    be: \[“a”\]
- Example 3:
  - Input: chars =
    \[“a”,“b”,“b”,“b”,“b”,“b”,“b”,“b”,“b”,“b”,“b”,“b”,“b”\]
  - Output: Return 4, and the first 4 characters of the input array
    should be: \[“a”,“b”,“1”,“2”\]

**Constraints:**

- 1 ≤ chars.length ≤ 2000
- chars\[i\] is a lowercase English letter, uppercase English letter,
  digit, or symbol

## SOLUTION [^3]

``` r
compress <- function(chars){
  if(length(chars) < 1 ) {
    if (length(chars) < 1 ) {warning("Length of chars must be ≥ 1")}
  } 
  else {
    # find changes of letters
    split <- NULL
    for (i in 2:length(chars)) {
      dif <- chars[i] == chars[i-1]
      split <- c(split, dif)
    }
    split <- grep("FALSE", split)
    split <- c(0,split, length(chars)) 
    
    # add to final vector
    s <- NULL
    # case simple (no repeat)
    for( i in 2:length(split)) {
      if (split[i] - split[i-1] == 1 ) {
        s <- c(s, chars[i-1] )
      }
      # case with repeats
      else {s <- c(s, chars[i-1], split[i] - split[i-1]) }
    }
    # count the characters
    s <- paste(s, collapse = "")
    s <- strsplit(s, "")[[1]]
    return(length(s))
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
compress(c("a","a","b","b","c","c","c"))
```

    ## [1] 6

``` r
compress(chars = c("a","b","b","b","b","b","b","b","b","b","b","b","b"))
```

    ## [1] 4

``` r
compress(c("a"))
```

    ## [1] 1

In addition, we can also check the restrictions.

``` r
compress(c())
```

    ## Warning in compress(c()): Length of chars must be ≥ 1

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/string-compression/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
