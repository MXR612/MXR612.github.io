---
ID: 118
post_title: B
post_name: b
author: mxr612
post_date: 2021-03-15 17:44:54
layout: page
link: https://mxr612.top/?page_id=118
published: true
tags: [ ]
categories: [ ]
---
<h3>题目描述</h3>

$n$个点$n$条带权边的联通图，求最大带权匹配。

<h3>输入格式</h3>

第$0$行一个数$n$。

随后$n$行，第$i \in [1,n]$行两个数$a,b$，$i$与$a$连一条权值为$b$的边。

<h3>输出格式</h3>

一行一个整数，最大带权匹配的边权和。

<h3>样例1</h3>

<h4>Input</h4>

<pre><code class="line-numbers">5
2 43
3 35
1 86
1 12
2 24
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">110
</code></pre>

<h3>数据范围</h3>

<ol>
<li>10pts：$n&lt;=20$</li>
<li>05pts：存在一点的度数为$n-1$，存在一条边权值为$0$且不与该点相连</li>
<li>05pts：存在一点的度数为$n-1$</li>
<li>10pts：所有点的度数为$2$，存在一条权值为$0$的边</li>
<li>15pts：存在一条权值为$0$的边，且这条边不是桥</li>
<li>15pts：所有点的度数为$2$</li>
<li>20pts：$n&lt;=10^3$</li>
<li>20ts：无特殊要求</li>
</ol>

对于一般的数据，$n \leq 10^6$, 1000ms128mb, C++11, with-O2