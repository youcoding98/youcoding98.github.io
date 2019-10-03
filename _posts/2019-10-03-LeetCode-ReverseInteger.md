---
layout: post
title: LeetCode 7. 整数反转 
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。
####  题解：

```java
public int reverse(int x)
    {
        int sum = 0;
        while(x != 0)
        {
            int pop = x % 10;
            x = x / 10;
            if(sum > Integer.MAX_VALUE/10 || (sum == Integer.MAX_VALUE/10 && pop > 7))
                return 0;
            if(sum < Integer.MIN_VALUE/10 || (sum == Integer.MIN_VALUE/10 && pop < -8))
                return 0;
            sum = sum * 10 + pop;
        }
        return sum;
    }

```
#### 解题思路


### 补充知识
#### 弹出和推入数字
在没有辅助堆栈/数组的帮助下，“弹出”和“推入”数字，可以使用数学方法
```java
// pop operation
pop = x % 10;
x /= 10;

//push operation
temp = rev * 10 + pop;
rev = temp;
```
#### 溢出检查
1.如果temp = rev*10+pop 导致溢出。那么一定有rev >= INTMAX/10   
2.如果rev>INTMAX/10,那么temp = rev*10+pop一定会溢出
3.如果rev==INTMAX/10，那么只要pop>7,temp = rev*10+pop就会溢出
