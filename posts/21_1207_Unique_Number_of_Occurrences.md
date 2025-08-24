
# 1207 Unique Number of Occurrences [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given an array of integers **arr**, return **true** if the number of
occurrences of each value in the array is unique or **false** otherwise.

**Examples**

- Example 1:
  - Input: arr = \[1,2,2,1,1,3\]
  - Output: true
  - Explanation: The value 1 has 3 occurrences, 2 has 2 and 3 has 1. No
    two values have the same number of occurrences.
- Example 2:
  - Input: arr = \[1,2\]
  - Output: false
- Example 3:
  - Input: arr = \[-3,0,1,-3,1,1,1,-3,10,0\]
  - Output: true

**Constraints:**

- 1 ≤ **arr.length** ≤ 1000
- -1000 ≤ **arr\[i\]** ≤ 1000

## SOLUTION [^3]

``` r
unique_occ <- function(arr){
  # find the unique values in arr
  unique_val <- unique(arr)
  
  # in each iteration, save the occurrences of i-element in arr
  vec_occ <- c() # vector of occurrences 
  for (i in unique_val) {
    vec_occ <- c(vec_occ, sum(arr == i))
  }
  
  # if each value has a different occurrence, the total number of 
    # unique values is equal to the number of unique occurrences 
    # in the vector vec_occ
  result <- length(unique_val) == length(unique(vec_occ))
  
  print(result)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
unique_occ(c(1,2,2,1,1,3))
```

    ## [1] TRUE

``` r
unique_occ(c(1,2))
```

    ## [1] FALSE

``` r
unique_occ(c(-3,0,1,-3,1,1,1,-3,10,0))
```

    ## [1] TRUE

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/unique-number-of-occurrences/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
