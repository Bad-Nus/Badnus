---
tags:
  - 板子
---
# 裸板

```cpp
const int N=1e6+1;
int la,lb,kmp[N],pos;
char a[N],b[N];
void Border(){//寻找b的border 
	for(int i=2;i<=lb;++i){
		while(pos&&b[i]!=b[pos+1])pos=kmp[pos];
		if(b[i]==b[pos+1])++pos;
		kmp[i]=pos;
	}
}
void Kmp(){//在a中找b，用b的前缀函数去失调跳跃 
	for(int i=1;i<=la;++i){
		while(pos&&a[i]!=b[pos+1])pos=kmp[pos];
		if(a[i]==b[pos+1])++pos;
		if(pos==lb)cout<<i-lb+1<<'\n',pos=kmp[pos];
	}
}
```