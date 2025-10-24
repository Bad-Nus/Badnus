---
tags:
  - 板子
---
# 裸板
```cpp
void dijkstra(){
    memset(dist,0x3f,sizeof dist);
    q.push({dist[S]=0,S});
    while(q.size()){
        int u=q.top().u;q.pop();
        if(vis[u])continue;
        vis[u]=1;
        for(int i=pre[u];i;i=nxt[i])if(dist[h[i]]>dist[u]+w[i])q.push({dist[h[i]]=dist[u]+w[i],h[i]});
    }
}
```
# Dijkstra 堆优化
[标准例题](https://www.luogu.com.cn/problem/P4779)

[弱化例题](https://www.luogu.com.cn/problem/P3371)
```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
using namespace std;
typedef long long ll;
const int N=1e6+1;
ll h[N],pre[N],w[N],nxt[N],idx;
ll vis[N],dist[N];
ll n,m,x,y,z,S,T;
struct nd{
    ll dis,u;
    bool operator>(const nd&a)const{return dis>a.dis;}
};
priority_queue<nd,vector<nd>,greater<nd> >q;
void add(int x,int y,int z){
    h[++idx]=y;
    nxt[idx]=pre[x];
    w[pre[x]=idx]=z;
}
void dijkstra(){
    memset(dist,0x3f,sizeof dist);
    q.push({dist[S]=0,S});
    while(q.size()){
        int u=q.top().u;q.pop();
        if(vis[u])continue;
        vis[u]=1;
        for(int i=pre[u];i;i=nxt[i])if(dist[h[i]]>dist[u]+w[i])q.push({dist[h[i]]=dist[u]+w[i],h[i]});
    }
}
int main(){
    cin>>n>>m>>S;
    while(m--)cin>>x>>y>>z,add(x,y,z);
    dijkstra();
    rep(i,1,n)cout<<dist[i]<<' ';
    return 0;
}
```