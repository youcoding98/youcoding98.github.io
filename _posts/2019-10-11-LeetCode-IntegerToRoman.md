---
layout: post
title: LeetCode 12. 整数转罗马数字
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
 
####  1. 题解：

####  1.解题思路


```java
public static String intToRoman(int num) {

        StringBuffer s = new StringBuffer();
        while(num != 0) {
            if (num >= 1000) {
                s.append("M");
                num -= 1000;
            } else if (num >= 900) {
                s.append("CM");
                num -= 900;
            } else if (num >= 500) {
                s.append("D");
                num -= 500;
            } else if (num >= 400) {
                s.append("CD");
                num -= 400;
            } else if (num >= 100) {
                s.append("C");
                num -= 100;
            } else if (num >= 90) {
                s.append("XC");
                num -= 90;
            } else if (num >= 50) {
                s.append("L");
                num -= 50;
            } else if (num >= 40) {
                s.append("XL");
                num -= 40;
            } else if (num >= 10) {
                s.append("X");
                num -= 10;
            } else if (num >= 9) {
                s.append("IX");
                num -= 9;
            } else if (num >= 5) {
                s.append("V");
                num -= 5;
            } else if (num >= 4) {
                s.append("IV");
                num -= 4;
            } else if (num >= 1) {
                s.append("I");
                num -= 1;
            }
        }

        return s.toString();
    }

```

####  2. 题解之人家的暴力法：

####  2.解题思路

   
```java
public class Solution {

    public String intToRoman(int num) {
        // 把阿拉伯数字与罗马数字可能出现的所有情况和对应关系，放在两个数组中
        // 并且按照阿拉伯数字的大小降序排列，这是贪心选择思想
        int[] nums = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        String[] romans = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};

        StringBuilder stringBuilder = new StringBuilder();
        int index = 0;
        while (index < 13) {
            // 特别注意：这里是等号
            while (num >= nums[index]) {
                // 注意：这里是等于号，表示尽量使用大的"面值"
                stringBuilder.append(romans[index] + " ");
                num -= nums[index];
            }
            index++;
        }
        return stringBuilder.toString();
    }
}

```

#### LeetCode 精选题解


### 补充知识
#### String StringBuilder StringBuffer
String：适用于少量的字符串操作的情况  
StringBuilder：适用于单线程下在字符缓冲区进行大量操作的情况(速度比较快)  
StringBuffer：适用多线程下在字符缓冲区进行大量操作的情况  
```java
String str="abc"+"de";
StringBuilder stringBuilder=new StringBuilder().append("abc").append("de");
System.out.println(str);
System.out.println(stringBuilder.toString());

```
