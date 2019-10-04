---
layout: post
title: LeetCode 13. 罗马数字转整数 
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。
####  题解之暴力法：

```java
public int romanToInt(String s)
    {
        char[] a = s.toCharArray();//取得String字符的每一位
        int sum = 0;
        for (int i = 0; i < s.length()-1; i++)
        {
            if(a[i] == 'I' && a[i+1] == 'V')
            {
                sum = sum + 4;
                a[i] = '0';a[i+1] = '0';
            }
            if(a[i] == 'I' && a[i+1] == 'X')
            {
                sum = sum + 9;
                a[i] = '0';a[i+1] = '0';
            }
            if(a[i] == 'X' && a[i+1] == 'L')
            {
                sum = sum + 40;
                a[i] = '0'; a[i+1] = '0';
            }
            if(a[i] == 'X' && a[i+1] == 'C')
            {
                sum = sum + 90;
                a[i] = '0';a[i+1] = '0';
            }
            if(a[i] == 'C' && a[i+1] == 'D')
            {
                sum = sum + 400;
                a[i] = '0';a[i+1] = '0';
            }
            if(a[i] == 'C' && a[i+1] == 'M')
            {
                sum = sum + 900;
                a[i] = '0';a[i+1] = '0';
            }
        }
        for (int i = 0; i < s.length(); i++)
        {
            if(a[i] == 'I')
                sum = sum + 1;
            if(a[i] == 'V')
                sum = sum + 5;
            if(a[i] == 'X')
                sum = sum + 10;
            if(a[i] == 'L')
                sum = sum + 50;
            if(a[i] == 'C')
                sum = sum + 100;
            if(a[i] == 'D')
                sum = sum + 500;
            if(a[i] == 'M')
                sum = sum + 1000;
        }
        return sum;
    }

```
#### 解题思路


### 补充知识
#### Java中取得String型字符的每一位
char[] a = s.toCharArray();
