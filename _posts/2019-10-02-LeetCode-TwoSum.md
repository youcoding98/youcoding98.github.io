---
layout: post
title: LeetCode 1. 两数之和  
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode] [alg]
---

###  题目  
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。  

####  题解之暴力法：

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int l = nums.length;
        int[] a = new int[2];
        for (int i = 0; i < l; i++) {
            for(int j = i+1;j < l;j++)
            {
                if(nums[i] + nums[j] == target)
                {
                    a[0] = i; a[1] = j;
                    break;
                }
            }
        }
        return a;


    }
}
```
#### 解题思路


