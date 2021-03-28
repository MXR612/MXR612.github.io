---
ID: 130
post_title: >
  SSL-OI夏日合宿 杂题 POI2018水箱
  最小生成树
post_name: 'ssl-oi%e5%a4%8f%e6%97%a5%e5%90%88%e5%ae%bf-%e6%9d%82%e9%a2%98-poi2018%e6%b0%b4%e7%ae%b1-%e6%9c%80%e5%b0%8f%e7%94%9f%e6%88%90%e6%a0%91'
author: mxr612
post_date: 2021-03-15 17:50:06
layout: post
link: https://mxr612.top/?p=130
published: true
tags:
  - POI
  - 最小生成树
categories:
  - OI
  - 题解
---
<blockquote>
  POI2018
  
  luoguP5952
</blockquote>

<h2>题意</h2>

给一个$n*m$的方格水箱, 相邻两个格子之间有一道有高度的墙.

墙的高度和水位不超过$H$, 问: 有多少种水位情况.

两种情况不同当且仅当存在至少一个格子在两种情况中的水位高度不同(高度是整数).

<h2>故事</h2>

<blockquote>
  今天故事即正解, 走向人生巅峰.
</blockquote>

不知道为啥这题好眼熟, 总感觉是刚学OI那会<font size="4">$_{儿}$</font>试图去做但没做出来的题目.

显然如果我们从小往大枚举水位, 每个格子只会被最低一个墙影响(合并). 那么就从小往大枚举墙, 合并两个水域的时候尝试合并两个答案.

设$f_i$是水域$i$的答案, $g_i$是水域$i$的高度. 刚开始每个格子都是一个水域, 且高度为$0$. 若将水域$i$和水域$j$合并成水域$k$, 且合并的墙高为$h$, 转移为:

$$
f_k=(f_i+h-g_i)*(f_j+h-g_j)&#92;
g_k=h.
$$

(一个格子$i$从水位$g_i$提升到$h$有$h-g_i$种水位)

<strong>总结</strong>: 我们发现这是一个最小生成树的过程, 那么直接建图跑最小生成树, 合并的时候统计答案就好. (我当初怎么没想到)

<blockquote>
  在这种记点方式下注意数组大小
  
  写丑了一点吸氧过的
</blockquote>

<pre><code class="language-cpp line-numbers">#define MXNM (5000020)
#define XJQ (1000000007)

#include &lt;stdio.h&gt;

#include &lt;queue&gt;

int n, m, H;

int node(int i, int j) { return i * m + j; }

struct Edge {
    int u, v, w;
    bool operator&lt;(const Edge E) const { return w &gt; E.w; }
};

long long f[MXNM], g[MXNM];

std::priority_queue&lt;Edge&gt; edge;

int fa[MXNM];

int find(int x) { return (fa[x] == x) ? (x) : (fa[x] = find(fa[x])); }
void merge(int x, int y, long long h) { x = find(x), y = find(y), f[x] = ((f[x] + h - g[x]) * (f[y] + h - g[y])) % XJQ, g[x] = h, fa[y] = x; }

signed main() {
#ifndef ONLINE_JUDGE
    freopen("P5952.in", "r", stdin);
#endif

    scanf("%d%d%d", &amp;n, &amp;m, &amp;H);

    for (int i = 1, j, w; i &lt;= n; ++i)
        for (j = 1; j &lt; m; ++j)
            scanf("%d", &amp;w), edge.push(Edge{node(i, j), node(i, j + 1), w});
    for (int i = 1, j, w; i &lt; n; ++i)
        for (j = 1; j &lt;= m; ++j)
            scanf("%d", &amp;w), edge.push(Edge{node(i, j), node(i + 1, j), w});
    for (int i = 1, j; i &lt;= n; ++i)
        for (j = 1; j &lt;= m; ++j)
            fa[node(i, j)] = node(i, j), f[node(i, j)] = 1;

    for (int i = n * m; i &gt; 1; --i) {
        while ((!edge.empty()) &amp;&amp; (find(edge.top().u) == find(edge.top().v))) edge.pop();
        if (!edge.empty()) merge(edge.top().u, edge.top().v, edge.top().w);
    }

    printf("%lld", (f[find(node(1, 1))] + H - g[find(node(1, 1))]) % XJQ);

    return 0;
}
</code></pre>

<blockquote>
  反正就是一道小水题, 不知道怎么变成紫题的, <del>不知道怎么被北大爷选进杂题的</del>.
</blockquote>