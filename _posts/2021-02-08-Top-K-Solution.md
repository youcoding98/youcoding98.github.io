---
layout: post
title: 【经典算法问题】Top K 问题
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [Algorithm]
---

## 一、题目：[最小的k个数](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/) 


**要求：**  
输入整数数组 arr ，找出其中最小的`k`个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

## 二、实现 
这里我们给出四种解题思路，分别为：   
1. 用快排最最最高效解决 TopK 问题
2. 大根堆(前 K 小) / 小根堆（前 K 大)
3. 二叉搜索树解决TopK 问题
4. 数据范围有限时直接计数排序
具体实现见下：

### 1.用快排最最最高效解决 TopK 问题
利用快排思想：找前 K 大/前 K 小问题不需要对整个数组进行`O(NlogN)`的排序，直接通过快排切分排好第 K 小的数（下标为 K-1），那么它左边的数就是比它小的另外 K-1 个数   
**参考代码：**    
```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if(arr == null || arr.length == 0 || k == 0){
            return new int[]{};
        }
        if(arr.length == k){
            return arr;
        }
        int[] result = new int[k];
        quickFind(arr,0,arr.length - 1,k);
        for(int i = 0; i < k;i++){
            result[i] = arr[i];
        }
        return result;
    }
    
    public void quickFind(int[] arr,int left,int right,int k){
        // 每快排切分1次，找到排序后下标为j的元素，如果index恰好等于k就返回
        int index = partition(arr,left,right);
        if(index == k){
            return;
        }
        //// 否则根据下标index与k的大小关系来决定继续切分左段还是右段。
        if(index > k){
            quickFind(arr,left,index-1,k);
        }
        if(index < k){
            quickFind(arr,index+1,right,k);
        }
    }
    
    public int partition(int[] arr,int left,int right){
        int mid = arr[left];
        while(left < right){
            while(left < right && arr[right] > mid){
                right--;
            }
            arr[left] = arr[right];
            while(left < right && arr[left] <= mid){
                left++;
            }
            arr[right] = arr[left];
        }
        arr[left] = mid;
        return left;
    }
}
```
快排切分时间复杂度分析： 因为我们是要找下标为k的元素，第一次切分的时候需要遍历整个数组 `(0 ~ n)` 找到了下标是 `j`的元素，
假如 `k` 比 `j` 小的话，那么我们下次切分只要遍历数组 `(0~k-1)`的元素就行啦，反之如果 `k` 比 `j` 大的话，那下次切分只要遍历数组 `(k+1～n)` 的元素就行，
总之可以看作每次调用 `partition` 遍历的元素数目都是上一次遍历的 `1/2`，因此时间复杂度是 `N + N/2 + N/4 + ... + N/N = 2N`, 因此时间复杂度是 `O(N)`。

### 2.大根堆(前 K 小) / 小根堆（前 K 大)
本题是求前 `K` 小，因此用一个容量为 `K` 的大根堆，每次 `poll` 出最大的数，那堆中保留的就是前 `K`小   
保持堆的大小为`K`，然后遍历数组中的数字，遍历的时候做如下判断：
1. 若目前堆的大小小于`K`，将当前数字放入堆中。
2. 否则判断当前数字与大根堆堆顶元素的大小关系，如果当前数字比大根堆堆顶还大，这个数就直接跳过；反之如果当前数字比大根堆堆顶小，先`poll`掉堆顶，再将该数字放入堆中。
```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if (k == 0 || arr.length == 0) {
            return new int[0];
        }
        // 默认是小根堆，实现大根堆需要重写一下比较器。
        Queue<Integer> pq = new PriorityQueue<>((v1, v2) -> v2 - v1);
        for (int num: arr) {
            if (pq.size() < k) {
                pq.offer(num);
            } else if (num < pq.peek()) {
                pq.poll();
                pq.offer(num);
            }
        }
        
        // 返回堆中的元素
        int[] res = new int[pq.size()];
        int idx = 0;
        for(int num: pq) {
            res[idx++] = num;
        }
        return res;
    }
}
```
大根堆时间复杂度为`O(NlogK)`  

### 4.二叉搜索树解决TopK 问题
BST求解思路与最大堆基本一致，与前两种方法相比，BST 有一个好处是求得的前K大的数字是有序的  
我们遍历数组中的数字，维护一个数字总个数为 K 的 `TreeMap`(`TreeMap`的`key` 是数字，`value` 是该数字的个数)：
1. 若目前 map 中数字个数小于 `K`，则将 `map` 中当前数字对应的个数 +1；
2. 否则，判断当前数字与 `map` 中最大的数字的大小关系：若当前数字大于等于 `map` 中的最大数字，就直接跳过该数字；若当前数字小于 `map` 中的最大数字，则将 `map` 中当前数字对应的个数 +1，并将 `map` 中最大数字对应的个数减 1。
```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if (k == 0 || arr.length == 0) {
            return new int[0];
        }
        // TreeMap的key是数字, value是该数字的个数。
        // cnt表示当前map总共存了多少个数字。
        TreeMap<Integer, Integer> map = new TreeMap<>();
        int cnt = 0;
        for (int num: arr) {
            // 1. 遍历数组，若当前map中的数字个数小于k，则map中当前数字对应个数+1
            if (cnt < k) {
                map.put(num, map.getOrDefault(num, 0) + 1);
                cnt++;
                continue;
            } 
            // 2. 否则，取出map中最大的Key（即最大的数字), 判断当前数字与map中最大数字的大小关系：
            //    若当前数字比map中最大的数字还大，就直接忽略；
            //    若当前数字比map中最大的数字小，则将当前数字加入map中，并将map中的最大数字的个数-1。
            Map.Entry<Integer, Integer> entry = map.lastEntry();
            if (entry.getKey() > num) {
                map.put(num, map.getOrDefault(num, 0) + 1);
                if (entry.getValue() == 1) {
                    map.pollLastEntry();
                } else {
                    map.put(entry.getKey(), entry.getValue() - 1);
                }
            }
            
        }

        // 最后返回map中的元素
        int[] res = new int[k];
        int idx = 0;
        for (Map.Entry<Integer, Integer> entry: map.entrySet()) {
            int freq = entry.getValue();
            while (freq-- > 0) {
                res[idx++] = entry.getKey();
            }
        }
        return res;
    }
}
```
二叉搜索树解决`TopK`问题时间复杂度为`O(NlogK)`  

### 3.数据范围有限时直接计数排序
```java
class Solution {
    public static int[] getLeastNumbers(int[] arr, int k) {
        if(arr == null || arr.length == 0 || k == 0){
            return new int[]{};
        }
        int[] counter = new int[10001];
        for (int num:arr) {
            counter[num]++;
        }
        int[] result = new int[k];
        int index = 0;
        for (int i = 0; i < counter.length; i++) {
            while (counter[i] > 0 && index < k){
                result[index++] = i;
                counter[i]--;
            }
            if (index == k){
                break;
            }
        }
        return result;
    }
}
```
直接计数排序时间复杂度`O(N)`  