
# 151 Reverse Words in a String [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an input string **s**, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in
**s** will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single
space.

Note that **s** may contain leading or trailing spaces or multiple
spaces between two words. The returned string should only have a single
space separating the words. Do not include any extra spaces.

**Examples**

- Example 1:
  - Input: s = “the sky is blue”
  - Output: “blue is sky the”
- Example 2:
  - Input: s = ” hello world ”
  - Output: “world hello”
- Example 3:
  - Input: s = “a good example”
  - Output: “example good a”

**Constraints:**

- 1 \<= **s.length** \<= 3 \* $10^4$
- **s** contains English letters (upper-case and lower-case), digits,
  and spaces **’ ’**.
- There is at least one word in **s**.

## SOLUTION [^3]

``` r
word_reverse <- function(s){
  # split by blank space 
  s_split <- strsplit(s, split = " ")
  # check if S only contain blank spaces
  noword<- ifelse(length(grep(pattern = "^\\s*$", s)) ==1, T, F) 
  l_s <- length(s_split[[1]])
  
  # conditions 
  if(l_s == 0  | noword == TRUE ) {
    if (l_s == 0 ) {warning("Length of s have to be >= 1")}
    if ( noword  == 1) {warning("s have to have at least one word")}
  }
  else {
    # identify more that one blank space 
    spac<- s_split[[1]] == ""
    s_split_wospac <- s_split[[1]][!spac]
    # reverse without blank spaces
    result <- paste(rev(s_split_wospac), collapse = " ")
    return(result)
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
word_reverse("the sky is blue")
```

    ## [1] "blue is sky the"

``` r
word_reverse( s = "  hello world  ")
```

    ## [1] "world hello"

``` r
word_reverse( s = "a good   example")
```

    ## [1] "example good a"

In addition, we can also check the restrictions.

``` r
word_reverse("")
```

    ## Warning in word_reverse(""): Length of s have to be >= 1

    ## Warning in word_reverse(""): s have to have at least one word

``` r
word_reverse("    ")
```

    ## Warning in word_reverse(" "): s have to have at least one word

[^1]: This problem is originally from Leetdode, you can find it in
    [Leetcode](https://leetcode.com/problems/reverse-words-in-a-string/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to receive your message.

[^3]: This solution is entirely my authorship. I used R version 4.4.1
    (2024-06-14 ucrt).
