# 1071 Greatest Common Divisor of Strings [^2]

## DESCRIPTION

For two strings **s** and **t**, we say “**t** divides **s**” if and
only if *s* = *t* + *t* + *t* + ... + *t* + *t* (i.e., t is concatenated
with itself one or more times). Given two strings **str1** and **str2**,
return the largest string **x** such that **x** divides both **str1**
and **str2**.

**Examples**

-   Example 1:
    -   Input: str1 = “ABCABC”, str2 = “ABC”
    -   Output: “ABC”
-   Example 2:
    -   Input: str1 = “ABABAB”, str2 = “ABAB”
    -   Output: “AB”
-   Example 3:
    -   Input: str1 = “LEET”, str2 = “CODE”
    -   Output: “”

**Constraints:**

-   1 \<= **str1.length**, **str2.length** \<= 1000
-   **str1** and **str2** consist of English uppercase letters.

## SOLUTION [^3]

``` r
divisor_str <- function(str1,str2){
  # split the words in letters
  split1 <-strsplit(str1,"")
  split2 <-strsplit(str2,"")
  l_w1 <- length(split1[[1]])
  l_w2 <- length(split2[[1]])
  
  # condition
  if(l_w1 < 1 | l_w2 < 1 | l_w1 > 100 | l_w2 > 100 ) {
    warning("Length of str1 and str2 have to be >= 1 and <= 1000")}
  
  # soluition
  else {
    result <- "" # it is the string x 
    string <- ifelse(l_w1<= l_w2, str1,str2)
    
    # in each interaction, evaluate if a base string divides str1 and str2
    for (i in 1:min(l_w1,l_w2)) {
      # string to evaluate. in each interaction, the string length is i 
      base_str <- substring(string,1,i) 
      if(l_w1%%i == 0 & l_w2%%i ==0) {
        # evaluate
        if (str1 == paste(rep( base_str,l_w1/i),collapse = "") 
            & str2 == paste(rep( base_str,l_w2/i),collapse = "") ) {
         result <- base_str }
        else {result <- ""}
      }
    }
    print(result)
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
divisor_str("ABABAB","ABAB")
```

    ## [1] "AB"

``` r
divisor_str(str1 = "LEET", str2 = "CODE")
```

    ## [1] ""

In addition, we can also check the restriction in the length of the
words.

``` r
divisor_str("","Hello")
```

    ## Warning in divisor_str("", "Hello"): Length of str1 and str2 have to be >= 1
    ## and <= 1000

[<kbd> <br> Previous <br> </kbd>](https://bing.com) [<kbd> <br> Next <br> </kbd>](https://bing.com)

[^1]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to receive your message.

[^2]: This problem is originally from Leetdode, you can find it in
    [Leetcode](https://leetcode.com/problems/greatest-common-divisor-of-strings/description/?envType=study-plan-v2&envId=leetcode-75).

[^3]: This solution is entirely my authorship. I used R version 4.4.1
    (2024-06-14 ucrt).
