---
layout: post
title: 【编程必备知识】Java输入输出
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [Java]
---

## [OJ在线编程常见输入输出](https://www.nowcoder.com/test/27976983/summary#question) 
 

### 1：多行同类数据(int),不知长度
**举例：**   


**参考代码：**
```java
class Solution {
    public void rotate(int[] nums, int k) {
        int len = nums.length;
        int[] temp = new int[len];
        for(int i = 0; i < len; i++){
            int index = (i + k) % len;
            temp[index] = nums[i];
        }
        for(int i = 0; i < len; i++){
            nums[i] = temp[i];
        }
    }
}
```







