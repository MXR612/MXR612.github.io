## B

### 题目描述

$n$个点$n$条带权边的联通图，求最大带权匹配。

### 输入格式

第$0$行一个数$n$。

随后$n$行，第$i \in [1,n]$行两个数$a,b$，$i$与$a$连一条权值为$b$的边。

### 输出格式

一行一个整数，最大带权匹配的边权和。

### 样例1

#### Input

```
5
2 43
3 35
1 86
1 12
2 24
```

#### Output

```
110
```

### 数据范围

0. 10pts：$n<=20$
1. 05pts：存在一点的度数为$n-1$，存在一条边权值为$0$且不与该点相连
2. 05pts：存在一点的度数为$n-1$
3. 10pts：所有点的度数为$2$，存在一条权值为$0$的边
4. 15pts：存在一条权值为$0$的边，且这条边不是桥
5. 15pts：所有点的度数为$2$
6. 20pts：$n<=10^3$
7. 20ts：无特殊要求

对于一般的数据，$n \leq 10^6$, 1000ms128mb, C++11, with-O2