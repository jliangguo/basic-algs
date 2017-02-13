# Insertion Sort - 选择排序

**核心实现**：通过构建有序序列，对于未排序序列，在已排序序列中从后面向前扫描（对于单向链表则只能从前往后遍历），找到相应位置并插入。实现上通常使用in-place排序（需用到$$O(1)$$的额外空间）。

1. 从第一个元素开始，该元素可认为已排序
2. 取下一个元素，对已排序数组从后往前扫描
3. 若从排序数组中取出的元素大于新元素，则移至下一个位置
4. 重复步骤3，直至找到已排序元素小于或等于新元素的位置
5. 插入新元素至该位置
6. 重复2~5

性质：

- 交换操作和数组中倒置的数量相同
- 比较次数>=倒置数量，<=倒置的数量加上数组的大小减一
- 每次交换都改变了两个顺序颠倒的元素的位置，即减少了一对倒置，倒置数据量为0时即完成排序。
- 每次交换对应着一次比较，且1到N-1之间的每个i都可能需要一次额外的记录（a[i]未到达数组左端时）
- 最坏情况下需要~N^2/2次比较和~N^2/2次交换，最好情况下需要N-1次比较和0次交换。
- 平均情况下需要~N^2/4次比较和~N^2/4次交换

![Insertion-sort](/assets/Insertion-sort-300px.gif)

## 编程实现

### Java

```java
public static void insertionSort(int[] array) {
    int N = array.length;
    for (int i = 0; i < N; i++) {
        int index = i, array_i = array[i];
        while (index > 0 && array[index - 1] > array_i) {
            array[index] = array[index - 1];
            index -= 1;
        }
        array[index] = array_i;
    }
}
```

### Go

```go
func insertionSort(array []int) {
	N := len(array)
	for i := 0; i < N; i++ {
		index, array_i := i, array[i]
		for index > 0 && array[index - 1] > array_i {
			array[index] = array[index - 1]
			index -= 1
		}
		array[index] = array_i
	}
}
```

# 希尔排序

**核心思想**：基于插入排序，使数组中任意间隔为h的元素都是有序的，即将全部元素分为h个区域使用插入排序。其实现可类似于插入排序但使用不同增量。更高效的原因是它权衡了子数组的规模和有序性。

## 编程实现

### Java

```java
public static void shellSort(int[] array) {
    int N = array.length;

    // 3x+1 increment sequence:  1, 4, 13, 40, 121, 364, 1093, ...
    int h = 1;
    while (h < N / 3) h = 3 * h + 1;

    while (h >= 1) {
        // h-sort the array
        for (int i = h; i < N; i++) {
            for (int j = i; j >= h && array[j - h] > array[j]; j -= h) {
                int tmp = array[j - h];
                array[j - h] = array[j];
                array[j] = tmp;
            }
        }
        h /= 3;
    }
}
```

## Reference

1. [插入排序 - 维基百科，自由的百科全书](http://zh.wikipedia.org/wiki/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F)
2. [希尔排序 - 维基百科，自由的百科全书](http://zh.wikipedia.org/wiki/%E5%B8%8C%E5%B0%94%E6%8E%92%E5%BA%8F)
3. [The Insertion Sort — Problem Solving with Algorithms and Data Structures](http://interactivepython.org/runestone/static/pythonds/SortSearch/TheInsertionSort.html)