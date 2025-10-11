
# 345 Reverse Vowels of a String [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given a string **s**, reverse only all the vowels in the string and
return it.

The vowels are **‘a’**, **‘e’**, **‘i’**, **‘o’**, and **‘u’**, and they
can appear in both lower and upper cases, more than once.

**Examples**

- Example 1:
  - Input: s = “IceCreAm”
  - Output: “AceCreIm”
  - Explanation: The vowels in s are \[‘I’, ‘e’, ‘e’, ‘A’\]. On
    reversing the vowels, s becomes “AceCreIm”.
- Example 2:
  - Input: s = “leetcode”
  - Output: “leotcede”

**Constraints:**

- 1 ≤ **s.length** ≤ 3 \* $10^5$
- **s** consist of printable ASCII characters.

## SOLUTION [^3]

``` r
string_reverse <- function(s){
  # split the string
  s_split <- strsplit(s, split = "")[[1]]   
  
  #get the vowels
  i_vowel <- grep(pattern = "[aeiouAEIOU]",s_split)
  
  # reverse of vowels 
  i_vowel_rev <- rev(i_vowel)
  
  # reverse the vowels in the string
  s_split[i_vowel] <- s_split[i_vowel_rev]
   
  result <- paste(s_split,collapse = "")
  return(result)

}
```

**Examples using the function**

We can use the examples presented before.

``` r
string_reverse("IceCreAm")
```

    ## [1] "AceCreIm"

``` r
string_reverse(s = "leetcode")
```

    ## [1] "leotcede"

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/reverse-vowels-of-a-string/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
