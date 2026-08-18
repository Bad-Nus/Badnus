---
tags:
  - 板子
---

# 裸板
```cpp
bool bfs(){
    memset(d,-1,sizeof d);
    d[que[hh=tt=0]=S]=1;
    cur[S]=pre[S];
    while(hh<=tt){
        int u=que[hh++];
        for(int i=pre[u];~i;i=nxt[i]){
            int to=h[i];
            if(d[to]==-1&&w[i]){
                d[to]=d[u]+1;
                cur[to]=pre[to];
                if(to==T)return 1;
                que[++tt]=to;
            }
        }
    }
    return 0;
}
ll dfs(int u,int lim){
    if(u==T)return lim;
    ll flow=0;
    for(int i=cur[u];~i&&flow<lim;i=nxt[i]){
        int to=h[cur[u]=i];
        if(d[to]==d[u]+1&&w[i]){
            ll t=dfs(to,min(w[i],lim-flow));
            if(!t)d[to]=-1;
            w[i]-=t,w[i^1]+=t,flow+=t;
        }
    }
    return flow;
}
ll dinic(){
    ll flow=0,res;
    while(bfs())while(res=dfs(S,inf))flow+=res;
    return flow;
}
```
# Dinic 最大流裸板
[例题](https://www.luogu.com.cn/problem/P3376)
```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
using namespace std;
typedef long long ll;
const int N=1e6+1,inf=INT_MAX;
int n,m,S,T,x,y,z;
ll h[N],pre[N],w[N],nxt[N],idx;
int que[N],cur[N],d[N],hh,tt;
void add(int x,int y,int z){
    h[idx]=y;
    nxt[idx]=pre[x];
    w[pre[x]=idx++]=z;
}
bool bfs(){
    memset(d,-1,sizeof d);
    d[que[hh=tt=0]=S]=1;
    cur[S]=pre[S];
    while(hh<=tt){
        int u=que[hh++];
        for(int i=pre[u];~i;i=nxt[i]){
            int to=h[i];
            if(d[to]==-1&&w[i]){
                d[to]=d[u]+1;
                cur[to]=pre[to];
                if(to==T)return 1;
                que[++tt]=to;
            }
        }
    }
    return 0;
}
ll dfs(int u,int lim){
    if(u==T)return lim;
    ll flow=0;
    for(int i=cur[u];~i&&flow<lim;i=nxt[i]){
        int to=h[cur[u]=i];
        if(d[to]==d[u]+1&&w[i]){
            ll t=dfs(to,min(w[i],lim-flow));
            if(!t)d[to]=-1;
            w[i]-=t,w[i^1]+=t,flow+=t;
        }
    }
    return flow;
}
ll dinic(){
    ll flow=0,res;
    while(bfs())while(res=dfs(S,inf))flow+=res;
    return flow;
}
int main(){
    cin>>n>>m>>S>>T;
    memset(pre,-1,sizeof pre);
    while(m--)cin>>x>>y>>z,add(x,y,z),add(y,x,0);
    cout<<dinic();
    return 0;
}
```