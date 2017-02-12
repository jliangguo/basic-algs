# Basic Sorting - 基础排序

## 算法复习——排序

时间限制为1s时，大O为10,000,000时勉强可行，100,000,000时很悬。

## 算法分析

1. **时间复杂度**-执行时间（比较和交换次数）
2. **空间复杂度**-所消耗的额外内存空间

 1 使用小堆栈或表
 
 2 使用链表或指针、数组索引来代表数据
 
 3 排序数据的副本
 
对具有重键的数据（同一组按不同键多次排序）进行排序时，需要考虑排序方法的稳定性，在非稳定性排序算法中需要稳定性时可考虑加入小索引。

**稳定性**：如果排序后文件中拥有相同键的项的相对位置不变，这种排序方式是稳定的。

常见的排序算法根据是佛需要比较可以分为如下几类：

1. Comparison Sorting
 1. Bubble Sort
 2. Selection Sort
 3. Insertion Sort
 4. Shell Sort
 5. Merge Sort
 6. Quick Sort
 7. Heap Sort
2. Bucket Sort
3. Counting Sort
4. Radix Sort

从稳定性角度考虑可分为如下两类：

1. 稳定
2. 非稳定

## Reference

1. [【面经】硅谷前沿Startup面试经验-排序算法总结及快速排序算法代码-九章算法 ](http://blog.sina.com.cn/s/blog_eb52001d0102v1k8.html) - 总结了一些常用常问的排序算法。

2. [常用排序算法总结（性能+代码）- SegmentFault](http://segmentfault.com/a/1190000002595152#articleHeader15)

