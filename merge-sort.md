# Merge Sort - 归并排序

核心思想：将两个有序对数组归并成一个更大的有序数组。通常做法为递归排序，并将两个不同的有序数组归并到第三个数组中。

先来看看动图，归并排序是一种典型的**分治**应用。

![](/assets/merge_sort.gif)

归并排序是[外排](https://en.wikipedia.org/wiki/External_sorting)的最好选择，注意大数据量下JVM虚拟机启动参数设置。

## 原地归并

### Java

```java
public static void merge(Comparable[] a, Comparable[] aux, int lo, int mid, int hi) {
    // copy to aux[]
    for (int k = lo; k <= hi; k++) {
        aux[k] = a[k];
    }

    // merge back to a[]
    int i = lo, j = mid + 1;
    for (int k = lo; k <= hi; k++) {
        if (i > mid) a[k] = aux[j++];
        else if (j > hi) a[k] = aux[i++];
        else if (less(aux[j], aux[i])) a[k] = aux[j++];
        else a[k] = aux[i++];
    }
}

private static void sort(Comparable[] a, Comparable[] aux, int lo, int hi) {
    if (hi <= lo) return;

    int mid = lo + (hi - lo) / 2;
    sort(a, aux, lo, mid);
    sort(a, aux, mid + 1, hi);
    merge(a, aux, lo, mid, hi);
}
```

时间复杂度为 $$O(N \log N)$$, 使用了等长的辅助数组，空间复杂度为 $$O(N)$$。

## Reference

1. [Mergesort](http://algs4.cs.princeton.edu/22mergesort/) - Robert Sedgewick 的大作，非常清晰。