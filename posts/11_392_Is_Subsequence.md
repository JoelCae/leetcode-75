
# 392 Is Subsequence [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given two strings **s** and **t**, return **true** if **s** is a
subsequence of **t**, or **false** otherwise.

A subsequence of a string is a new string that is formed from the
original string by deleting some (can be none) of the characters without
disturbing the relative positions of the remaining characters. (i.e.,
“ace” is a subsequence of **“abcde”** while **“aec”** is not).

**Examples**

- Example 1:
  - Input: s = “abc”, t = “ahbgdc”
  - Output: true
- Example 2:
  - Input: s = “axc”, t = “ahbgdc”
  - Output: nums = false

**Constraints:**

- 0 ≤ **s.length** ≤ 100
- 0 ≤ **t.length** ≤ $10^{4}$
- **s** and **t** consist only of lowercase English letters.

## SOLUTION [^3]

``` r
subseq <- function(s, t){
  # split the string "s"
  s <- strsplit(s, "")
  
  # create pattern (t[1] + ... + t[2] + ... + t[n])
  pattern <- paste(s[[1]], collapse = "([a-z]*)")
  
  # evaluate the pattern
  result <- grepl(pattern, t)
  return(result)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
subseq("abc","ahbgdc")
```

    ## [1] TRUE

``` r
subseq(s = "axc", t = "ahbgdc")
```

    ## [1] FALSE

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/is-subsequence/description/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
