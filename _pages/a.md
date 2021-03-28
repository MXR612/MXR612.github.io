---
ID: 114
post_title: A
post_name: a
author: mxr612
post_date: 2021-03-15 17:44:13
layout: page
link: https://mxr612.top/?page_id=114
published: true
tags: [ ]
categories: [ ]
---
<h3>题目描述</h3>

考虑一个$map$里面有$n$个$key$在$long\ long$范围内的数,每次选择一些在区间$[l,r]$内的$key$对$val$进行操作：

<ol>
<li>$+1$</li>
<li>$-1$</li>
</ol>

若操作$1$的区间中有$0$，取消这次操作。

询问每次操作后有多少个$val=0$?

<h3>输入格式</h3>

第$0$行两个整数$n,m$，分别表示$key$的个数和操作的个数。

第$1$行$n$个整数，分别表示第$i$个$key$。

第$2$行$n$个数，表示第$key_i$的初值$val_i$。

第$i \in [3,2+m]$行，每行三个整数$o,l,r$（$o \in {0,1}$）。

$o$表示操作的类型，$l,r$表示操作的区间。

<h3>输出格式</h3>

$m$行，每行输出一个数表示答案。

<h3>样例1</h3>

<h4>Input</h4>

<pre><code class="line-numbers">3 4
10001 20002 30003
0 0 0
0 10001 20002
0 20002 30003
1 10001 30003
1 20002 30003
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">1
0
2
2
</code></pre>

<h3>数据范围</h3>

<ol>
<li>40pts：$n \leq 10^3$, $length_{key} \leq 10^6$</li>
<li>20pts：只有操作0</li>
<li>20pts：只有操作1</li>
<li>20pts：无特殊要求</li>
</ol>

对于一般的数据$n \leq 10^6$, $l,r,val_i$在$long\ long$范围内,   5000ms128MB, C++11, With-O2,<br />
只有取得所有测试点的分数才能获得该子任务的分数.<br />
输入数据较多, 时间已经开到极限, 但还请注意读入优化和代码常数.