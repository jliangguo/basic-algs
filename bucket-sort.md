# Bucket Sort - 桶排序

桶排序和归并排序有那么点点类似，也使用了归并的思想。大致步骤如下：

1. 设置一个定量的数组当作空桶。
2. Divide - 从待排序数组中取出元素，将元素按照一定的规则塞进对应的桶子去。
3. 对每个非空桶进行排序，通常可在塞元素入桶时进行插入排序。
4. Conquer - 从非空桶把元素再放回原来的数组中。

## 编程实现

```java
/**
 * Bucket sort
 * @param array array to be sorted
 * @param bucketCount number of buckets
 * @return array sorted in ascending order
 */
public static int[] bucketSort(int[] array, int bucketCount) {
    if (bucketCount <= 0) throw new IllegalArgumentException("Invalid bucket count");
    if (array.length <= 1) return array; //trivially sorted

    int high = array[0];
    int low = array[0];
    for (int i = 1; i < array.length; i++) { //find the range of input elements
        if (array[i] > high) high = array[i];
        if (array[i] < low) low = array[i];
    }
    double interval = ((double)(high - low + 1))/bucketCount; //range of one bucket

    ArrayList<Integer> buckets[] = new ArrayList[bucketCount];
    for (int i = 0; i < bucketCount; i++) { //initialize buckets
        buckets[i] = new ArrayList();
    }

    for (int i = 0; i < array.length; i++) { //partition the input array
        buckets[(int)((array[i] - low)/interval)].add(array[i]);
    }

    int pointer = 0;
    for (int i = 0; i < buckets.length; i++) {
        Collections.sort(buckets[i]); //mergeSort
        for (int j = 0; j < buckets[i].size(); j++) { //merge the buckets
            array[pointer] = buckets[i].get(j);
            pointer++;
        }
    }
    return array;
}

```

## 复杂度分析

内部排序算法复杂度为$$C(n/m)$$，n为数组大小，m为桶个数。所以，总的算法复杂度为$$O(m \cdot C(n/m))$$。

## Reference

1. [Bucket Sort Visualization](http://www.cs.usfca.edu/~galles/visualization/BucketSort.html) - 动态演示。
2. [桶排序 - 维基百科，自由的百科全书](http://zh.wikipedia.org/wiki/%E6%A1%B6%E6%8E%92%E5%BA%8F)
