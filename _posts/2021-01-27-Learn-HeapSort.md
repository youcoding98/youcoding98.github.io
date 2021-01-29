---
layout: post
title: 【经典算法问题】堆排序总结与实现
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [Java,Algorithm]
---
本文总结学习堆排序算法，以一个数组为例，采用大根堆进行升序排序，附有代码实现。堆排序是一种选择排序，它的最坏，最好，平均时间复杂度均为O(nlogn)，它也是不稳定排序。  



## 一、堆 
堆是具有以下性质的完全二叉树：每个结点的值都大于或等于其左右孩子结点的值，称为大顶堆；或者每个结点的值都小于或等于其左右孩子结点的值，称为小顶堆。
[![svFGm6.png](https://s3.ax1x.com/2021/01/26/svFGm6.png)](https://imgchr.com/i/svFGm6){: .center-block :}
同时，我们对堆中的结点按层进行编号，将大根堆映射到数组中就是下面这个样子
[![svFh1s.png](https://s3.ax1x.com/2021/01/26/svFh1s.png)](https://imgchr.com/i/svFh1s){: .center-block :}

## 二、 堆排序基本思想
*堆排序的基本思想是：将待排序序列构造成一个大顶堆，此时，整个序列的最大值就是堆顶的根节点。将其与末尾元素进行交换，此时末尾就为最大值。然后将剩余n-1个元素重新构造成一个堆，这样会得到n个元素的次小值。如此反复执行，便能得到一个有序序列了*

1. 构造初始堆。将给定无序序列构造成一个大顶堆
   + 我们从最后一个非叶子结点`i = arr.length / 2 - 1`开始，从左到右，从上到下进行调整
   [![svF5Xq.png](https://s3.ax1x.com/2021/01/26/svF5Xq.png)](https://imgchr.com/i/svF5Xq){: .center-block :}
   [![svFbAU.png](https://s3.ax1x.com/2021/01/26/svFbAU.png)](https://imgchr.com/i/svFbAU){: .center-block :}
   [![svFvcR.png](https://s3.ax1x.com/2021/01/26/svFvcR.png)](https://imgchr.com/i/svFvcR){: .center-block :}

2. 将堆顶元素与末尾元素进行交换，使末尾元素最大。然后继续利用堆调整算法，对前 n-1 个数进行堆调整，再将堆顶元素与末尾元素交换，得到第二大元素。如此反复进行交换、重建、交换。
   + 将堆顶元素9和末尾元素4进行交换
   [![svkiND.png](https://s3.ax1x.com/2021/01/26/svkiND.png)](https://imgchr.com/i/svkiND){: .center-block :}
   + 重新调整堆结构，使其继续满足堆定义
   [![svkVgA.png](https://s3.ax1x.com/2021/01/26/svkVgA.png)](https://imgchr.com/i/svkVgA){: .center-block :}

## 三、参考代码：
     
```
        public static void heapSort(int [] arr){
            //1.构建大顶堆
            for(int i = arr.length / 2 - 1;i >= 0;i--){
                //从第一个非叶子结点从下至上，从右至左调整结构
                adjustHeap(arr,i,arr.length);
            }
            //2.调整堆结构+交换堆顶元素与末尾元素
            for(int j = arr.length - 1;j > 0;j--){
                //将堆顶元素与末尾元素进行交换
                swap(arr,0,j);
                //重新对堆进行调整
                adjustHeap(arr,0,j);
            }
        }
        /**
         * 交换数组中两个数，使用位运算
         */
        private static void swap(int[] arr, int i, int j) {
            arr[i] ^= arr[j];
            arr[j] ^= arr[i];
            arr[i] ^= arr[j];
        }
        /**
         * 堆调整
         */
        private static void heapAdjustOld(int[] arr, int s, int length) {
            for (int i = 2 * s + 1; i < length; i = 2 * i + 1) {
                if (i + 1 < length && arr[i + 1] > arr[i]) {
                    ++i;
                }
                if (arr[s] > arr[i]) {
                    break;
                }
                swap(arr, s, i);
                s = i;
            }
    
        }
        /**
         * 堆调整优化方法
         */
        public static void adjustHeap(int []arr,int i,int length){
            //先取出当前元素i
            int temp = arr[i];
            //从i结点的左子结点开始，也就是2i+1处开始
            for(int k = i * 2 + 1;k < length;k = k * 2 + 1){
                //如果左子结点小于右子结点，k指向右子结点
                if(k+1 < length && arr[k] < arr[k+1]){
                    k++;
                }
                //如果子节点大于父节点，将子节点值赋给父节点（不用进行交换）
                if(arr[k] > temp){
                    arr[i] = arr[k];
                    i = k;
                }else{
                    break;
                }
            }
            //将temp值放到最终的位置
            arr[i] = temp;
        }
```




