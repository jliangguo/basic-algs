# Queue - 队列

Queue是一个FIFO（先进先出）的数据结构，并发中使用较多，可以安全地将对象从一个任务传给另一个任务。

## 编程实现

### Java

Queue在Java中是Interface，一种实现是LinkedList，LinkedList向上转型为Queue，Queue通常不能存储`null`元素，否则与`poll()`等方法的返回值混淆。

```java
Queue<Integer> q = new LinkedList<Integer>();
int qLen = q.size(); // get queue length
```

方法如下：

|方法|Throws exception|Returns special value|
|--|--|--|
|Insert|add(e)|offer(e)|
|Remove|remove()|poll()|
|Examine|element()|peek()|

优先考虑右侧方法，右侧元素不存在时返回`null`，判断非空时使用`isEmpty()`方法，继承自Collection。

### Go

> TODO 待补充Go语言实现。

## Priority Queue - 优先队列

应用程序常常需要处理带有优先级的业务，优先级最高的业务首先得到服务。因此优先队列这种数据结构应运而生。优先队列中的每个元素都有各自的优先级，优先级最高的元素最先得到服务；优先级相同的元素按照其在优先队列中的顺序得到服务。

优先队列可以使用数组或链表实现，从时间和空间复杂度来说，往往用二叉堆来实现。

> TODO 什么是二叉堆？列出其Java语言实现。

Java 中提供`PriorityQueue`类，该类是Interface Queue的另外一种实现，和LinkedList的区别主要在于排序行为而不是性能，基于priority heap实现，非 synchronized，故多线程下应使用`PriorityBlockingQueue`。默认为自然序（ 小根堆），需要其他排序方式可自行实现`Comparator`接口，选用合适的构造器初始化。使用迭代器遍历时不保证有序，有序访问时需要使用`Arrays.sort(pq.toArray())`。

不同方法的时间复杂度：

- enqueuing and dequeuing: `offer`,`poll`,`remove` and `add     - $$O(log n)$$
- Object: `remove(object)` and `contains(object)` - $$O(n)$$
- retrieval: `peek`, `element` and `size` - $$O(1)$$

## Deque - 双端队列

双端队列（deque，全名是double-ended queue）可以让你在任何一端添加或者移除元素，因此它是一种具有队列和栈性质的数据结构。

### Java

Java在1.6之后提供了Deque接口，既可使用`ArrayDeque`（数组）来实现，也可以使用`linkedList`（链表）来实现。前者是一个数组外加首尾索引，后者是双向链表。

```java
Deque<Integer> deque = new ArrayDeque<Integer>();
```

||First Element (Head) ||Last Element (Tail)||
|--|--|--|--|--|
||Throws exception|Special value|Throws exception|Special value|
|Insert|addFirst(e)|offerFirst(e)|addLast(e)| offerLast(e)|
|Remove|removeFirst()|pollFirst()|removeLast()| pollLast()|
|Examine|getFirst()|peekFirst()|getLast()|peekLast()|

其中`offerLast`和Queue中的`offer`功能相同，都是从尾部插入。

### Go
