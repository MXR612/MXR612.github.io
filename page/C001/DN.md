## D

### 题目描述

给出两个包含小写字母的字符串$a,b$，求字符串$a$满足以下条件的子序列集$A$：

0. $length \leq 10$
1. 相邻两个字符不相同

$b$的子串集为$B$.

求$A \cup B$的大小(包含的字符串个数).

### 输入格式

两行共两个字符串$a$和$b$。

### 输出格式

一行一个数表示答案

### 样例1

#### Input

```
mxxr
mxr
```

#### Output

```
6
```

### 数据范围

0. 05pts：$a,b$均为空串
1. 25pts：$length_a,length_b \leq 20$, 2000ms
2. 30pts：$length_a\leq 20$
3. 40pts：无特殊要求, 只有通过所有测试点才能取得此子任务的分数

对于一般的数据:$length_a,length_b \leq 10^6$, 500ms500Mib, C++11, With-O2,


