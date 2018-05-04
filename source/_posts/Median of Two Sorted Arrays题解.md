---
title: Median of Two Sorted Arrays题解
date: 2018-02-01 20:24:16
tags: problems
categories: Python
---

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0

```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

问题：已知两个有序数列，求他们之间的中位数

思考：把两个数组merge成一个数组，求中位数

Python3解法如下：

```Python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        res = []
        while len(nums1) !=0 and len(nums2) != 0:
            if nums1[0]<nums2[0]:
                res.append(nums1[0])
                del nums1[0]
            else:
                res.append(nums2[0])
                del nums2[0]
        newnums = res+nums1+nums2
        if len(newnums)%2==0:
            return (newnums[len(newnums)//2]+newnums[len(newnums)//2-1])/2
        else:
            return newnums[len(newnums)//2]
```
