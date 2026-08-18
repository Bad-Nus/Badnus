---
tags:
  - 板子
---
```cpp
int t,n,m,q;
int a[N],s[N],c[N];
ll ans,f[M][N];
int lowbit(int x){return x&-x;}
ll query(int x,ll sum=0){
    while(x)sum+=c[x],x-=lowbit(x);
    return sum;
}
void upd(int x,int v){while(x<=m)c[x]+=v,x+=lowbit(x);}
int main(){
    t=read();
    rep(T,1,t){
        memset(f,0,sizeof f),ans=0;
        n=read(),q=read();
        rep(i,1,n)s[i]=a[i]=read();
        sort(s+1,s+1+n);
        m=unique(s+1,s+n+1)-s-1;
        rep(i,1,n)f[1][i]=1,a[i]=(lower_bound(s+1,s+1+m,a[i])-s);
        rep(i,2,q){
            memset(c,0,sizeof c);
            rep(j,1,n)f[i][j]+=query(a[j]-1),upd(a[j],f[i-1][j]);
        }
        rep(i,1,n)ans+=f[q][i];
        printf("Case #%d: %lld\n",T,ans);
    }
    return 0;
}
```