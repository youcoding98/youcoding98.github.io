---
layout: post
title: LeetCode 6. Z字形变换
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  

####  1. 题解之暴力法：

####  1.解题思路


```java

public static String convert(String s, int numRows)
    {

        if (numRows == 1) return s;
        char[] a = s.toCharArray();
         int i = 0, j = 0, k = 0;
         int l = s.length();
         char[][] b;
         b = new char[numRows][s.length()];
        for (int m = 0; m < numRows; m++) {
            for (int n = 0; n < s.length(); n++) {
                b[m][n] = '0';
            }
        }
         while(l > 0)
         {
             if(i == 0)
             {
                 for ( i = 0; i < numRows-1 && k < a.length; i++)
                 {

//                     b1[i] = a[k++];
                     b[i][j] = a[k++];//这地方哪里错了
                     l--;
                 }
             }
             if (i == numRows-1)
             {
                 for ( i = numRows-1; i > 0 && k < a.length; i--)
                 {
                     b[i][j] = a[k];
                     j = j + 1;
                     l--;
                     k = k + 1;
                 }
             }
         }
        StringBuilder stringBuilder=new StringBuilder() ;
        for (i = 0; i < numRows; i++)
        {
            for (int m = 0; m <= j; m++) {
                if (b[i][m] != '0')
                    stringBuilder = stringBuilder.append(b[i][m]);
            }
        }
         return stringBuilder.toString();
    }
```

####  2. 

####  2.解题思路

```java
//
//
//
```

#### LeetCode 精选题解


### 补充知识
#### 


```

```
