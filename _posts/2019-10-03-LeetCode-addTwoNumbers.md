---
layout: post
title: LeetCode 2. 两数相加  
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储一位数字。如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
####  题解之暴力法：

```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode l3 = new ListNode(0);//声明链表
        ListNode p = l1,q = l2,curr = l3;
        int carry = 0,x = 0,y = 0;
        while(p!= null || q!= null)
        {
            if(p != null)
                x = p.val;
            else
                x = 0;
            if(q != null)
                y = q.val;
            else
                y = 0;
            int sum = x + y + carry;
            carry = sum / 10;
            curr.next = new ListNode(sum%10);
            curr = curr.next;
            if(p != null)
                p = p.next;
            if(q != null)
                q = q.next;

        }
        if(carry > 0)
            curr.next = new ListNode(carry);

        return l3.next;

    }

```
#### 解题思路


### 补充知识
三元运算符  
C=A>B ? 100 :200; 这条语句的意思是，如果A>B的话，就将100赋给C，否则就将200赋给C；  
![Crepe](https://github.com/youcoding98/youcoding98.github.io/blob/master/img/dummy%20head.png){: .center-block :}
