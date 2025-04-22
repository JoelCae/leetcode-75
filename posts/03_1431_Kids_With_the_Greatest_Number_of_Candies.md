
# 1431 Kids With the Greatest Number of Candies [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

There are **n** kids with candies. You are given an integer array
**candies**, where each **candies\[i\]** represents the number of
candies the **i<sup>th</sup>** kid has, and an integer **extraCandies**,
denoting the number of extra candies that you have.

Return a boolean array **result** of length **n**, where **result\[i\]**
is **true** if, after giving the **i<sup>th</sup>** kid all the
**extraCandies**, they will have the greatest number of candies among
all the kids, or **false** otherwise.

Note that multiple kids can have the greatest number of candies.

**Examples**

- Example 1:
  - Input: candies = \[2,3,5,1,3\], extraCandies = 3
  - Output: \[true,true,true,false,true\]
- Example 2:
  - Input: candies = \[4,2,1,1,2\], extraCandies = 1
  - Output: \[true,false,false,false,false\]
- Example 3:
  - Input: candies = \[12,1,12\], extraCandies = 10
  - Output: \[true,false,true\]

**Constraints:**

- **n** == **candies.length**
- 2 \<= **n** \<= 100
- 1 \<= **candies\[i\]** \<= 100
- 1 \<= **extraCandies** \<= 50

## SOLUTION [^3]

``` r
kids_candies <- function(candies,extraCandies){
  
  # conditions 
  if (length(candies) < 2 | length(candies) > 100 | 
      extraCandies < 1 |  extraCandies > 50 | 
      min(candies)<1  | max(candies)>100 ) {
    if(length(candies) < 2 | length(candies) > 100 ) {
      warning("Length of candies have to be >= 2 and <= 100")}
    if(extraCandies < 1 |  extraCandies > 50 ) {
      warning("extracadies have to be >=  1 and <= 50")}
    if(min(candies)<1  | max(candies)>100 ) {
      warning("candies[i] have to be >= 1  and <= 100")}
  }
  
  # solution
  else {
    # get the max in candies and evaluate with candies + extraCandies
    max_cand <- max(candies)
    result <- candies + extraCandies >= max_cand
    return(result)
  }
}
```

**Examples using the function**

We can use the examples presented before.

``` r
kids_candies(c(2,3,5,1,3),3)
```

    ## [1]  TRUE  TRUE  TRUE FALSE  TRUE

``` r
kids_candies(candies = c(12,1,12), extraCandies = 10)
```

    ## [1]  TRUE FALSE  TRUE

In addition, we can also check the restrictions.

``` r
kids_candies(c(11), 0)
```

    ## Warning in kids_candies(c(11), 0): Length of candies have to be >= 2 and <= 100

    ## Warning in kids_candies(c(11), 0): extracadies have to be >= 1 and <= 50

``` r
kids_candies(c(1,103),51)
```

    ## Warning in kids_candies(c(1, 103), 51): extracadies have to be >= 1 and <= 50

    ## Warning in kids_candies(c(1, 103), 51): candies[i] have to be >= 1 and <= 100

[^1]: This problem is originally from Leetdode, you can find it in
    [Leetcode](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to receive your message.

[^3]: This solution is entirely my authorship. I used R version 4.4.1
    (2024-06-14 ucrt).
