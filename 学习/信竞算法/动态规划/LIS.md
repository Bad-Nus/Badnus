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

- （ $K$ 维）偏序关系： $(i\lt j)\wedge (\forall k\in[1,K],a[k]_i\lt a[k]_j)$
- （ $K$ 维）逆偏序关系： $(i\lt j)\wedge (\forall k\in[1,K],a[k]_i\gt a[k]_j)$

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

我们设 $f_i$ 为长度为 $i$ 的 LIS 末尾元素的最小值，我们发现 $f$ 单调递增，且 $f_i$ 越小必然越优，由此我们可以贪心地维护 $f_i$ 。

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

如此我们便可转化为一维偏序。
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

## K 维偏序

对 $k$ 维偏序问题，我们有如下的解法及其复杂度

| 方法         | 时间复杂度                         | 空间复杂度                                                                   |
| ---------- | ----------------------------- | ----------------------------------------------------------------------- |
| 暴力         | $O(n^{2})$                    | $O(n)$                                                                  |
| KD 树       | $O(n^{\frac{2k-1}{k}})$       | $O(n)$                                                                  |
| 树套树        | $O(n\log^{k-1}{n})$           | $O(n\log^{k-1}{n})$                                                     |
| CDQ 分治     | $O(n\log^{k-1}{n})$           | $O(n)$                                                                  |
| Bitset 黑科技 | $O(k\frac{1}{\omega}{n^{2}})$ | $O(k\frac{1}{\omega}{n^{\frac{3}{2}}})\sim O(k\frac{1}{\omega}{n^{2}})$ |

由于 $\log^{k-1}n$ 随 $k$ 增加迅速，当 $k\ge 4$ 时适合采用 bitset ，跑的飞快。
### 暴力
QwQ
```cpp
#include<bits/stdc++.h>
using namespace std;
#define rep(i,x,y) for(auto i=x;i<=y;++i)
const int N=1e5+5,M=10;
int n,m,a[N][M],ans,cnt[N],fl;
int main() {
    n=read(),m=read();
    rep(i,1,n)rep(j,1,m)a[i][j]=read();
    rep(i,1,n){
        rep(j,1,i-1){
            fl=1;
            rep(k,1,m)if(a[i][k]<a[j][k])fl=0;
            ans+=fl;
        }
        ++cnt[ans],ans=0;
    }
    rep(i,1,n)wrt(cnt[i]),pc('\n');
    return 0;
}
```
### CDQ

搜集自 [SkyWave](https://www.luogu.me/article/say1s590) 的原创模板

```cpp
template <typename Tp>
struct kDPO<Tp, 0> {
	const vector<vector<Tp>> &arr;
	int k;

	kDPO(const vector<vector<Tp>> &arr_) : arr(arr_) {
		k = arr[0].size();
	}

	vector<int> a, cnt, ans;
	vector<vector<int>> b;
	vector<int> hero;
	void cdq(int l, int r) {
		if (l == r) {
			return ;
		}

		int mid = (l + r) >> 1;
		cdq(l, mid);
		cdq(mid + 1, r);

		int i = l, j = mid + 1;
		b[0].clear();
		while (i <= mid || j <= r) {
			if (j > r || (i <= mid && arr[a[i]][1] <= arr[a[j]][1])) {
				b[0].push_back(a[i]);
				++i;
			} else {
				b[0].push_back(a[j] | 1 << 31);
				++j;
			}
		}
		for (int i = 0; i < r - l + 1; ++i) {
			a[i + l] = b[0][i] & 2147483647;
		}

		cdq(0, r - l, 0);
	}
	void cdq(int l, int r, int d) {
		if (l == r) {
			return ;
		}

		int mid = (l + r) >> 1;
		cdq(l, mid, d);
		cdq(mid + 1, r, d);

		int i = l, j = mid + 1;
		hero.clear();
		if (d == k - 3) {
			int sum = 0;
			while (i <= mid || j <= r) {
				if (j > r || (i <= mid && arr[b[d][i] & 2147483647][k - 1] <= arr[b[d][j] & 2147483647][k - 1])) {
					sum += b[d][i] >> 31 ? 0 : cnt[b[d][i] & 2147483647];
					hero.emplace_back(b[d][i]);
					++i;
				} else {
					ans[b[d][j] & 2147483647] += b[d][j] >> 31 ? sum : 0;
					hero.emplace_back(b[d][j]);
					++j;
				}
			}
			memcpy(b[d].data() + l, hero.data(), sizeof(int) * (r - l + 1));
			return ;
		}
		b[d + 1].clear();
		while (i <= mid || j <= r) {
			if (j > r || (i <= mid && arr[b[d][i] & 2147483647][d + 2] <= arr[b[d][j] & 2147483647][d + 2])) {
				if (!(b[d][i] >> 31)) {
					b[d + 1].push_back(b[d][i]);
				}
				hero.emplace_back(b[d][i]);
				++i;
			} else {
				if (b[d][j] >> 31) {
					b[d + 1].push_back(b[d][j]);
				}
				hero.emplace_back(b[d][j]);
				++j;
			}
		}
		memcpy(b[d].data() + l, hero.data(), sizeof(int) * (r - l + 1));

		if (!b[d + 1].empty()) {
			cdq(0, (int)b[d + 1].size() - 1, d + 1);
		}
	}

	vector<int> operator () () {
		int n = (int)arr.size();
		if (k == 1) {
			vector<array<Tp, 1>> a(n);
			for (int i = 0; i < n; ++i) {
				a[i][0] = arr[i][0];
			}
			return kDPO<Tp, 1>(a)();
		}
		if (k == 2) {
			vector<array<Tp, 2>> a(n);
			for (int i = 0; i < n; ++i) {
				a[i][0] = arr[i][0];
				a[i][1] = arr[i][1];
			}
			return kDPO<Tp, 2>(a)();
		}

		vector<int> ord(n);
		iota(ord.begin(), ord.end(), 0);
		sort(ord.begin(), ord.end(), [&](int x, int y) {
			return arr[x] < arr[y];
		});

		vector<pair<int, int>> equa;
		equa.reserve(n);
		cnt.resize(n);
		for (int i = 0; i < n; ) {
			int j = i + 1;
			for ( ; j < n && arr[ord[j]] == arr[ord[i]]; ++j) {
				equa.emplace_back(ord[j], ord[i]);
			}

			a.emplace_back(ord[i]);
			cnt[ord[i]] = j - i;

			i = j;
		}
		ans.resize(n);
		hero.reserve(n);
		b.resize(k - 2);
		for (vector<int> &i : b) {
			i.reserve(n);
		}

		cdq(0, (int)a.size() - 1);

		for (int i = 0; i < n; ++i) {
			ans[i] += cnt[i] - 1;
		}
		for (pair<int, int> i : equa) {
			ans[i.first] = ans[i.second];
		}
		return ans;
	}
};
```

### Bitset

#### Bitset 1

搜集自 [_Wallace_](https://www.cnblogs.com/-Wallace-/p/bit-parti-ord.html) 的转载

```cpp
/*
 * Author : _Wallace_
 * Source : https://www.cnblogs.com/-Wallace-/
 * Problem : bitset 求解较高维偏序
 */

// rank[k][v] 表示 k 维中值为 v 的点的编号 
for (int k = 0; k < K; k++)
	for (int i = 1; i * b <= n; i++)
		for (int j = 1; j <= i * b; j++)
			dat[k][i].set(rank[k][j]); // 分块预处理 

for (int i = 1; i <= n; i++) {
	bitset<N> ans, tmp;
	ans.set(); // 一开始设为全 1（按位与操作）
	for (int k = 0; k < K; k++) {
		tmp.reset(); // 每一维都要重置 
		int p = point[k][i] / b; // 计算整块的范围 
		tmp |= dat[k][p]; // 整块取现成 
		for (int j = p * b + 1; j <= point[k][i]; j++)
			tmp.set(rank[k][j]); // 暴力扫散块 
		ans &= tmp; // 对每一维按位与 
	}
	cout << ans.count() - 1 << endl; // 统计答案 
}
```

#### Bitset 2

```cpp
#include<bits/stdc++.h>
using namespace std;
#define MAX 45000
inline int read()
{
	int x=0,t=1;char ch=getchar();
	while((ch<'0'||ch>'9')&&ch!='-')ch=getchar();
	if(ch=='-')t=-1,ch=getchar();
	while(ch<='9'&&ch>='0')x=x*10+ch-48,ch=getchar();
	return x*t;
}
int n,blk;
bitset<45000> bs[15][250];
pair<int,int> val[15][MAX];
int bl[MAX],bll[MAX],blr[MAX];
int K,num;
long long Ans;
int f[15][MAX];
int find(int k,int x)
{
	int l=1,r=n,ans=0;
	while(l<=r)
	{
		int mid=(l+r)>>1;
		if(val[k][mid].first<=x)ans=x,l=mid+1;
		else r=mid-1;
	}
	return ans;
}
inline bitset<MAX> getbst(int p,int x)
{
	bitset<MAX> ans;ans.reset();
	int pp=find(p,x);
	if(pp<=0)return ans;
	int pre=(pp-1)/blk;
	int st=pre*blk+1;
	ans=bs[p][pre];
	for(int i=st;i<=pp;++i)ans.set(val[p][i].second);
	return ans;
}
void Solve()
{
	bitset<MAX> ans;ans.reset();
	for(int i=1;i<=n;++i)
	{
		ans.set();
		for(int j=1;j<=K;++j)
			ans&=getbst(j,f[j][i]);
		Ans+=ans.count()-1;
	}
}
int main()
{
	freopen("partial_order_plus.in","r",stdin);
	freopen("partial_order_plus.out","w",stdout);
	n=read();blk=sqrt(n);K=read()+1;
	for(int i=1;i<=n;++i)val[1][i]=make_pair(f[1][i]=i,i);
	for(int j=2;j<=K;++j)
		for(int i=1;i<=n;++i)
			val[j][i]=make_pair(f[j][i]=read(),i);
	for(int i=1;i<=K;++i)sort(&val[i][1],&val[i][n+1]);
	for(int i=1;i<=n;++i)
		bl[i]=(i-1)/blk+1;num=bl[n];
	for(int i=1;i<=num;++i)
		bll[i]=(i-1)*blk+1,blr[i]=i*blk;blr[num]=n;
	for(int j=1;j<=K;++j)
		for(int i=1;i<=num;++i)
		{
			bs[j][i]=bs[j][i-1];
			for(int k=bll[i];k<=blr[i];++k)
				bs[j][i][val[j][k].second]=1;
		}
	Solve();
	printf("%lld\n",Ans);
	return 0;
}
```