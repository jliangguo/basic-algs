# Stack - 栈

栈是一种LIFO（Last In First Out）的数据结构，常用方法有添加元素、取栈顶元素，弹出栈顶元素，判断栈是否为空。

## 编程实现

### Java

```java
Deque<Integer> stack = new ArrayDeque<Integer>();
s.size(); // size of stack
```

方法如下：

- `boolean isEmpty()` - 判断栈是否为空，若使用Stack类构造则为empty()

- `E peek()` - 取栈顶元素，不移除

- `E pop()` - 移除栈顶元素并返回该元素

- `void push(E item)` - 向栈顶添加元素


