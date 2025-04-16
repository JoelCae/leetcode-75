
# 605 Can Place Flowers [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

You have a long flowerbed in which some of the plots are planted, and
some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array **flowerbed** containing **0**’s and **1**’s,
where **0** means empty and **1** means not empty, and an integer **n**,
return **true** if **n** new flowers can be planted in the **flowerbed**
without violating the no-adjacent-flowers rule and **false** otherwise.

**Examples**

- Example 1:
  - Input: flowerbed = \[1,0,0,0,1\], n = 1
  - Output: true
- Example 2:
  - Input: flowerbed = \[1,0,0,0,1\], n = 2
  - Output: false

**Constraints:**

- 1 \<= **flowerbed.length** \<= 2 x $10^4$
- **flowerbed\[i\]** is 0 or 1
- There are no two adjacent flowers in flowerbed
- 0 \<= **n** \<= flowerbed.length

## SOLUTION [^3]

``` r
flowers <- function(flowerbed,n){
 
   #conditions
  l_fb <- length(flowerbed)
  if(sum(0 == flowerbed | flowerbed == 1) != l_fb  | l_fb == 0  | n  < 0  | n > l_fb |
     grepl(paste(flowerbed, collapse = ""), pattern = "11" ) ) {
    if(sum(0 == flowerbed | flowerbed == 1) != l_fb){
     warning("Elements in flowerded are not 1 or 0")}
    if(l_fb == 0) {warning("Length of flowerbed have to be => 1")}
    if(n  < 0  | n > l_fb ) {warning("n have to be >= 0 and <=  lowerbed.length")}
    if(grepl(paste(flowerbed, collapse = ""), pattern = "11")) {
      warning("There are two adjacent flowers in flowerbed")}
  } else {
    
    # solution
      # 1st case: Only 0, the maximum possible is floor((length(flowerbed) + 1)/2)
  
      # 2nd case: at least a 1 in the vector (sum of 2.1 and 2.2 cases)
        ## 2.1 case: count in extremes 
        ## 2.2 case: count in the middle 
        # it is possible to think the 2nd case in terms of the  1st case
          ## just dividing the vector in sub vectors of 0's
      
      # 1st case:
    if(sum(flowerbed) == 0) {
      n_pos <- floor((length(flowerbed) + 1)/2)
      return(n <= n_pos) }
    else {
      # 2nd case: 
      #create vector where i-element is 1 
      vector_1 <- c(0)  
      for (i in 1:length(flowerbed)) {
        if (flowerbed[i] == 1) {
          vector_1 <- c(vector_1, i) }
      }
      vector_1 <- c(vector_1, length(flowerbed) + 1)
      # create vector: how many 0 (between two "1", 1...1)?
      vector_dif <- c()  
      for (i in 2:length(vector_1)) {
        vector_dif[i - 1] <- vector_1[i] - vector_1[i - 1] - 1 }
      # adjust per each case
      vector_dif_aj <- c()
      for (i in 1:length(vector_dif)) {
        ## 2.1 case: in the extremes of the vector: (0 0 1 ... ) or (...1 0 0 0)
        if (i == 1 | i == length(vector_dif)) {
          ## we can't use the element next to the first/last 1 (due to adjacent)
          vector_dif_aj[i] <-  vector_dif[i] - 1 }
          ## 2.2 case: in the middle of the vector: (...1 0 0 1 ... ) or (...1 0 0 0 1...)
        else {
          # we can't use two elements (due to adjacent), one per each 1
          vector_dif_aj[i] <-  vector_dif[i] - 2 }
      }
      # count the possibles 1's in each sub vector
      vector_n_pos <- c()
      for (i in 1:length(vector_dif_aj)) {
        vector_n_pos[i] <- floor((vector_dif_aj[i] + 1) / 2) }
      
      # total of 1's for the 2nd case
      n_pos <- sum(vector_n_pos)
      return(n <= n_pos)
    }
  }
}
```

**Examples using the function**

``` r
flowers(c(1,0,0,0,1), 1)
```

    ## [1] TRUE

``` r
flowers(flowerbed = c(1,0,0,0,1), n = 2)
```

    ## [1] FALSE

In addition, we can also check the restrictions.

``` r
flowers(c(), -1)
```

    ## Warning in flowers(c(), -1): Length of flowerbed have to be => 1

    ## Warning in flowers(c(), -1): n have to be >= 0 and <= lowerbed.length

``` r
flowers(c(1,1,0,0,2), 6)
```

    ## Warning in flowers(c(1, 1, 0, 0, 2), 6): Elements in flowerded are not 1 or 0

    ## Warning in flowers(c(1, 1, 0, 0, 2), 6): n have to be >= 0 and <= lowerbed.length

    ## Warning in flowers(c(1, 1, 0, 0, 2), 6): There are two adjacent flowers in flowerbed

[^1]: This problem is originally from Leetdode, you can find it in
    [Leetcode](https://leetcode.com/problems/can-place-flowers/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to receive your message.

[^3]: This solution is entirely my authorship. I used R version 4.4.1
    (2024-06-14 ucrt).
