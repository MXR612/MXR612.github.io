---
ID: 112
post_title: 小膜法师 (Mod)
post_name: '%e5%b0%8f%e8%86%9c%e6%b3%95%e5%b8%88-mod'
author: mxr612
post_date: 2021-03-15 17:43:34
layout: page
link: https://mxr612.top/?page_id=112
published: true
tags: [ ]
categories: [ ]
---
<h2>题目背景</h2>

众所周知，准备拯救$SSL$大地的<a class="wp-editor-md-post-content-link" href="https://www.luogu.com.cn/user/35056">小魔法师</a>降临到五百亩时，第一个见到的OIer是<a class="wp-editor-md-post-content-link" href="https://www.luogu.com.cn/user/30496">CEM</a>! 在腐佬的腐化下, 小魔法师变成了小膜法师QwQ.

<h2>题目描述</h2>

小膜法师有$n$个前辈，每个前辈都有一个QQ号。（AJ：你们的QQ号怎么一个个都那么长？）

小膜法师已经膜过了一些前辈，现在他想用下面的方式膜一些前辈：

<ol>
<li>小膜法师是一个冲动的人，他有时候会选择膜拜Q号在$[l,r]$内的学长<strong>一次</strong>。</li>
<li>小膜法师是一个善变的人，他有时候会选择撤回Q号在$[l,r]$内的<strong>一次</strong>膜拜。</li>
</ol>

如果小膜法师记错了，准备对一个没有被膜拜过的学长撤回膜拜，你就偷偷帮他把<strong>这次操作</strong>取消叭～

小膜法师想知道他每次操作后有多少学长是没有被膜拜过的.（被膜拜次数等于$0$）

<h2>输入格式</h2>

第$0$行两个整数$n,m$，分别表示前辈的个数和操作的个数。

第$1$行$n$个整数，分别表示每个学长的QQ号(小科普:世界上最小的Q号是$10000$)。

第$2$行$n$个数，第$a_i$个数表示已经对第$i$个学长膜拜了$a_i$。

第$i \in [3,2+m]$行，每行三个整数$o,l,r$（$o \in {0,1}$）。

$o$表示操作的类型，$l,r$表示操作的区间。

<h2>输出格式</h2>

$m$行，每行输出一个数表示答案。

<h2>样例</h2>

<h3>样例0</h3>

<h4>Input</h4>

<pre><code class="line-numbers">3 5
74751 20031120 99824353
0 0 0
0 8848 7355608
0 25252 19260817
0 38000000 998344353 
1 998244353 998244853
0 1000000007 1000000009
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">2
2
1
1
1
</code></pre>

<h3>样例1</h3>

<h4>Input</h4>

<pre><code class="line-numbers">3 4
20000 30000 10000
0 0 0
0 10000 20000
0 20000 30000
1 10000 30000
1 10000 30000
</code></pre>

<h4>Output</h4>

<pre><code class="line-numbers">1
0
2
2
</code></pre>

<h2>提示说明</h2>

<ol>
<li>40pts：$n \leq 10^3$</li>
<li>15pts：只有膜拜</li>
<li>15pts：只有撤回</li>
<li>20pts：无特殊要求</li>
</ol>

对于一般的数据$n \leq 10^6$, $l,r,val_i$在$long\ long$范围内, 5000ms128MB, With-O2,
只有取得所有测试点的分数才能获得该子任务的分数.
输入数据较多, 时间已经开到极限, 但还请注意读入优化和代码常数.