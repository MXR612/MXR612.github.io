# SSL-OI夏日合宿 2020.08.19

> 大佬们在打NOI网络同步赛day2, 我只能在初中划水惹.
> 
> 今天这套是做过的原题, 好像是JZOJ? 因为是比较简单的那种, 所以就没打了, 比赛时间来口胡一下题解算了.
> 
> 本来想找找以前的代码然后秒AK的, 但是好像以前没有做好标记, 文件搜索搜不到. 所以今天就没有代码了~

## T1 KC看星(star)

### 题意

给出${8}$个点的坐标, 问: 能否构成一个正方形和一个矩形? (四点共线不算). 输出正方形和矩形四个角的坐标.

### 口胡

搜索或枚举四个点就好, 然后随便判断一下两条直线是否垂直, 长度是否相等就好.

## T2 KC的瓷器(porcelain)

### 题意

有$n<=100$排物品, 每排不超过$100$个物品. 每排只能从左右两边取连续的物品, 选$m$个, 求物品价值和最大.

### 口胡

很容易想到这是一个分组背包. 对于每行枚举一个$i,j$作为左右两边的分界点即可. 每行的复杂度是$O(N^2)$, 总复杂度是$O(N^3)$.

## T3 开心小屋(smile)

### 题意

给出一个图, 问: 是否有正环? 最小正环大小?

点数$n<=300$, 边数$m<=5000$, 边权$-10000<=C_{ij}<=1000$.

### 口胡

搜索&剪枝. 

**剪枝1:** 一个显然且常用的剪枝:当深度大于当前$Ans$时停止搜索.

**剪枝2:** 若搜索到的和小于等于$0$时停止搜索, 因为一个正环肯定存在从环上某个点开始求和永远非负.

> 后来研究了一下, 确实去年十月底看过这套题, 但是最后没有去写.
> 
> 口胡王者在此?