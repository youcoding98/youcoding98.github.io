---
layout: post
title: LeetCode 9. 回文数 
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  

####  题解之暴力法：

```java
public boolean isPalindrome(int x)
    {
        boolean  tag = true;
        if(x < 0)
            tag = false;
        if(x > 0)
        {
            String s=Integer.toString(x);
            char[] a = s.toCharArray();
            int i = 0,j = s.length()-1;
            while(i < s.length()/2)
            {
                if (a[i] != a[j])
                {
                    tag = false;
                    break;
                }
                i++;j--;
            }
        }

        return tag;
    }
```
#### 解题思路


#### LeetCode 精选题解


### 补充知识
#### Java中取得String型字符的每一位
char[] a = s.toCharArray();
#### 整数转换成字符串
String s = Integer.toString(x);
