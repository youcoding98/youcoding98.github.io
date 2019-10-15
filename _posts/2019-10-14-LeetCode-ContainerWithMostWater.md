---
layout: post
title: LeetCode 11. 盛最多水的容器
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。  

####  1. 题解之暴力法：

####  1.解题思路


```java
public int maxArea(int[] height) 
    {
        int l = height.length;
        int area = 0;
        for (int i = 0; i < l -1; i++) 
        {
            for (int j = i+1; j < l; j++)
            {
                area = Math.max(area,(j-i)*Math.min(height[i],height[j]));
            }
            
        }
        return  area;
    }

```

####  2. 题解之双指针法：

####  2.解题思路
在由线段长度构成的数组中使用两个指针，一个放在开始，一个置于末尾。 此外，我们会使用变量 maxarea 来持续存储到目前为止所获得的最大面积。 在每一步中，我们会找出指针所指向的两条线段形成的区域，更新 maxarea，并将指向较短线段的指针向较长线段那端移动一步。
   
```java
public int maxArea(int[] height) {
        int maxarea = 0, l = 0, r = height.length - 1;
        while (l < r) {
            maxarea = Math.max(maxarea, Math.min(height[l], height[r]) * (r - l));
            if (height[l] < height[r])
                l++;
            else
                r--;
        }
        return maxarea;
    }
```

#### LeetCode 精选题解


### 补充知识
#### 


```
