---
tags:
  - 板子
---
# 裸板

```cpp
typedef unsigned long long ull;const int N=1e6+1;
ull a[N],H[N],len,P[N]={1,131};
char s[N];
void pre(){
	for(int i=2;i<=100;++i)P[i]=P[i-1]*P[1];
	for(int i=0;i<(int)len;++i)H[i]=H[i-1]*P[1]+s[i];
}
ull gethash(ull L,ull R){return H[R]-H[L-1]*P[R-L+1];}
ull Hash(char*s){//整体hash,等价于gethash(0,len-1)
	ull ans=0;
	while(*s)ans=ans*P[1]+(*s++);
	return ans;
}
```