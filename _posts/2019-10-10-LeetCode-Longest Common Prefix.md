---
layout: post
title: LeetCode 14. 最长公共前缀
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。  
####  1. 题解之水平扫描：

####  1.解题思路
依次遍历字符串，当遍历到第i个字符串的时候，找到公共前缀，当公共前缀是个空串时，算法就结束了。否则，在执行n次遍历后，算法就会返回最终答案   

```java
public String longestCommonPrefix(String[] strs)
    {
        if (strs.length == 0)
            return "";
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++) 
        {
            while (strs[i].indexOf(prefix) != 0)
            {
                prefix = prefix.substring(0,prefix.length()-1);
                if (prefix.isEmpty())
                    return "";
            }
        }
        return prefix;
    }

```

####  2. 题解：

####  2.解题思路
从前往后枚举字符串的每一列，先比较每个字符串相同列上的字符，然后再进行对下一列的比较
   
```java
public String longestCommonPrefix(String[] strs)
    {
       if (strs == null || strs.length == 0)
           return "";
        for (int i = 0; i < strs[0].length(); i++) {
            char c = strs[0].charAt(i);
            for (int j = 1;j <strs.length;j++)
            {
                if (i == strs[j].length() || strs[j].charAt(i) != c)
                {
                    return strs[0].substring(0,i);
                }
            }
        }
        return strs[0];
    }
```

#### LeetCode 精选题解


### 补充知识
#### String方法
(1) indexOf()方法    
int indexOf(String str):返回第一次出现指定子字符串在此字符串中的索引   
int indexOf(String str,int startIndex):从指定索引处开始，返回第一次出现的指定子字符串在此字符串中的索引   
(2) substring() 方法
返回一个新的字符串，它是此字符串的一个子字符串。该子字符串始于指定索引处的字符，一直到此字符串末尾   
例："unhappy".substring(2) returns "happy"   


