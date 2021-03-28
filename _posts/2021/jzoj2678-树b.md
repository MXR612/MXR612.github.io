---
ID: 151
post_title: JZOJ2678 树B
post_name: 'jzoj2678-%e6%a0%91b'
author: mxr612
post_date: 2021-03-15 21:44:30
layout: post
link: https://mxr612.top/?p=151
published: true
tags:
  - DP
  - 图
categories:
  - OI
  - 题解
---
<h2><a href="https://jzoj.net/senior/#main/show/2678" target="_blank" rel="noopener">题</a></h2>

<div class="span12 well"><fieldset>
<h4>Description</h4>
<div class="content">
<p class="p0">已知无向连通图G由N个点，N-1条边组成。每条边的边权给定。现要求通过删除一些边，将节点1与另M个指定节点分开，希望删除的边的权值和尽量小，求此最小代价。</p>
</div>
</fieldset></div>

<div>
<div class="span6 well"><fieldset>
<h4>Input</h4>
<div class="content">
每个输入文件中仅包含一个测试数据。</p>
<p class="p0">第一行包含两个整数N,M。</p>
<p class="p0">第二行至第N行每行包含3个整数,A、B、C，表示节点A与节点B有一条边相连，边权为C。</p>
<p class="p0">第N+1行至第N+M行每行包含一个整数X，表示要求与节点1分开的节点。</p>
</div>
</fieldset></div>
<div class="span6 well"><fieldset>
<h4>Output</h4>
<div class="content">
<p class="p0">输出文件仅包含一个整数，表示最小代价。</p>
</div>
</fieldset></div>
</div>

<h2>思路</h2>

&nbsp;树的遍历+DP

不知道为什么大家都喜欢叫树形DP,好高逼的感觉.害得我昨天那题一听是什么"树形DP"就不敢写了

对于每个必删的点 i ,很容易想到我们不必遍历以其为根的子树,<br />　　这样的情况花费是 cost[i]=E[V[i].dad->V[i]]

对于一个不必删的点 j ,<br />　删掉其子树中所有必删的点的花费是<br />　　　cost[j]=SUM(cost[儿子1]+cost[儿子2]+......+cost[儿子n]);<br />　我们可以考虑删掉以其为根的子树,这样当然就删除了其子树中的所有必删点<br />　　花费 cost[j]=E[V[i].dad->V[i]]

考虑最小情况,所以点 n 的值应为 min(E[V[i].dad->V[i]],SUM(cost[儿子1]+cost[儿子2]+......+cost[儿子n]))

由于树的性质,每个点的DP值只给自己父亲用,所以不必存下,利用返回值带回即可.

<h2>代码(有问题欢迎讨论)</h2>

&nbsp;

<div class="cnblogs_code" onclick="cnblogs_code_show('9c96766c-dc9f-480a-9667-bdad8075e02b')"><img id="code_img_closed_9c96766c-dc9f-480a-9667-bdad8075e02b" class="code_img_closed" src="http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif" alt="" /><img id="code_img_opened_9c96766c-dc9f-480a-9667-bdad8075e02b" class="code_img_opened" style="display: none;" onclick="cnblogs_code_hide('9c96766c-dc9f-480a-9667-bdad8075e02b',event)" src="http://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif" alt="" />
<div id="cnblogs_code_open_9c96766c-dc9f-480a-9667-bdad8075e02b" class="cnblogs_code_hide">
<pre><span style="color: #008080;"> 1</span> #include <iostream>
<span style="color: #008080;"> 2</span> #include <algorithm>
<span style="color: #008080;"> 3</span> <span style="color: #0000ff;">using</span> <span style="color: #0000ff;">namespace</span><span style="color: #000000;"> std;
</span><span style="color: #008080;"> 4</span> 
<span style="color: #008080;"> 5</span> <span style="color: #0000ff;">int</span><span style="color: #000000;"> N,M;
</span><span style="color: #008080;"> 6</span> 
<span style="color: #008080;"> 7</span> <span style="color: #0000ff;">struct</span> edge{<span style="color: #0000ff;">int</span> fr,to,vl;}E[<span style="color: #800080;">2000000</span><span style="color: #000000;">];
</span><span style="color: #008080;"> 8</span> <span style="color: #0000ff;">int</span> cmpS(edge m,edge n){<span style="color: #0000ff;">return</span> (m.fr==n.fr)?(m.to<n.to):(m.fr<<span style="color: #000000;">n.fr);}
</span><span style="color: #008080;"> 9</span> 
<span style="color: #008080;">10</span> <span style="color: #0000ff;">struct</span> node{<span style="color: #0000ff;">int</span> l,r,flag,vl;}V[<span style="color: #800080;">1000001</span><span style="color: #000000;">];
</span><span style="color: #008080;">11</span> 
<span style="color: #008080;">12</span> <span style="color: #0000ff;">int</span> dfs(<span style="color: #0000ff;">int</span> dad,<span style="color: #0000ff;">int</span> dv,<span style="color: #0000ff;">int</span> id){<span style="color: #008000;">//</span><span style="color: #008000;">他老爸是谁(李刚) / 他到他老爸多远 / 他是谁</span>
<span style="color: #008080;">13</span>     <span style="color: #0000ff;">if</span>(V[id].flag==<span style="color: #800080;">1</span>)<span style="color: #008000;">//</span><span style="color: #008000;">要删就删,不多话</span>
<span style="color: #008080;">14</span>         <span style="color: #0000ff;">return</span><span style="color: #000000;"> dv;
</span><span style="color: #008080;">15</span>     <span style="color: #0000ff;">int</span> s=<span style="color: #800080;">0</span>;<span style="color: #008000;">//</span><span style="color: #008000;">儿子的和SUM(没儿子返回0)</span>
<span style="color: #008080;">16</span>     <span style="color: #0000ff;">for</span>(<span style="color: #0000ff;">int</span> i=V[id].l;i<=V[id].r;++<span style="color: #000000;">i){
</span><span style="color: #008080;">17</span>         <span style="color: #0000ff;">if</span>(E[i].to!=dad){<span style="color: #008000;">//</span><span style="color: #008000;">你爸爸还是你爸爸,只能找自己儿子</span>
<span style="color: #008080;">18</span>             s+=<span style="color: #000000;">dfs(id,E[i].vl,E[i].to);
</span><span style="color: #008080;">19</span> <span style="color: #000000;">        }
</span><span style="color: #008080;">20</span> <span style="color: #000000;">    }
</span><span style="color: #008080;">21</span>     <span style="color: #0000ff;">return</span><span style="color: #000000;"> min(dv,s);
</span><span style="color: #008080;">22</span> <span style="color: #000000;">}
</span><span style="color: #008080;">23</span> 
<span style="color: #008080;">24</span> <span style="color: #0000ff;">int</span><span style="color: #000000;"> main(){
</span><span style="color: #008080;">25</span>     
<span style="color: #008080;">26</span> <span style="color: #008000;">//</span><span style="color: #008000;"> 输入数据</span>
<span style="color: #008080;">27</span>     cin>>N>><span style="color: #000000;">M;
</span><span style="color: #008080;">28</span>     <span style="color: #0000ff;">for</span>(<span style="color: #0000ff;">int</span> i=<span style="color: #800080;">1</span>;i<N;++i)<span style="color: #008000;">//</span><span style="color: #008000;">无向图存成两个有向边</span>
<span style="color: #008080;">29</span>         cin>>E[i].fr>>E[i].to>>E[i].vl,E[N-<span style="color: #800080;">1</span>+i]=<span style="color: #000000;">{E[i].to,E[i].fr,E[i].vl};
</span><span style="color: #008080;">30</span>     <span style="color: #0000ff;">for</span>(<span style="color: #0000ff;">int</span> i=<span style="color: #800080;">1</span>,a;i<=M;++<span style="color: #000000;">i)
</span><span style="color: #008080;">31</span>         cin>>a,V[a].flag=<span style="color: #800080;">1</span>;<span style="color: #008000;">//</span><span style="color: #008000;">标记要删
</span><span style="color: #008080;">32</span> <span style="color: #008000;">//</span><span style="color: #008000;"> 初始化图</span>
<span style="color: #008080;">33</span>     <span style="color: #0000ff;">for</span>(<span style="color: #0000ff;">int</span> i=<span style="color: #800080;">1</span>;i<=N;++<span style="color: #000000;">i)
</span><span style="color: #008080;">34</span>         V[i]={<span style="color: #800080;">0</span>,-<span style="color: #800080;">1</span>,V[i].flag,<span style="color: #800080;">0</span><span style="color: #000000;">};
</span><span style="color: #008080;">35</span>     sort(&E[<span style="color: #800080;">1</span>],&E[<span style="color: #800080;">2</span>*N-<span style="color: #800080;">1</span><span style="color: #000000;">],cmpS);
</span><span style="color: #008080;">36</span>     <span style="color: #0000ff;">for</span>(<span style="color: #0000ff;">int</span> i=<span style="color: #800080;">1</span>;i<=<span style="color: #800080;">2</span>*N-<span style="color: #800080;">1</span>;++<span style="color: #000000;">i){
</span><span style="color: #008080;">37</span>         <span style="color: #0000ff;">if</span>(E[i].fr!=E[i-<span style="color: #800080;">1</span><span style="color: #000000;">].fr){
</span><span style="color: #008080;">38</span>             V[E[i].fr].l=<span style="color: #000000;">i;
</span><span style="color: #008080;">39</span>             V[E[i-<span style="color: #800080;">1</span>].fr].r=i-<span style="color: #800080;">1</span><span style="color: #000000;">;
</span><span style="color: #008080;">40</span> <span style="color: #000000;">        }
</span><span style="color: #008080;">41</span> <span style="color: #000000;">    }
</span><span style="color: #008080;">42</span> <span style="color: #008000;">//</span><span style="color: #008000;"> 深搜/输出</span>
<span style="color: #008080;">43</span>     cout<<dfs(<span style="color: #800080;">0</span>,1e9,<span style="color: #800080;">1</span>);<span style="color: #008000;">//</span><span style="color: #008000;">可怜的根节点没爸爸所以他离他爸很远(要不你当他爸做根节点</span><span style="color: #008000;">//</span><span style="color: #008000;">别打我)</span>
<span style="color: #008080;">44</span>     
<span style="color: #008080;">45</span>     <span style="color: #0000ff;">return</span> <span style="color: #800080;">0</span><span style="color: #000000;">;
</span><span style="color: #008080;">46</span>     
<span style="color: #008080;">47</span> }</pre>
</div>
<span class="cnblogs_code_collapse">能理解尽量自己码</span></div>

&nbsp;

&nbsp;

淼仔mxxr第一次在博客写题解,大佬轻喷.