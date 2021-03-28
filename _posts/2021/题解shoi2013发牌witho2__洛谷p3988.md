---
ID: 134
post_title: '[题解][SHOI2013]发牌withO2__洛谷P3988'
post_name: '%e9%a2%98%e8%a7%a3shoi2013%e5%8f%91%e7%89%8cwitho2__%e6%b4%9b%e8%b0%b7p3988'
author: mxr612
post_date: 2021-03-15 21:32:34
layout: post
link: https://mxr612.top/?p=134
published: true
tags:
  - luogu
  - SHOI
categories:
  - OI
  - 题解
---
由于满心萧然太菜了<br />所以不能过这题wryyyyyy</p>

<img src="https://img2018.cnblogs.com/blog/1733432/201908/1733432-20190803164947161-1384412337.png" alt="" />

已经尽力卡常了(可能是算法不够力)

7mm是水平不够呐,with_O2能过

<h4>做法</h4>

树状数组+二分搜索

将数组考虑为为一个循环队列,"销牌"操作可以考虑为指针的移动.