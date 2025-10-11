
# 1768 Merge Strings Alternately [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

You are given two strings **word1** and **word2**. Merge the strings by
adding letters in alternating order, starting with **word1**. If a
string is longer than the other, append the additional letters onto the
end of the merged string.

Return the merged string.

**Examples**

- Example 1:
  - Input: word1 = “abc”, word2 = “pqr”
  - Output: “apbqcr”
  - Explanation: The merged string will be merged as so:
    - word1: a \_ b \_ c \_
    - word2: \_ p \_ q \_ r
    - merged: a p b q c r
- Example 2:
  - Input: word1 = “ab”, word2 = “pqrs”
  - Output: “apbqrs”
  - Explanation: Notice that as word2 is longer, “rs” is appended to the
    end.
    - word1: a \_ b \_
    - word2: \_ p \_ q r s
    - merged: a p b q r s
- Example 3:
  - Input: word1 = “abcd”, word2 = “pq”
  - Output: “apbqcd”
  - Explanation: Notice that as word1 is longer, “cd” is appended to the
    end.
    - word1: a \_ b \_ c d
    - word2: \_ p \_ q \_
    - merged: a p b q c d

**Constraints:**

- 1 ≤ **word1.length**, **word2.length** ≤ 100
- **word1** and **word2** consist of lowercase English letters

## SOLUTION [^3]

``` r
merg_str <- function(word1, word2){
  # split the words in letters
  split1 <-strsplit(word1,"")[[1]]
  split2 <-strsplit(word2,"")[[1]]
  max_len <- max(length(split1), length(split2))
  
  string <- "" # element that contains the merge
  
  # in each iteration, take an element per word 
  for (i in 1:max_len) { # to include all elements 
    if (i <= length(split1)){
      string <- c(string, split1[i])} 
    
    if (i <= length(split2)){
      string <- c(string, split2[i])}
  }
  string <- paste(string,collapse= "") 
  return(string)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
merg_str("abc","pqr")
```

    ## [1] "apbqcr"

``` r
merg_str(word1 = "ab", word2 = "pqrs")
```

    ## [1] "apbqrs"

``` r
merg_str(word1 = "abcd", word2 = "pq")
```

    ## [1] "apbqcd"

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
