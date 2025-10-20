---
tags:
  - 板子
---
# SPFA
[弱化例题](https://www.luogu.com.cn/problem/P3371)

```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
using namespace std;
typedef long long ll;
const int N=1e6+1;
ll h[N],pre[N],w[N],nxt[N],idx;
ll vis[N],dist[N],cnt[N];
ll n,m,x,y,z,S,T;
queue<int>q;
void add(int x,int y,int z){
    h[++idx]=y;
    nxt[idx]=pre[x];
    w[pre[x]=idx]=z;
}
bool spfa(int s){
    memset(dist,0x3f,sizeof dist);
    dist[s]=0;
    q.push(s);
    while(q.size()){
        int u=q.front();
        q.pop(),vis[u]=0;
        for(int i=pre[u];i;i=nxt[i])if(dist[h[i]]>dist[u]+w[i]){
            dist[h[i]]=dist[u]+w[i];
            cnt[h[i]]=cnt[u]+1;
            if(cnt[h[i]]>=n)return 0;
            if(!vis[h[i]])vis[h[i]]=1,q.push(h[i]);
        }
    }
    return 1;
}
int main(){
    cin>>n>>m>>S;
    while(m--)cin>>x>>y>>z,add(x,y,z);
    spfa(S);
    rep(i,1,n)dist[i]>0x3f3f3f3f/2?cout<<INT_MAX<<' ':cout<<dist[i]<<' ';
    return 0;
}
```