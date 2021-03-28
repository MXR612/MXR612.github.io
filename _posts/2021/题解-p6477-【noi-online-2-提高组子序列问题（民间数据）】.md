---
ID: 158
post_title: '题解 P6477 【[NOI Online #2 提高组]子序列问题（民间数据）】'
post_name: '%e9%a2%98%e8%a7%a3-p6477-%e3%80%90noi-online-2-%e6%8f%90%e9%ab%98%e7%bb%84%e5%ad%90%e5%ba%8f%e5%88%97%e9%97%ae%e9%a2%98%ef%bc%88%e6%b0%91%e9%97%b4%e6%95%b0%e6%8d%ae%ef%bc%89%e3%80%91'
author: mxr612
post_date: 2021-03-16 16:27:47
layout: post
link: https://mxr612.top/?p=158
published: true
tags:
  - luogu
  - 离散化
  - 离线
  - 线段树
categories:
  - OI
  - 题解
---
本人蒟蒻,没怎么写过不可重集的题,所以第一眼就想到了做过的唯一一道题<a class="wp-editor-md-post-content-link" href="https://www.luogu.com.cn/problem/P1972">P1972 [SDOI2009]HH的项链</a>

<del>首先离散化</del>

那题是维护每个值最后出现的位置,然后离线查询.
这题要维护所有区间的答案,还要平方,怎么办呢?

转化转化就好啦!
我们只关心每个值最后出现的位置,想象一个01数组,我们把相同的值最后出现的位置放1,其余放0,我们一个一个加入值,然后维护这个东西.(相当于枚举右端点)

然后我们对这个01数组做后缀和就好了,
对于每个右端点,答案就是每个后缀和的平方(感性理解)

但是这样太朴素了,完全跟那道题一样的做法,必TLE

我们发现,每次加入一个已经有过的值,会把上一次出现的位置从1变成0,而当前位置变成1.

那么从上一次出现的位置(包含)往前的所有位置作为左端点时,答案都不会改变,而往后一直到右端点的f()值会+1

如果这个值没有出现过,视为出现在0位置

那么我们用平方线段树维护一下,对于每个右端点,暴力修改区间,当前枚举的右端点的答案就是根节点的值

<del>稍微</del>卡一下常,注意一下long long就好了

<pre><code class="language-cpp line-numbers">/**
 * NOI Online 2
 * B
 * sequence
 */

#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;

#include &lt;algorithm&gt;

#define MXN (1000020)
#define MOD (1000000007)

int N, A[MXN], las[MXN] = {0};
long long ans = 0;

struct LSH {
    int a, b, d;
} lsh[MXN];
bool cmp1(LSH x, LSH y) {
    return x.a &lt; y.a;
}
bool cmp2(LSH x, LSH y) {
    return x.d &lt; y.d;
}

struct node {
    int l, r, s;
    long long t, w, p;
    node *ls, *rs;
}* root = NULL;

void build(node*&amp; x, int l, int r) {
    if (r &lt; l)
        return;
    if (x == NULL)
        x = (node*)calloc(sizeof(node), 1);
    x-&gt;l = l, x-&gt;r = r, x-&gt;s = r - l + 1;
    if (l &lt; r)
        build(x-&gt;ls, l, (l + r) &gt;&gt; 1), build(x-&gt;rs, ((l + r) &gt;&gt; 1) + 1, r);
}

void modify(node* x, int l, int r) {
    if (x == NULL || x-&gt;r &lt; l || r &lt; x-&gt;l)
        return;
    if (l &lt;= x-&gt;l &amp;&amp; x-&gt;r &lt;= r)
        x-&gt;p = (x-&gt;p + (x-&gt;w &lt;&lt; 1) + x-&gt;s) % MOD, x-&gt;w += x-&gt;s, ++x-&gt;t;
    else {
        if (x-&gt;t &gt; 0) {
            register node* xy = x-&gt;ls;
            long long t = x-&gt;t;
            xy-&gt;p = (xy-&gt;p + (t * xy-&gt;w &lt;&lt; 1) + xy-&gt;s * t * t) % MOD,
            xy-&gt;w += t * xy-&gt;s, xy-&gt;t += t;
            xy = x-&gt;rs;
            xy-&gt;p = (xy-&gt;p + (t * xy-&gt;w &lt;&lt; 1) + xy-&gt;s * t * t) % MOD,
            xy-&gt;w += t * xy-&gt;s, xy-&gt;t += t;
            x-&gt;t = 0;
        }
        modify(x-&gt;ls, l, r);
        modify(x-&gt;rs, l, r);
        x-&gt;p = x-&gt;ls-&gt;p + x-&gt;rs-&gt;p;
        x-&gt;w = x-&gt;ls-&gt;w + x-&gt;rs-&gt;w;
    }
}

signed main() {
    freopen("sequence.in", "r", stdin);
    freopen("sequence.out", "w", stdout);

    scanf("%d", &amp;N);
    for (register int i = 1, p; i &lt;= N; ++i)
        scanf("%d", &amp;lsh[i].a), lsh[i].d = i;

    std::sort(&amp;lsh[1], &amp;lsh[N + 1], cmp1);
    for (register int i = 1, p = 0; i &lt;= N; ++i)
        lsh[i].b = (lsh[i].a == lsh[i - 1].a) ? (p) : (++p);
    std::sort(&amp;lsh[1], &amp;lsh[N + 1], cmp2);
    for (register int i = 1; i &lt;= N; ++i)
        A[i] = lsh[i].b;

    build(root, 1, N);

    for (register int i = 1; i &lt;= N; ++i) {
        modify(root, las[A[i]] + 1, i);
        ans = (ans + root-&gt;p) % MOD;
        las[A[i]] = i;
    }

    printf("%lld", ans);

    return 0;
}
</code></pre>

菜鸭淼淼的做法就是简sha单gua且暴yu力chun