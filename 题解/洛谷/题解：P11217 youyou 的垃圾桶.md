# 题面
[P11217 youyou 的垃圾桶](/%E9%A2%98%E9%9D%A2/%E6%B4%9B%E8%B0%B7%E9%A2%98%E9%9D%A2/P11217%20youyou%20%E7%9A%84%E5%9E%83%E5%9C%BE%E6%A1%B6.md#p11217-mx-s4-t1yyoi-r2youyou-%E7%9A%84%E5%9E%83%E5%9C%BE%E6%A1%B6)

![[P11217 youyou 的垃圾桶]]
# 分析
> 我们规定:
> 
> 1. 对一个 $n$ 元序列 $x$ 来说,如果
> $$\sum_{k}^{0}{(2^k\sum_{n}^{i=1}{x_i})}+\sum_{m}^{i=1}{x_i}\lt W \le\sum_{k}^{0}{(2^k\sum_{n}^{i=1}{x_i})}+\sum_{m+1}^{i=1}{x_i}$$
> 	那么 $ans_{x}=(k+1)n+m$
> 
> 2. 对序列 $x$ 进行更改:令 $x_i=x_i+d,i\in [l,r]$
> 	记第 $f$ 次更改所得的序列为 $x_f$
> 	
> 那么最终要求的便是 $ans_{x_f},f\in [1,q]$
# 做法
> 1. 考虑暴力,由与攻击力翻倍机制最多打 $\log W$ 次,复杂度 $O(q\times n\log W)$
> 
> 2. 涉及区间求和,区间修改,容易想到线段树,复杂度 $O(q\log ^2 n+q\log W)$.
> 
> 3. 由于前缀和可优化,容易想到线段树上二分,复杂度 $O(q\log n+q\log W)$.
> 
> 4. 我们可以发现一个性质:要么 $k$ 递减,要么 $k$ 不变时 $m$ 递减.求完第一遍后维护数组更改(差分前缀,线段树,分块等方法)求出后面的 $k$ 和 $m$,复杂度 $O(n\log W+q)$ 或 $O(n\log W+q\log W)$,达到理论最优.
# 代码
## 差分维护
> 出自[原题解](https://www.luogu.com.cn/article/gsv0ssvc)
```cpp
#include <iostream>
using namespace std;
const int Q = 1000005;
const int N = 200005;
long long l[Q],r[Q];
long long d[Q];
int q;
long long int A,B,C;
int M;
int n;
long long a[N];
long long W;
__int128 S;
long long k,m;
long long lst[N];
long long nxt[N];
__int128 camPa,camPb;
__int128 lastW;
__int128 sumf;
long long ass;
void workfor_new()
{
	long long now = 0;
	lst[n + 1] = nxt[n + 1] = lst[0] = nxt[0] = 0;
	sumf = 0;
	for(int i = 1;i <= n;i ++)
	{
		now = now + lst[i];
		a[i] = a[i] + now;
		lst[i] = nxt[i] = 0;
	}
	long long BASE = (1ll << k) - 1;
	long long ok = W - S * BASE;
	long long ove = (1ll << k);
	for(int i = 1;i <= n;i ++)
	{
		if(ok <= a[i] * ove) 
		{
			m = i - 1;
			lastW = ok;
			break;
		}
		ok -= a[i] * ove;
	}
	return;
}
long long ans;
int main()
{
    //freopen("wxyt20.in","r",stdin);
    //freopen("wxyt20.out","w",stdout);
    cin >> n >> q >> W;
    for(int i = 1;i <= n;i ++)
    cin >> a[i],S += a[i];
    for(int i = 1;i <= q;i ++)
    {
      scanf("%lld%lld%lld",&l[i],&r[i],&d[i]);
    }
	for(k = 60;k >= 0;k --) 
	{
		camPb = S;
		camPb *= ((1ll << k) - 1ll);
		camPa = W;
		if(camPb < camPa) break;
	}
	
	workfor_new();
	for(int i = 1;i <= q;i ++)
	{
		S = S + (r[i] - l[i] + 1) * d[i];
		camPb = S;
		camPb *= ((1ll << k) - 1ll);
		camPa = W;
		lst[l[i]] += d[i];
		lst[r[i] + 1] -= d[i];
		nxt[r[i]] += d[i];
		nxt[l[i] - 1] -= d[i];
		if(camPb >= camPa)
		{
			for(;k >= 0;k --)
			{
				camPb = S;
				camPb *= ((1ll << k) - 1ll);
				camPa = W;
				if(camPb < camPa) break; 
			}
			workfor_new();
		}
		else
		{
			long long po = (1ll << k); 
			lastW -= (po - 1) * (r[i] - l[i] + 1) * d[i];
			lastW -= d[i] * po * max(min(r[i],m) - l[i] + 1,0ll); 
			if(l[i] <= m + 1 && m < r[i]) sumf += d[i];
			for(;m >= 1;m --)
			{  
				if(lastW > 0) break;
				sumf += nxt[m];
				lastW += (sumf + a[m]) * po; 
			}
		}
        printf("%lld\n",k*n+m);
	}
	
}
```
## 线段树
> 出自[原题解](https://www.luogu.com.cn/article/2a6kvgjo)
```cpp
#include<bits/stdc++.h>
#define int long long
using namespace std;
const int N=2e5+10;
void read(int &a){
	int s=0,w=1;
	char ch=getchar();
	while(ch<'0'||'9'<ch){
		if(ch=='-')w=-1;
		ch=getchar(); 
	}
	while('0'<=ch&&ch<='9'){
		s=s*10+ch-'0';
		ch=getchar();
	}
	a=s*w;
}
int n,m,W,i,a[N];
struct tree{
	int l,r,pre,add;
}t[N<<2];
void build(int p,int l,int r){
	t[p].l=l,t[p].r=r;
	if(l==r){
		t[p].pre=a[l];
		return;
	}
	int mid=l+r>>1;
	build(p*2,l,mid);
	build(p*2+1,mid+1,r);
	t[p].pre=t[p*2].pre+t[p*2+1].pre;
}
void spread(int p){
	t[p*2].pre+=(t[p*2].r-t[p*2].l+1)*t[p].add;
	t[p*2+1].pre+=(t[p*2+1].r-t[p*2+1].l+1)*t[p].add;
	t[p*2].add+=t[p].add;
	t[p*2+1].add+=t[p].add;
	t[p].add=0;
}
void change(int p,int x,int y,int z){
	if(x<=t[p].l&&t[p].r<=y){
		t[p].pre+=(t[p].r-t[p].l+1)*z;
		t[p].add+=z;
		return;
	}
	spread(p);
	int mid=t[p].l+t[p].r>>1;
	if(x<=mid)change(p*2,x,y,z);
	if(y>mid)change(p*2+1,x,y,z);
	t[p].pre=t[p*2].pre+t[p*2+1].pre;
}
int ask(int p,int res){
	if(t[p].l==t[p].r){
		return t[p].l;
	}
	spread(p);
	int mid=t[p].l+t[p].r>>1;
	if(t[p*2].pre*(1ll<<(i-1))>=res)return ask(p*2,res);
	else return ask(p*2+1,res-t[p*2].pre*(1ll<<(i-1)));
}
signed main(){
	cin>>n>>m>>W;
	for(int j=1;j<=n;j++){
		read(a[j]);
	}
	build(1,1,n);
	while(m--){
		int l,r,d;
		read(l),read(r),read(d);
		change(1,l,r,d);
		i=0;
		int k=2,T=t[1].pre;
		for(i=1;;i++){
			int tot=T*(k-1);
			if(tot>=W)break;
			k*=2;
		}
		int res=W-T*(k/2-1);
		int ans=ask(1,res);
		printf("%lld\n",ans+(i-1)*n-1);
	}
	return 0;
}
```
## 分块
> 出自自己
```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
#define gc getchar()
using namespace std;
const int N=2e5+1;
typedef long long ll;
ll read(){
	ll x=0,w=1;
	char ch = gc;
	while(ch<'0'||ch>'9')((ch=='-')&&(w=-1,0)),ch=gc;
	while(ch>='0'&&ch<='9')x=(x<<3)+x+x+(ch^48),ch=gc;
	return x*w;
}
void wrt(ll x){
	if(x<0)putchar('-'),x=-x;
	if(x>9)wrt(x/10);
	putchar(x%10^48);
}
int n,q,a[N],id[N],len,l,r,d,sid,eid,k,pos;
ll tot,sum[500],tag[500],w,wt,mi[50]={1};
void init(){
//	freopen("wxyt2.in","r",stdin);
	n=read(),q=read(),w=read(),len=sqrt(n);
	rep(i,1,n)a[i]=read(),sum[id[i]=(i-1)/len+1]+=a[i],tot+=a[i];
	k=log2(w*1.0/tot+1)+1;
	rep(i,1,k)mi[i]=mi[i-1]<<1ll;
}
void solve(){
	l=read(),r=read(),d=read(),sid=id[l],eid=id[r],tot+=(r-l+1)*d;
	if(sid==eid)rep(i,l,r)a[i]+=d,sum[sid]+=d;
	else{
		rep(i,sid+1,eid-1)sum[i]+=len*d,tag[i]+=d;
		for(int i=l;id[i]==sid;++i)a[i]+=d,sum[sid]+=d;
		for(int i=r;id[i]==eid;--i)a[i]+=d,sum[eid]+=d;
	}
	while(w<=tot*(mi[k]-1)&&k)--k;
	pos=0,wt=w-tot*(mi[k]-1);
	while(sum[pos+1]*mi[k]<wt&&(pos+1)<=n)++pos,wt-=sum[pos]*mi[k];pos*=len;
	while((tag[id[pos+1]]+a[pos+1])*mi[k]<wt)++pos,wt-=(tag[id[pos]]+a[pos])*mi[k];
	wrt(n*k+pos),putchar('\n');
}
int main(){
	init();
	while(q--)solve();
	return 0;
} 
```
