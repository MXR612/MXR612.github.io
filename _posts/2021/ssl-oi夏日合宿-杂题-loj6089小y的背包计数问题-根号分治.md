---
ID: 128
post_title: 'SSL-OI夏日合宿 杂题 LOJ#6089小Y的背包计数问题 根号分治'
post_name: 'ssl-oi%e5%a4%8f%e6%97%a5%e5%90%88%e5%ae%bf-%e6%9d%82%e9%a2%98-loj6089%e5%b0%8fy%e7%9a%84%e8%83%8c%e5%8c%85%e8%ae%a1%e6%95%b0%e9%97%ae%e9%a2%98-%e6%a0%b9%e5%8f%b7%e5%88%86%e6%b2%bb'
author: mxr612
post_date: 2021-03-15 17:49:02
layout: post
link: https://mxr612.top/?p=128
published: true
tags:
  - LOJ
  - 根号分治
categories:
  - OI
  - 题解
---
<blockquote>
  LOJ #6089
  
  这题是集训第一天晚上的杂题, 由于本人本性爱咕, 所以集训第二周才来补题解.
</blockquote>

<h2>前置知识</h2>

<a class="wp-editor-md-post-content-link" href="https://www.luogu.com.cn/problem/P1776">多重背包</a>: 用单调队列优化, 做到$O(NM)$的复杂度.

<a class="wp-editor-md-post-content-link" href="https://www.luogu.com.cn/problem/P1025">数的划分</a>: $n$个整数由$k$个整数组成的方案数(可重/不可重), $O(NK)$复杂度DP.

<h2>题意</h2>

背包大小为$n$, 物品数量为$n$, 第$i$个物品的重量为$i$, 数量为$i$.

问: 将背包装满的方案数是多少?

<h2>正解</h2>

对于大于$\sqrt{N}$的物品, 相当于没有数量限制. 我们用数的划分(可重方式)求出答案就好.

对于小于$\sqrt{N}$的物品, 我们用多重背包求出答案. 由于物品数量是$\sqrt{N}$, 背包大小是$N$, 所以复杂度为$O(N\sqrt{N})$.