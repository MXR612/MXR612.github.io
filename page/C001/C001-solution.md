# 题解

> 标程请在[出题人的Github](https://github.com/MXR612/OI-log/tree/master/my/001)查阅（陈某慎入）

## A

> 送分题

### 暴力



### 100pts线段树1：维护区间最小值和数量（验题人）

### 100pts线段树2：维护区间长度线段数量（出题人）

## B

> 大水题

### 0-5pts搜索

### 01-20pts双向搜索

状态压缩的是每个点选了没有，枚举选边情况求出相同状态下最大权值和。

状态数（大概）不会很多

### 2-5pts求最大边权

### 3-10pts线性DP

设计状态$f_{i,j}(j \in \{0,1\})$为点$i$可用或不可用时最大贡献。

### 4-15pts树形DP

用3中设计的状态，在dfs时做即可。

### 5-25pts环上DP

显然经典的$O(n^2)$DP不可行。我们随便找一个点开始，设计状态如下：

$f_{i,j,k}$表示开始点的状态是$j$，到点$i$的状态是$k$时最大贡献。

我们从开始点向两个方向各跑一次环，做线性DP，最后枚举不选的边和开始点的状态，合并两边的贡献。

### 0123456-100pts基环树上DP

把34拼起来：先找出环，对于每个环上的点求出子树内答案，最后环上DP即可。

## C

> 中水题



## D

> 小水题

出题人想出一道子序列自动机+AC自动机，然后被学弟模拟秒了。
