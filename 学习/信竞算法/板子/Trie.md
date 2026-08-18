---
tags:
  - 板子
---
# 裸板

```cpp
int getnum(char x){
    if(isupper(x))return x-'A';
    else if(islower(x))return x-'a'+26;
    else return x-48+52;
}
struct trie{
	int nex[N][65],cnt[N],idx;
	void insert(char* s){
		int p=0,l=strlen(s),c;
		rep(i,0,l-1){
			c=getnum(s[i]);
			if(!nex[p][c])nex[p][c]=++idx;
			++cnt[p=nex[p][c]];
		}
	}
	int find(char* s){
		int p=0,l=strlen(s),c;
		rep(i,0,l-1){
			c=getnum(s[i]);
			if(!nex[p][c])return 0;
			p=nex[p][c];
		}
		return cnt[p];
	}
	void clear(){
		rep(i,0,idx)rep(j,0,64)nex[i][j]=0;
		memset(cnt,0,(idx+1)*sizeof(int));
		idx=0;
	}	
}T;
```
# 优化
```cpp
char s[N];
struct trie{
    int cnt,nxt[N],top[N];
    int siz[N],v[N];
    void insert(char* s){
        int p=1,len=strlen(s),x,pos;
        for(int i=0;i<len;i++){
            x=s[i],pos=top[p];
			if(x<v[pos]){
                v[++cnt]=x,top[p]=cnt;
                nxt[cnt]=pos,p=cnt;
            }
            else{
                while(v[nxt[pos]]<=x) pos=nxt[pos];
				if(v[pos]!=x){
                    v[++cnt]=x;
                    nxt[cnt]=nxt[pos];
                    nxt[pos]=cnt,p=cnt;
                }
                else p=pos;
            }
            siz[p]++;
        }
    }
    int query(char* s){
        int p=1,len=strlen(s),x,pos;
        for(int i=0;i<len;i++){
            x=s[i],pos=top[p];
            while(v[nxt[pos]]<=x) pos=nxt[pos];
            if(v[pos]!=x) return 0;
        	else p=pos;
		}
        return siz[p];
    }
    void clear(){
    	for(int i=1;i<=cnt;i++)
    		siz[i]=top[i]=0;
		v[0]=inf,cnt=1;
	}
}T;
```
# 二进制 Trie

```cpp
#include<bits/stdc++.h>
#define rep(u,x,y) for(int u=x;u<=y;++u)
#define per(u,x,y) for(int u=x;u>=y;--u)
using namespace std;
const int N=3e6+1;
int a[N],n,ans,idx,tr[N][2],res,now;
struct trie{
	void insert(int x){
		now=0;
		per(i,31,0){//从高位开始放 
			if(!tr[now][(x>>i)&1]) tr[now][(x>>i)&1]=++idx;
			now=tr[now][(x>>i)&1];
		}
	}
	int query(int x){
		res=now=0;
		per(i,31,0){//从高位开始要
			if(!tr[now][((x>>i)&1)^1]) now=tr[now][(x>>i)&1];
			else now=tr[now][((x>>i)&1)^1],res=res^(1<<i);
		}
		return res;
	}
}T;
int main(){
	cin>>n;
	rep(i,1,n)cin>>a[i],T.insert(a[i]);
	rep(i,1,n)ans=max(ans,T.query(a[i]));
	wrt(ans);
	return 0;
}
```