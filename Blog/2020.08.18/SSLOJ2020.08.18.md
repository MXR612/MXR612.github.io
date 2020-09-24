# SSL-OI夏日合宿 2020.08.18

> 今天大佬们都去打NOI网络同步赛了, 就我一个没报名QwQ.
>
> 于是就只有一个组别, 好像题还挺简单.(不是
> 
> 然后就被**初一**爆踩了 /doge

## T1 分火腿

### 题意

给出$n$根火腿, 要求切成大小相等的$m$份. 求最小切几刀.

### 故事

~~显然这是一道给小学生写的水题.~~ 对于每$(n,m)$根火腿, 我们都可以少切一刀. 于是直接输出$(m-1)-((n,m)-1)$即$m-(n,m)$就好.

``` cpp
#include <stdio.h>

int T;

int gcd(int a, int b) { return (b == 0) ? (a) : gcd(b, a % b); }

signed main() {
    freopen("A.in", "r", stdin);

    scanf("%d", &T);

    for (int i, n, m; T-- > 0;)
        scanf("%d%d", &n, &m), printf("%d\n", m - gcd(n, m));

    return 0;
}
```

实际上这也是正解.

## T2 工资

### 题意

给出一个数组$arr$, 最多划分成$m$块. 对划分出的每一块求和, 求最大值最小.

### 故事

T2就开始不会了QwQ.

求最大值最小的问题一般就二分答案吧? 那么我们对于二分出的最大值$lim$, 贪心地遍历$arr$, 一旦求和超过$lim$就另起一段. 总觉得贪心哪里不对, 但又不会证, 也想不出更好的方法.

``` cpp
#define MXN (100020)

#include <stdio.h>

#include <algorithm>

int n, m;
long long a[MXN];

int check(int lim) {
    int res = 0, cnt = 0;
    for (int i = 0; i < n; ++i)
        if ((cnt += a[i]) > lim)
            cnt = a[i], ++res;
        else if (cnt == lim)
            cnt = 0, ++res;
    return res + (cnt > 0);
}

long long l, r = MXN * MXN, md;

signed main() {
    freopen("B.in", "r", stdin);
    scanf("%d%d", &n, &m);
    for (int i = 0; i < n; ++i)
        scanf("%lld", &a[i]), l = std::max(l, a[i]);

    while (l < r) {
        if (check(md = (l + r) / 2) <= m)
            r = md;
        else
            l = md + 1;
    }

    printf("%d", r);

    return 0;
}
```

结果WA90? 奇奇怪怪. 稍微改了一贪心函数就过了.

待会研究一下贪心为啥正确.

## T3 欠扁的CD

### 题意

给出$n$个数, 从中选$k$个, 使他们的$gcd$最大.

### 故事

T3就已经完全不会了, 感觉题目读得有点奇怪? 于是乎没有故事...

### 正解

好像果然是读题的问题, 如果多读几遍说不定就读懂了. 不出意外地, 这题也是大水题.

我们开一个$500000$的数组, 记录每个值出现的次数. 再从大到小枚举答案$ans$, 然后统计它的所有倍数出现次数的和, 若大于等于$k$即为答案. 是的, 正解非常暴力.

复杂度为 $O(\sum_{i=1}^{N}\frac{i}{N})$ 大概就是 $O(N\log{N})$. (我也不知道为啥)

``` cpp
#define MXN (500020)

#include <stdio.h>

#include <algorithm>

int n, k, top;
int cnt[MXN];
long long ans;

signed main() {
    freopen("C.in", "r", stdin);

    scanf("%d%d", &n, &k);

    for (int i = 0, x; i < n; ++i)
        scanf("%d", &x), ++cnt[x], top = std::max(top, x);

    for (int i = top, j, res; i > 0; --i) {
        for (j = i, res = 0; j <= top; j += i)
            res += cnt[j];
        if (res >= k) {
            ans = i;
            break;
        }
    }

    printf("%lld", ans * k);

    return 0;
}
```

> 中午就把题全改完了, 今天的题确实简单.
> 
> 下午把昨天的题改一改吧.
>
> 然后看一看今天他们打的NOI?