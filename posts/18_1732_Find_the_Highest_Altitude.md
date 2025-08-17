
# 1732 Find the Highest Altitude[^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

There is a biker going on a road trip. The road trip consists of **n +
1** points at different altitudes. The biker starts his trip on point
**0** with altitude equal **0**.

You are given an integer array **gain** of length **n** where
**gain\[i\]** is the net gain in altitude between points **i** and **i +
1** for all (**0 \<= i \< n**). Return the highest altitude of a point.

**Examples**

- Example 1:
  - Input: gain = \[-5,1,5,0,-7\]
  - Output: 1
  - Explanation: The altitudes are \[0,-5,-4,1,1,-6\]. The highest is 1.
- Example 2:
  - Input: gain = \[-4,-3,-2,-1,4,3,2\]
  - Output: 0
  - Explanation: The altitudes are \[0,-4,-7,-9,-10,-6,-3,-1\]. The
    highest is 0.

**Constraints:**

- **n** == **gain.length**
- 1 ≤ **n** ≤ 100
- -100 ≤ **gain\[i\]** ≤ 100

## SOLUTION [^3]

``` r
hig_alt <- function(gain){
  alt <- 0 # first altitude 
  vec_alt <- c(0) # vector of altitudes 
  # in each iteration, obtain the altitude for the i-point 
  for (i in 1:length(gain)) {
    alt <- alt + gain[i] # the altitude in i-point
    vec_alt <- c(vec_alt,alt) # add to the vector of altitudes 
  }
  # get the highest altitude in the vector 
  max_alt <- max(vec_alt)
  print(max_alt)
}
```

**Examples using the function**

We can use the examples presented before.

``` r
hig_alt(c(-5,1,5,0,-7))
```

    ## [1] 1

``` r
hig_alt(c(-4,-3,-2,-1,4,3,2))
```

    ## [1] 0

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/find-the-highest-altitude/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
