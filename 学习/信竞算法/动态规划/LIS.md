# 定义

数组中删除若干个数后，构造一个单调递增的序列，这个序列的最大长度即最长上升子序列，下简称 **LIS** 。

形式化地，已知
$$A=\{a_1,a_2,\ldots,a_n\},B=\{a_{k_1},a_{k_2},\ldots,a_{k_m}\},其中 \forall i,j\in[1,m]且i\lt j,有 k_{i-1}\lt k_i且a_{k_{i-1}}\lt a_{k_i}$$

求 $m_\operatorname{max}$

## 顺序对

对于式子中 $i\lt j且 a_i\lt a_j$ 又被称为**顺序对**。

其相对的**逆序对** $i\lt j且 a_i\gt a_j$ 具有相似的单调性质，因此对于部分逆序对的题目可以参考 LIS 的思路进行思考。

还存在相等对，即 $i\lt j且 a_i = a_j$
## 偏序问题
- （一维）偏序关系： $(i\lt j)\wedge (a_i\lt a_j)$
- （一维）逆偏序关系： $(i\lt j)\wedge (a_i\gt a_j)$

推广至 $K$ 维，有

- （ $n$ 维）偏序关系： $(i\lt j)\wedge (\forall k\in[1,K],a[k]_i\lt a[k]_j)$
- （ $n$ 维）逆偏序关系： $(i\lt j)\wedge (\forall k\in[1,K],a[k]_i\gt a[k]_j)$

LIS 本质是一维偏序问题，可以推广到 $K$ 维偏序问题
# 解法
设 $f_i$ 为以第 $i$ 位为结尾的 LIS 长度,那么根据定义有 
$$f_i=\Big(\operatorname{max}\limits_{(j\lt i)\wedge(a_j\lt a_i)} f_j\Big)+1$$
## 暴力
对每一位 $i$ 暴力枚举 $\forall j\lt i$ 即可

复杂度 $O(n^2)$
```cpp
rep(i,1,n){
	rep(j,1,i-1)if(a[j]<a[i])f[i]=max(f[i],f[j]+1);
	ans=max(ans,f[i]);
}
```

## 前缀优化
对于 $i$ 的 $O(n)$ 枚举不可避免，瓶颈在于取最大值，考虑做前缀优化 DP ，维护第 $i$ 位的 LIS 长度 $f_i$ ，式子变成了查询第 $i$ 位的前缀最大，将序列按权值从小到大排序后，以权值的原位置 $id_i$ 为下标 $i$ ，用 $i$ 的前缀最大 $f_j$ 更新即可。

考虑复杂度，进行了 $n$ 次查询和维护前缀和，树状结构 $O(n\log n)$ ，块状结构 $O(n^{\frac{3}{2}})$

### 树状数组维护代码
```cpp
int n,f[N];
struct nd{
    int v,id;
    bool operator<(const nd&a)const{return v<a.v;}
}a[N];
int lowbit(int x){return x&-x;}
void add(int x,int y){
    while(x<=n)f[x]=max(f[x],y),x+=lowbit(x);
}
int ask(int x,int res=0){
    while(x)res=max(f[x],res),x-=lowbit(x);
    return res;
}
int main(){
    cin>>n;
    rep(i,1,n)cin>>a[i].v,a[i].id=i;
    sort(a+1,a+1+n);
    rep(i,1,n)if(i==1||a[i].v!=a[i-1].v)add(a[i].id,ask(a[i].id)+1);
    cout<<(ask(n))<<endl;
    return 0;
}
```

## 二分

二分基于贪心思想

我们设 $f_i$ 为长度为 $i$ 的 LIS 末尾元素的最小值，我们发现 $f$ 单调递增。且 $f_i$ 越小必然越优，由此我们可以贪心地维护 $f_i$ 。

那么对于每一位 $a_j$ 考虑贡献：

- 若 $f_m\lt a_j$ ，那么增长，令 $f_{m+1}=a_j$
- 若 $f_m \ge a_j$ ，那么考虑维护 $f_i$ 的最小，我们设 $f_k$ 为最小的满足 $f_i\ge a_j$ 的位置，那么：
	- $f_{1\ldots k-1}$ 不满足 $f_i \ge a_j$ ，不更新
	- $f_{k+1\ldots m}$ 是由 $f_k$ 转移而来，相当于 LIS 的第 $k$ 位最优已经是 $a_j$ 。如果 $a_j$ 参与构成 $f_{k+1\ldots m}$ ，那么 $a_j$ 必然被多次使用，证明显然；若不参与构成又没有考虑的必要。
	- 综上令 $f_k=a_j$ 即可

复杂度 $O(n\log n)$
```cpp
int n,cnt,c[N],x;

int main() {
	cin>>n;
	rep(i,1,n){
		cin>>x;
		if(x>c[cnt])c[++cnt]=x;
		else *lower_bound(c+1,c+1+cnt,x)=x;
	}
	cout<<cnt;
	return 0;
}

```
## M 元 LIS 计数

即统计长度为 $m$ 的 LIS 的个数。

设 $f_{i,j}$ 为以 $a_j$ 结尾长度为 $i$ 的 LIS 个数，注意到只要用 $\forall k\lt j$ 处长度为 $i-1$ 的 LIS 接上 $a_j$ 考虑贡献即可，那么根据加法原理，有 $f_{i,j}=\sum\limits_{(k\lt j)\wedge (a_k\lt a_j)} (f_{i-1,k})$ 。

我们注意到 $O(nm)$ 的枚举部分不可避免，瓶颈在求顺序对 LIS 的个数和，考虑做法：

1. 暴力枚举，由式子可得复杂度 $O(n^2 m)$ ，**不可行**
2. 二分仅能维护 LIS 长度，无法统计个数，**不可行**
3. 前缀和优化 DP ，**可行**

对前缀和优化 DP ，由于 $k$ 有两个限制条件： $(k\lt j)\wedge (a_k\lt a_j)$ ，可以先将 $a$ 对权值离散化，再对每层 $i$ 严格按下标 $j$ 的顺序处理 $f_{i,j}$ ，用数据结构维护这个权值前缀和即可。

具体地，对每 $i$ 层维护一个以权值为下标的前缀和 $pre$ ，内层处理第 $j$ 位时：
1. 令 $f_{i,j}+=pre_{j-1}$ 维护贡献。
2. 令 $pre_j$ 单点增加 $f_{i-1,j}$ 维护前缀和。

考虑复杂度，进行了 $O(nm)$ 次查询和维护前缀和，对树状结构 $O(nm\log n)$ ，块状结构 $O(n^{\frac{3}{2}}m)$ 。

### 树状数组维护代码

此代码对答案进行取模

```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
#define per(u,x,y) for(int u=x;u>=y;--u)
#define gc getchar
#define pc putchar
using namespace std;
const int N=1e5+1,M=51,mod=1e9+7;
typedef long long ll;
ll read(){
    ll x=0,f=1;
    char ch=gc();
    while(ch<'0'||ch>'9')ch=='-'&&(f=-1,0),ch=gc();
    while(ch>='0'&&ch<='9')x=(x*10)+(ch^48),ch=gc();
    return x*f;
}
void wrt(ll x){
    if(x<0)x=-x,pc('-');
    if(x>9)wrt(x/10);
    pc(x%10^48);
}
ll n,m,q,ans,a[N],s[N],f[M][N],c[N];
int lowbit(int x){return x&-x;}
ll query(int x,ll sum=0){
    while(x)sum=(sum+c[x])%mod,x-=lowbit(x);
    return sum;
}
void upd(int x,ll v){while(x<=m)c[x]=(c[x]+v)%mod,x+=lowbit(x);}
int main(){
    n=read(),q=read();
    rep(i,1,n)s[i]=a[i]=read();
    sort(s+1,s+1+n);
    m=unique(s+1,s+n+1)-s-1;
    rep(i,1,n)f[1][i]=1,a[i]=(lower_bound(s+1,s+1+m,a[i])-s);
    rep(i,2,q){
        memset(c,0,sizeof c);
        rep(j,1,n)f[i][j]=(f[i][j]+query(a[j]-1))%mod,upd(a[j],f[i-1][j]);
    }
    rep(i,1,n)ans=(ans+f[q][i])%mod;
    wrt(ans);
    return 0;
}
```

## 二维偏序

即对一个二维点集 $\bigcup \{(x,y)\in R^2\}$，找到最长的 $x_i$ 和 $y_i$ 均构成 LIS 的点序列

形式化地，已知
$$A=\{p_i\in R^2\vert p_i=(x,y),i\in[1,n]\}, B=\{p_{k_1},p_{k_2},\ldots,p_{k_m}\}, 其中 \forall i, j\in[1, m]且 i\lt j, 有 k_{i-1}\lt k_i 且 (x_{k_{i-1}}\lt x_{k_i})\wedge (y_{k_{i-1}}\lt y_{k_i})$$

求 $m_{\operatorname{max}}$

容易想到对满足 $x_k\lt x_j$ 的 $y$ 做 LIS 即可

但，注意到受 $x_k\lt x_j$ 影响，我们并不能直接通过对 $x$ 排序后找 $y$ 的顺序对。因为需要同时满足三个条件： $(k\lt j)\wedge (x_k\lt x_j)\wedge (y_k\lt y_j)$ ，但我们对 $x$ 排序只满足了 $x_k\le x_j$ 。

为了排除这一影响，我们对相等的 $x$ 按 $y$ 递减排序即可，这样 $x_k=x_j$ 的部分就恒有 $y_k\ge y_j$ ，不再对顺序对的条件成立性产生影响。

如此我们便转化为一维偏序
### 树状数组

用树状数组维护前缀最大优化

```cpp
int n,c[N],cnt;
struct Point{
    int x,y;
    bool operator<(const Point&p)const{return x==p.x?y>p.y:x<p.x;}
}p[N];
struct Node{
    int v,id;
    bool operator<(const Node&a)const{return v<a.v;}
}a[N];
int lowbit(int x){return x&-x;}
void add(int x,int y){while(x<=n)c[x]=max(c[x],y),x+=lowbit(x);}
int ask(int x,int res=0){
    while(x)res=max(c[x],res),x-=lowbit(x);
    return res;
}
int main(){
    cin>>n;
    rep(i,1,n)cin>>p[i].x>>p[i].y;
    sort(p+1,p+n+1);//按x升序，x相同时按y降序排序
    rep(i,1,n)a[i].v=p[i].y,a[i].id=i;//提取y坐标并离散化
    sort(a+1,a+n+1);
    rep(i,1,n){
        if(i==1||a[i].v!=a[i-1].v)++cnt;
        p[a[i].id].y=cnt;//用离散化后的值替换原y值
    }
    rep(i,1,n)add(p[i].y,ask(p[i].y-1)+1);//对离散化后的y序列求LIS
    cout<<ask(n)<<endl;
    return 0;
}
```

### M 元二维偏序计数
与一维同理

```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
#define per(u,x,y) for(int u=x;u>=y;--u)
#define gc getchar
#define pc putchar
using namespace std;
const int N=1e5+1,M=51,mod=1e9+7;
typedef long long ll;
ll read(){
    ll x=0,f=1;
    char ch=gc();
    while(ch<'0'||ch>'9')ch=='-'&&(f=-1,0),ch=gc();
    while(ch>='0'&&ch<='9')x=(x*10)+(ch^48),ch=gc();
    return x*f;
}
void wrt(ll x){
    if(x<0)x=-x,pc('-');
    if(x>9)wrt(x/10);
    pc(x%10^48);
}
struct Point{
    int x,y;
    bool operator<(const Point& p)const{return x==p.x?y>p.y:x<p.x;}
}p[N];
struct Node{
    int v,id;
    bool operator<(const Node& a)const{return v<a.v;}
}a[N];
ll n,m,q,ans,f[M][N],c[N];
int lowbit(int x){return x&-x;}
void upd(int x,ll v){while(x<=m)c[x]=(c[x]+v)%mod,x+=lowbit(x);}
ll query(int x,ll sum=0){
    while(x)sum=(sum+c[x])%mod,x-=lowbit(x);
    return sum;
}
int main(){
    n=read(),q=read();
    rep(i,1,n)p[i].x=read(),p[i].y=read();
    sort(p+1,p+n+1);//按x升序，x相同时按y降序排序
    rep(i,1,n)a[i].v=p[i].y,a[i].id=i;
    sort(a+1,a+n+1);
    rep(i,1,n){
        f[1][i]=1;
        if(i==1||a[i].v!=a[i-1].v)++m;
        p[a[i].id].y=m;
    }
    rep(i,2,q){
        memset(c,0,sizeof(c));
        rep(j,1,n){
            f[i][j]=query(p[j].y-1);
            upd(p[j].y,f[i-1][j]);
        }
    }
    rep(i,1,n)ans=(ans+f[q][i])%mod;
    wrt(ans);
    return 0;
}
```

## 三维偏序

## K 维偏序

对 $k$ 维偏序问题，我们有如下的解法及其复杂度



