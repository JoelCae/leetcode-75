
# 1456 Maximum Number of Vowels in a Substring of Given Length [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given a string **s** and an integer **k**, return the maximum number of
vowel letters in any substring of **s** with length **k**.

Vowel letters in English are **‘a’**, **‘e’**, **‘i’**, **‘o’**, and
**u’**.

**Examples**

- Example 1:
  - Input: s = “abciiidef”, k = 3
  - Output: 3
  - Explanation: The substring “iii” contains 3 vowel letters.
- Example 2:
  - Input: s = “aeiou”, k = 2
  - Output: 2
  - Explanation: Any substring of length 2 contains 2 vowels.
- Example 3:
  - Input: s = “leetcode”, k = 3
  - Output: 2
  - Explanation: “lee”, “eet” and “ode” contain 2 vowels.

**Constraints:**

- 1 ≤ **s.length** ≤ $10^{5}$
- **s** consists of lowercase English letters.
- 1 ≤ **k** ≤ **s.length**

## SOLUTION [^3]

``` r
max_vowels <- function(s, k){
  s_split <- strsplit(s, "")[[1]]
  # define the first max for the k-first elements in s
  max_vo <- sum(grepl(pattern = "[aeiou]", s_split[1:k]))
  # case if the k == length of s
  if (k == length(s)) {
    return(max_vo)
  } else {
    # in each iteration, calculate the number of vowels in the subarray s[i:i+k-1]
    max_ext <- length(s_split) - k + 1 
    for (i in 2:max_ext) {  # max_ext: max value to get a k-length subarray 
      ext <- i+k-1
      # calculate the number of vowels
      val <- sum(grepl(pattern = "[aeiou]", s_split[i:ext]))
      # and compare with the max
      max_vo <- ifelse(max_vo > val, max_vo, val)
    }
    return(max_vo)
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
max_vowels("abciiidef", 3)
```

    ## [1] 3

``` r
max_vowels("aeiou", 2)
```

    ## [1] 2

``` r
max_vowels("leetcode", 3)
```

    ## [1] 2

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
