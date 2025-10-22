---
tags:
  - 板子
---
# 裸板
```cpp
void dfs(int u,int f){
    dep[u]=dep[fa[u][0]=f]+1;
    rep(i,1,L-1)fa[u][i]=fa[fa[u][i-1]][i-1];
    for(int i=pre[u];i;i=nxt[i])if(h[i]!=f)dfs(h[i],u);
}
int LCA(int x,int y){
    if(dep[x]<dep[y])swap(x,y);
    per(i,L-1,0)if(dep[fa[x][i]]>=dep[y])x=fa[x][i];
    if(x==y)return x;
    per(i,L-1,0)if(fa[x][i]!=fa[y][i])x=fa[x][i],y=fa[y][i];
    return fa[x][0];
}
```
# LCA 倍增裸板
[例题](https://www.luogu.com.cn/problem/P3379)
```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
#define per(u,x,y) for(int u=x;u>=y;--u)
using namespace std;
typedef long long ll;
const int N=1e6+1,L=20;
int h[N],pre[N],w[N],nxt[N],idx;
int fa[N][L],dep[N];
int n,m,r,x,y;
void add(int x,int y){
    h[++idx]=y;
    nxt[idx]=pre[x];
    pre[x]=idx;
}
void dfs(int u,int f){
    dep[u]=dep[fa[u][0]=f]+1;
    rep(i,1,L-1)fa[u][i]=fa[fa[u][i-1]][i-1];
    for(int i=pre[u];i;i=nxt[i])if(h[i]!=f)dfs(h[i],u);
}
int LCA(int x,int y){
    if(dep[x]<dep[y])swap(x,y);
    per(i,L-1,0)if(dep[fa[x][i]]>=dep[y])x=fa[x][i];
    if(x==y)return x;
    per(i,L-1,0)if(fa[x][i]!=fa[y][i])x=fa[x][i],y=fa[y][i];
    return fa[x][0];
}
int main(){
    cin>>n>>m>>r;
    rep(i,1,n-1)cin>>x>>y,add(x,y),add(y,x);
    dfs(r,0);
    while(m--)cin>>x>>y,cout<<LCA(x,y)<<endl;
    return 0;
}
```