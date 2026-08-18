---
tags:
  - 板子
---
# 裸板
```cpp
void floyd(){rep(k,1,n)rep(i,1,n)if(dp[i][k])rep(j,1,n)if(dp[k][j])dp[i][j]=min(dp[i][j],dp[i][k]+dp[k][j]);}
```
# Floyd 最短路

```cpp
typedef long long ll;
const int N=1001;
ll n,m,dp[N][N];
void floyd(){rep(k,1,n)rep(i,1,n)if(dp[i][k])rep(j,1,n)if(dp[k][j])dp[i][j]=min(dp[i][j],dp[i][k]+dp[k][j]);}
```

# Floyd 连通性闭包传递

```cpp
bitset<N>dp[N];
void floyd(){
	rep(k,1,n)rep(i,1,n)if(dp[i][k])dp[i]|=dp[k];
}
```