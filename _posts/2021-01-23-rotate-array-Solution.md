---
layout: post
title: 【经典算法问题】旋转数组
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [Algorithm]
---

## 一、题目：[旋转数组](https://leetcode-cn.com/problems/rotate-array/) 

**要求：**  
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。  

## 二、思路

### 思路一：使用额外的数组
使用额外的数组来将每个元素放至正确的位置。用`len`表示数组的长度，我们遍历原数组，将原数组下标为`i`的元素放至新数组下标为`(i+k) mod len`的位置，
最后将新数组拷贝至原数组即可。  
时间复杂度`O(N)`,空间复杂度`O(N)`  

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

### 思路二：环形替换
可以将被替换的元素保存在变量`temp`中，从而避免了额外数组的开销。  
我们从位置 `0` 开始，最初令 `temp=nums[0]` 根据规则，位置 `0`的元素会放至 `(0+k)mod n` 的位置，令 `x=(0+k)mod n`，此时交换 `temp` 和 `nums[x]`，完成位置 `x` 的更新。
然后，我们考察位置 `x`，并交换 `temp` 和 `nums[(x+k)mod n]`，从而完成下一个位置的更新。不断进行上述过程，直至回到初始位置 `0`。  
从 `0` 开始不断遍历，最终回到起点 `0` 的过程中，我们遍历了多少个元素？ 为了访问到所有的元素，我们需要进行遍历的次数为`gcd(n,k)` 过程为数学推导  
时间复杂度`O(N)`,空间复杂度`O(1)`  

**参考代码：**   
```java
class Solution {
    public void rotate(int[] nums,int k){
        int n = nums.length;
        k = k % n;
        //需要遍历的次数
        int count = gcd(k,n);
        for (int start = 0; start < count; start++) {
            int current = start;
            int prev = nums[start];
            do {
               int next = (current + k) % n;
                int temp = nums[next];
                nums[next] = prev;
                prev = temp;
                current = next;
            }while (start != current);
        }
    }

    private int gcd(int x,int y){
        return y > 0 ? gcd(y, x % y) : x;
    }
}
```



### 思路三：三次翻转 
先反转全部数组，然后反转前k个，最后反转剩余的，如下所示  
[![yFUWxP.png](https://s3.ax1x.com/2021/01/30/yFUWxP.png)](https://imgchr.com/i/yFUWxP)
时间复杂度`O(N)`,空间复杂度`O(1)`  
**参考代码：**    
```java
class Solution {
    public void rotate(int[] nums, int k) {
        int len = nums.length;
        k = k % len;
        reverse(nums,0,len - 1);
        reverse(nums,0,k - 1);
        reverse(nums,k,len - 1);
    }
    
    private void reverse(int[] nums,int left,int right){
        while(left < right){
            swap(nums,left,right);
            left++;
            right--;
        }
    }
    
    private void swap(int[] nums,int i,int j){
        nums[i] ^= nums[j];
        nums[j] ^= nums[i];
        nums[i] ^= nums[j];
    }
}
```





