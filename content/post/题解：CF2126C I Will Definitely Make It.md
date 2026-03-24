---
title: "First Post"
date: 2026-03-23
draft: false
categories: ["solution"]
tags: ["普及-","贪心"]
---

## 思路
因为从 $x$ 到 $y$ 的时间与从 $x$ 到 $z$ 再到 $y$ 的时间相同 $(x \le z \le y)$ ;    
而如果直接从 $x$ 到 $y$ 的话，有一段时间还在比 $z$ 低的 $x$ ，显然劣于从 $x$ 到 $z$ 再到 $y$ ;  
所以直接从当前塔一路向更高的塔走，直到某一刻水升上来所需时间小于传送所需时间，就会被水淹没。  
## 实现
将塔的高度排序，把比初始点还低的塔排除掉，再遍历一遍即可。   
## 代码

```cpp
#include<bits/stdc++.h>
#define int long long
#define fep(i,s,e) for(int i=s;i<e;i++)
#define pef(i,s,e) for(int i=s;i>e;i--)
#define rep(i,s,e) for(int i=s;i<=e;i++)
#define per(i,s,e) for(int i=s;i>=e;i--)
using namespace std;
const int N=1e5+7;
int T,n,k,h[N];
signed main(){
	cin>>T;
	while(T--){
		cin>>n>>k;
		rep(i,1,n){
			cin>>h[i];
		}
		rep(i,1,n){
			if(h[i]<h[k])h[i]=0;
		}
		sort(h+1,h+n+1);
		int head=1;
		rep(i,1,n){
			if(h[i]==0){
				head++;
			}
		}
		int wt=0,p=1;
		rep(i,head,n-1){
			if(abs(h[i]-wt)<abs(h[i+1]-h[i])){
				cout<<"NO\n";
				p=0;
				break;
			}
			wt+=abs(h[i+1]-h[i]);
		}
		if(p){
			cout<<"YES\n";
		}
	}
}
```