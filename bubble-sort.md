# Bubble Sort - 冒泡排序

核心思想：持续比较相邻元素，大的挪到后面，因此大的会逐步往后挪，故称之为**冒泡**。

原理示意图：

![](/assets/bubble_sort.gif)

## 编程实现


### Java

```java
public static void bubbleSort(int[] array) {
    int len = array.length;
    for (int i = 0; i < len; i++) {
        for (int j = 1; j < len - i; j++) {
            if (array[j - 1] > array[j]) {
                int temp = array[j - 1];
                array[j - 1] = array[j];
                array[j] = temp;
            }
        }
    }
}
```

### Scala

### Go

```go
func bubbleSort(array []int)  {
	for i:= 0; i < len(array); i++ {
		for j := 1; j < len(array) - i; j++ {
			if array[j-1] > array[j] {
				tmp := array[j-1]
				array[j-1] = array[j]
				array[j] = tmp
			}
		}
	}
}
```
## 复杂度分析

平均情况与最坏情况均为$$ O(n^2)$$, 使用了` tmp `作为临时交换变量，空间复杂度为 $$O(1)$$。

## Reference

1. [冒泡排序 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E5%86%92%E6%B3%A1%E6%8E%92%E5%BA%8F)

