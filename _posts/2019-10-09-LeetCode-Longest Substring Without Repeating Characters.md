---
layout: post
title: LeetCode 3. 无重复字符的最长子串
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。  
####  1. 题解之暴力法：

####  1.解题思路
逐个检查所有的子字符串，看是否含有重复的字符   
（1） 枚举给定的所有字符串，枚举他们开始和结束的索引，使用 i从 0 到 n - 1 以及 j 从 i+1 到 n 这两个嵌套的循环   
（2） 使用集合来检查一个字符串是否有重复字符，在放置一个字符之前，检查该集合是否已经包含它。  
```java

public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int ans = 0;
        for (int i = 0; i < n; i++)
            for (int j = i + 1; j <= n; j++)
                if (allUnique(s, i, j)) ans = Math.max(ans, j - i);
        return ans;
    }

    public boolean allUnique(String s, int start, int end) {
        Set<Character> set = new HashSet<>();
        for (int i = start; i < end; i++) {
            Character ch = s.charAt(i);
            if (set.contains(ch)) return false;
            set.add(ch);
        }
        return true;
    }
}

```

####  2. 题解之滑动窗口：

####  2.解题思路
如果从索引 i 到 j - 1之间的子字符串 s{ij} 已经被检查为没有重复字符。我们只需要检查 s[j] 对应的字符是否已经存在于子字符串 s_{ij}中。   
使用HashSet作为滑动窗口，可以用O(1)时间完成对字符是否在当前子字符串中的检查。   
```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        Set<Character> set = new HashSet<>();
        int ans = 0, i = 0, j = 0;
        while (i < n && j < n) {
            // try to extend the range [i, j]
            if (!set.contains(s.charAt(j))){
                set.add(s.charAt(j++));
                ans = Math.max(ans, j - i);
            }
            else {
                set.remove(s.charAt(i++));
            }
        }
        return ans;
    }
}
```

#### LeetCode 精选题解


### 补充知识
#### Set 和 HashSet
Set  如果是实现了Set接口的集合类，具备的特点： 无序，不可重复   
HashSet  底层是使用了哈希表来支持的，特点： 存取速度快.    


