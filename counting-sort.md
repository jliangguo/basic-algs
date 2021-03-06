# Counting Sort - 计数排序

计数排序，顾名思义，就是对待排序数组按元素进行计数。使用前提是需要先知道待排序数组的元素范围，将这些一定范围的元素置于新数组中，新数组的大小为待排序数组中最大元素与最小元素的差值。

维基上总结的四个步骤如下：

1. 定新数组大小——找出待排序的数组中最大和最小的元素
2. 统计次数——统计数组中每个值为i的元素出现的次数，存入新数组C的第i项
3. 对统计次数逐个累加——对所有的计数累加（从C中的第一个元素开始，每一项和前一项相加）
4. 反向填充目标数组——将每个元素i放在新数组的第C(i)项，每放一个元素就将C(i)减去1

其中反向填充主要是为了避免重复元素落入新数组的同一索引处。

以下例子为Java代码：

```java
public static void sort(int[] a, int maxValue) {
    int[] bucket = new int[maxValue + 1];

    for (int i = 0; i < bucket.length; i++) {
        bucket[i] = 0;
    }

    for (int i = 0; i < a.length; i++) {
        bucket[a[i]]++;
    }

    int outPos = 0;
    for (int i = 0; i < bucket.length; i++) {
        for (int j = 0; j < bucket[i]; j++) {
            a[outPos++] = i;
        }
    }
}
```

> TODO 待区分桶排序与计数排序。

## Reference

1. [计数排序 - 维基百科，自由的百科全书](http://zh.wikipedia.org/wiki/%E8%AE%A1%E6%95%B0%E6%8E%92%E5%BA%8F) - 中文版的维基感觉比英文版的好理解些。
2. [Counting Sort Visualization](https://www.cs.usfca.edu/~galles/visualization/CountingSort.html) - 动画真心不错~ 结合着看一遍就理解了。


