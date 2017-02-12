# Selection Sort - 选择排序

**核心思想**：不断地选择剩余元素中的最小者。

1. 找到数组中最小元素并将其和数组第一个元素交换位置。
2. 在剩下的元素中找到最小元素并将其与数组第二个元素交换，直至整个数组有序。

性质：

- 比较次数=$$(N-1)+(N-2)+(N-3)+...+2+1 \sim N^2/2$$
- 交换次数=N
- 运行时间与输入无关
- 数据移动最少

下图来源为[File:Selection-Sort-Animation.gif - IB Computer Science](http://wiki.ibcsstudent.org/index.php?title=File:Selection-Sort-Animation.gif)

![Selection-Sort-Animation.gif](/assets/selection_sort.gif)

## 编程实现

### Java

```java
public static void sort(int[] array) {
    int N = array.length;
    for (int i = 0; i < N; i++) {
        int min = i;
        for (int j = i + 1; j < N; j++) {
            if (array[min] > array[j]) {
                min = j;
            }
        }
        int tmp = array[min];
        array[min] = array[i];
        array[i] = tmp;
    }
}
```

### Scala

```scala
def sort(array: Array[Int]): Unit = {
    val N = array.length
    var i = 0
    while (i < N) {
      // search minimal
      var min = i
      var j = i + 1
      while (j < N) {
        if (array(min) > array(j))
          min = j
        j += 1
      }
      // swap
      val tmp = array(min)
      array(min) = array(i)
      array(i) = tmp

      i += 1
    }
  }
```

### Go

```go
func selectionSort(array []int) {
	N := len(array)
	for i := 0; i < N; i++ {
		min := i
		for j := i + 1; j < N; j++ {
			if array[min] > array[j] {
				min = j
			}
		}

		tmp := array[min]
		array[min] = array[i]
		array[i] = tmp
	}
}
```

## Reference

1. [选择排序 - 维基百科，自由的百科全书](http://zh.wikipedia.org/wiki/%E9%80%89%E6%8B%A9%E6%8E%92%E5%BA%8F)

2. [The Selection Sort — Problem Solving with Algorithms and Data Structures](http://interactivepython.org/runestone/static/pythonds/SortSearch/TheSelectionSort.html)