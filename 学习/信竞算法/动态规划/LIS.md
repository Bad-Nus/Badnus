# 定义

数组中删除若干个数后，构造一个单调递增的序列，这个序列的最大长度即最长上升子序列，下简称 LIS

形式化地，已知
$$A=\{a_1,a_2,\ldots,a_n\},B=\{a_{k_1},a_{k_2},\ldots,a_{k_m}\},其中 \forall i,j\in[1,m]且i\lt j,有 k_{i-1}\lt k_i且a_{k_{i-1}}\lt a_{k_i}$$

求 $m_\operatorname{max}$
# 解法
设 $f_i$ 为以第 $i$ 位为结尾的 LIS 长度,那么根据定义有 
$$f_i=\Big(\max\limits_{(j\lt i)\wedge(a_j\lt a_i)} f_j\Big)+1$$
## 暴力
对每一位 $i$ 暴力枚举 $\forall j\lt i$ 即可

复杂度 $O(n^2)$
```cpp
rep(i,1,n){
	rep(j,1,i-1)if(a[j]<a[i])f[i]=max(f[i],f[j]+1);
	ans=max(ans,f[i]);
}
```

## 树状数组
树状数组维护第 $i$ 位的 LIS 长度 $f_i$ ，式子变成了查询第 $i$ 位的前缀最大，将序列按权值从小到大排序后，以权值的原位置 $id_i$ 为树状数组下标 $i$ ，用 $i$ 的前缀最大 $f_j$ 更新即可。

复杂度 $O(n\log n)$
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

我们设 $f_i$ 为长度为 $i$ 的 LIS 末尾元素的最小值，我们发现 $f$ 单调不降。且 $f_i$ 越小必然越优，由此我们可以贪心地维护 $f_i$ 。

那么对于每一位 $a_j$ 考虑贡献：

- 若 $f_m\lt a_j$ ，那么增长，令 $f_{m+1}=a_j$
- 若 $f_m \ge a_j$ ，那么考虑维护 $f_i$ 的最小，我们设 $f_k$ 为最小的满足 $f_i\ge a_j$ 的位置，那么：
	- $f_{1\ldots k-1}$ 不满足 $f_i \ge a_j$ ，不更新
	- $f_{k+1\ldots m}$ 是由 $f_k$ 转移而来，相当于 LIS 的第 $k$ 位最优已经是 $a_j$ 。如果 $a_j$ 参与构成 $f_{k+1\ldots m}$ ，那么 $a_j$ 必然被多次使用，证明显然；若没贡献又没有考虑的必要。
	- 综上令 $f_k=a_j$ 即可

复杂度 $O(n\log n)$
```cpp
int n,cnt,c[N];
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

## M 元 LIS

需要预处理 M 元 LIS 个数时，暴力复杂度 $O(n^3)$ ，考虑维护，参考