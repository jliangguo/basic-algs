# Dynamic Programming - 动态规划算法

**核心思想**：动态规划（DP，Dynamic Programming）是算法设计方法之一，其本质是对问题**状态的定义**和**状态转移方程的定义**。动态规划是通过**拆分问题**，定义问题状态和状态之间的关系，使得问题能够以**递推**（或者说分治）的方式去解决。因此，如何拆分问题是动态规划的核心。

摘自[维基百科](https://en.wikipedia.org/wiki/Dynamic_programming)：
> **Dynamic programming** (also known as dynamic optimization) is a method for solving a complex problem by **breaking it down into a collection of simpler subproblems**, solving each of those subproblems just once, and storing their solutions – ideally, using a memory-based data structure. 

## 概念介绍

1. 什么是状态的定义？

 “状态”用来描述该问题的子问题的解。

2. 什么是状态转移方程？
 
 上述状态定义好之后，状态和状态之间的关系式，就叫做**状态转移方程**，即是带有条件的递推式。
 
## 适用情况

- **最优子结构**性质。如果问题的最优解所包含的子问题的解也是最优的，我们就称该问题具有最优子结构性质（即满足最优化原理）。最优子结构性质为动态规划算法解决问题提供了重要线索。
- **无后效性**。即子问题的解一旦确定，就不再改变，不受在这之后、包含它的更大的问题的求解决策影响。
- **子问题重叠**性质。子问题重叠性质是指在用递归算法自顶向下对问题进行求解时，每次产生的子问题并不总是新问题，有些子问题会被重复计算多次。动态规划算法正是利用了这种子问题的重叠性质，对每一个子问题只计算一次，然后将其计算结果保存在一个表格中，当再次需要计算已经计算过的子问题时，只是在表格中简单地查看一下结果，从而获得较高的效率。

## 典型问题解析

### LCS - 最长公共子序列

**问题描述**：给定两个字符串$$s_{1}s_{2} \cdots s_{n}$$和$$t_{1}t_{2} \cdots t_{n}$$。求出这两个字符串最长的公共子序列的长度。字符串$$s_{1}s_{2} \cdots s_{n}$$的子序列指可以表示为$$s_{i_1}s_{i_2} \cdots s_{i_m} (i_1 \lt i_2 \lt \cdots \lt i_m)$$的序列。

这个问题是被称为最长公共子序列问题（LCS，Longest Common Subsequence）的著名问题。不妨用如下定义：

$$
dp[i][j] :=  s_{1}s_{2} \cdots s_{i}和t_{1}t_{2} \cdots t_{j}对应的LCS的长度
$$

由此，$$s_{1}s_{2} \cdots s_{i+1}$$和$$t_{1}t_{2} \cdots t_{j+1}$$对应的公共子序列可能是:

当$$s_{i+1}=t_{j+1}$$时，

1. 在$$s_{1}s_{2} \cdots s_{i}$$和$$t_{1}t_{2} \cdots t_{j}$$的公共子序列末尾追加上$$s_{i+1}$$；

2. $$s_{1}s_{2} \cdots s_{i}$$和$$t_{1}t_{2} \cdots t_{j+1}$$的公共子列 

3. $$s_{1}s_{2} \cdots s_{i+1}$$和$$t_{1}t_{2} \cdots t_{j}$$的公共子列

所以，其递推关系式就是：



$$dp[i+1][j+1] = \left\{
\begin{aligned}
dp[i][j] + 1 & , & (s_{i+1}=t_{j+1}) \\
max(dp[i+1][j], dp[i][j+1]) & , & 其他 
\end{aligned}
\right.

$$

这个递推式可用$$O(nm)$$计算出来，$$dp[n][m]$$就是LCS的长度。


## Reference

1. [Dynamic programming - From Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Dynamic_programming)
