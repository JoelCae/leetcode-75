
# 2215 Find the Difference of Two Arrays [^1]

Joel Castillo Espinosa [^2]

## DESCRIPTION

Given two 0-indexed integer arrays **nums1** and **nums2**, return a
list **answer** of size **2** where:

- **answer\[0\]** is a list of all distinct integers in **nums1** which
  are not present in **nums2**.
- **answer\[1\]** is a list of all distinct integers in **nums2** which
  are not present in **nums1**.

Note that the integers in the lists may be returned in any order.

**Examples**

- Example 1:
  - Input: nums1 = \[1,2,3\], nums2 = \[2,4,6\]
  - Output: \[\[1,3\],\[4,6\]\]
  - Explanation: For nums1, nums1\[1\] = 2 is present at index 0 of
    nums2, whereas nums1\[0\] = 1 and nums1\[2\] = 3 are not present in
    nums2. Therefore, answer\[0\] = \[1,3\]. For nums2, nums2\[0\] = 2
    is present at index 1 of nums1, whereas nums2\[1\] = 4 and
    nums2\[2\] = 6 are not present in nums1. Therefore, answer\[1\] =
    \[4,6\].
- Example 2:
  - Input: nums1 = \[1,2,3,3\], nums2 = \[1,1,2,2\]
  - Output: \[\[3\],\[\]\]
  - Explanation: For nums1, nums1\[2\] and nums1\[3\] are not present in
    nums2. Since nums1\[2\] == nums1\[3\], their value is only included
    once and answer\[0\] = \[3\].Every integer in nums2 is present in
    nums1. Therefore, answer\[1\] = \[\].

**Constraints:**

- 1 ≤ **nums1.length**,**nums2.length** ≤ 1000
- -1000 ≤ **nums1\[i\]**,**nums2\[i\]** ≤ 1000

## SOLUTION [^3]

``` r
dif_array <- function(nums1, nums2){
  nums1r <- nums1
  nums2r <- nums2
  
  # in each iteration, check if nums1[i] matches in nums2
    # then drop the matches or keep in both arrays 
  for (i  in nums1) {
    match <- sum(nums2r == i)
    if(match > 0){
    nums2r <- nums2r[nums2r != i] # drop matches in nums2
    nums1r <- nums1r[nums1r != i] # drop matches in nums1
    }
  }
  
  # for empty arrays (if it is necessary)
  if(length(nums1r) == 0 ) {
    nums1r <- " "  } 
  if(length(nums2r) == 0 ) {
    nums2r <- " "  }
  
  return(list(unique(nums1r), unique(nums2r)))
}
```

**Examples using the function**

We can use the examples presented before.

``` r
dif_array(c(1,2,3), c(2,4,6))
```

    ## [[1]]
    ## [1] 1 3
    ## 
    ## [[2]]
    ## [1] 4 6

``` r
dif_array(c(1,2,3,3), c(1,1,2,2))
```

    ## [[1]]
    ## [1] 3
    ## 
    ## [[2]]
    ## [1] " "

[^1]: This problem is originally from LeetCode, you can find it in
    [Leetcode](https://leetcode.com/problems/find-the-difference-of-two-arrays/?envType=study-plan-v2&envId=leetcode-75).

[^2]: Email: <jocastillo@colmex.mx>. For more content visit my website:
    <https://joelcastillo.netlify.app> <br> If you have any questions or
    suggestions, I’d be grateful to hear from you.

[^3]: This solution is entirely my own work. It was developed using R
    version 4.4.1 (2024-06-14 ucrt).
