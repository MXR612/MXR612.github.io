---
ID: 124
post_title: D
post_name: d
author: mxr612
post_date: 2021-03-15 17:46:44
layout: page
link: https://mxr612.top/?page_id=124
published: true
tags: [ ]
categories: [ ]
---
<h3>题目描述</h3>

给出两个包含小写字母的字符串$a,b$，求字符串$a$满足以下条件的子序列集$A$：

<ol>
<li>$length \leq 10$</li>
<li>相邻两个字符不相同</li>
</ol>

$b$的子串集为$B$.

求$A \cup B$的大小(包含的字符串个数).

<h3>输入格式</h3>

两行共两个字符串$a$和$b$。

<h3>输出格式</h3>

一行一个数表示答案

<h3>样例1</h3>

<h4>Input</h4>

<pre><code class="line-numbers">mxxr
mxr
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">6
</code></pre>

<h3>数据范围</h3>

<ol>
<li>05pts：$a,b$均为空串</li>
<li>25pts：$length_a,length_b \leq 20$, 2000ms</li>
<li>30pts：$length_a\leq 20$</li>
<li>40pts：无特殊要求, 只有通过所有测试点才能取得此子任务的分数</li>
</ol>

对于一般的数据:$length_a,length_b \leq 10^6$, 500ms500Mib, C++11, With-O2,