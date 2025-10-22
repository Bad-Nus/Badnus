---
tags:
  - 板子
---
# 裸板
```cpp
void gather(){++sz[id[sta[tp]]=cnt],insta[sta[tp--]]=0;}
void tarjan(int u){
    low[u]=dfn[u]=++tot,sta[++tp]=u,insta[u]=1;
    for(int i=pre[u];i;i=nxt[i]){
        int to=h[i];
        if(!dfn[to])tarjan(to),low[u]=min(low[u],low[to]);
        else if(insta[to])low[u]=min(low[u],dfn[to]);
    }
    if(dfn[u]==low[u]){
		++cnt;
        while(sta[tp]!=u)gather();
        gather();
    }
}
```
# Tarjan
[例题](https://www.luogu.com.cn/problem/P2863)
```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
using namespace std;
typedef long long ll;
const int N=1e6+1;
ll h[N],pre[N],w[N],nxt[N],idx;
ll dfn[N],low[N],sta[N],id[N],insta[N],sz[N],tot,tp,cnt;
int n,m,x,y,z;
void add(int x,int y){
    h[++idx]=y;
    nxt[idx]=pre[x];
    pre[x]=idx;
}
void gather(){++sz[id[sta[tp]]=cnt],insta[sta[tp--]]=0;}
void tarjan(int u){
    low[u]=dfn[u]=++tot,sta[++tp]=u,insta[u]=1;
    for(int i=pre[u];i;i=nxt[i]){
        int to=h[i];
        if(!dfn[to])tarjan(to),low[u]=min(low[u],low[to]);
        else if(insta[to])low[u]=min(low[u],dfn[to]);
    }
    if(dfn[u]==low[u]){
		++cnt;
        while(sta[tp]!=u)gather();
        gather();
    }
}
int main(){
    cin>>n>>m;
    while(m--)cin>>x>>y,add(x,y);
    rep(i,1,n)if(!dfn[i])tarjan(i);
    cout<<cnt;
    return 0;
}
```