---
title: "Start My Coding Record from Binary Search and Array!"
date: 2023-06-07T15:34:30-04:00
categories:
  - Leetcode
tags:
  - Binary Search
  - Array
  

---

Find kth smallest element of two sorted arrays: 
Given two arrays a and b, find the Kth smallest element of the two arrays. k is smaller than a.length + b.length
 
```ruby
public int kthSmallest(int[] a, int[] b, int k) {
  if(a == null || b == null){
    return -1;
  }
  int aLeft = 0;
  int bLeft = 0;
  int aVal = 0;
  int bVal = 0;
  while(k > 1){
    aVal = aLeft + k / 2 - 1 >= a.length? Integer.MAX_VALUE: a[aLeft + k/2 - 1];
    bVal = bLeft + k / 2 - 1 >= b.length? Integer.MAX_VALUE: b[bLeft + k/2 - 1];
    if(aVal <= bVal){
      aLeft = aLeft + k / 2;
    }else{
      bLeft = bLeft + k / 2;
    }
    k = k - k / 2; // k = 1
    }
  aVal = aLeft >= a.length ? Integer.MAX_VALUE: a[aLeft + k - 1];
  bVal = bLeft >= b.length ? Integer.MAX_VALUE: b[bLeft + k - 1];
  return Math.min(aVal, bVal);
}
  Time complexity: O(logn) Space complexity: O(1)
```

Solution: 
  
  For sure that the Kth smallest element of the two arrays is in the two arrays' first k elements. Every time the middle element among two arrays are taken and compared, and then the search domain can be reduced to half.
  
  There are two cases to think about:
  
  1. array.length > k(the search range)
  2. array.length < k, where out of boundary error can happen and it needs attention
