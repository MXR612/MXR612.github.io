---
ID: 116
post_title: Amazing John的P30拍照贼棒 (AJ)
post_name: 'amazing-john%e7%9a%84p30%e6%8b%8d%e7%85%a7%e8%b4%bc%e6%a3%92-aj'
author: mxr612
post_date: 2021-03-15 17:44:35
layout: page
link: https://mxr612.top/?page_id=116
published: true
tags: [ ]
categories: [ ]
---
<h2>题目背景</h2>

众所周知， Amazing John很喜欢用他的P30拍照。今天他想跟他的学生们合照一张，但是SSL-OI有个不成文的规定：教练在合照前都会请大家吃一次CFK！于是AJ打算先把CFK准备好。

经历过的都清楚，CFK的钱取之于民用之于民，所以现在他决定现打开他的监控。

<h2>题目描述</h2>

这一天，机房里有$n$个LSP，因为某些奇怪的原因，今天每个LSP都给另一个LSP发了一份色图。

AJ当然知道这些事情，虽然平时他是不管的，但今天不同了！

<ol>
<li>每次AJ都会选择一对LSP，每张色图罚款$1$円。</li>
<li>因为AJ是个仁慈的人，所以对于每个LSP他都只忍心罚款一次（作为发色图的人或者收色图的人）</li>
</ol>

AJ想知道他最多可以获得多少钱？（钱越多，大家吃得就越好）

<h2>输入格式</h2>

第$0$行一个数$n$，表示机房里有多少个LSP。

随后$n$行，第$i \in [1,n]$行两个数$a,b$，表示第$i$个LSP发了$b$张色图给$a$。

<h2>输出格式</h2>

一行一个整数，表示AJ最多能收多少钱。

<h2>样例</h2>

<h3>样例0</h3>

<h4>Input</h4>

<pre><code class="line-numbers">8
2 2
3 0
1 0
3 3
2 1
4 1
2 2
1 0
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">5
</code></pre>

<h3>样例1</h3>

<h4>Input</h4>

<pre><code class="line-numbers">5
2 43
3 35
1 86
1 12
2 24
</code></pre>

<h4>OutPut</h4>

<pre><code class="line-numbers">110
</code></pre>

<h2>数据范围</h2>

<ol>
<li>10pts：$n&lt;=20$</li>
<li>05pts：存在一个人收发了色图$n-1$次，有一份色图中没有色图(欸,还没发呢), 但与这个人无关</li>
<li>05pts：存在一个人收发了色图$n-1$次</li>
<li>10pts：所有LSP都有且只有收发色图一次，有一份色图中没有色图</li>
<li>15pts：有一份色图中没有色图，且这条边不是桥</li>
<li>15pts：所有LSP都有且只有收发色图一次</li>
<li>20pts：$n&lt;=10^3$</li>
<li>20ts：无特殊要求</li>
</ol>

对于一般的数据，$n \leq 10^6$, 1000ms128mb,with-O2