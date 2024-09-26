## 数位DP

 数位DP用于数字的统计。

- 给定两个正整数a，b。求[a,b]的所有整数中，每个数码各出现了多少次？

**[说明]**

1. 定义状态`dp[]`，`dp[i]`表示i位数字有多少个。

#### 1. 递推实现

```c++
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N=15;
ll ten[N],dp[N];
ll cnta[N],cntb[N];             //cnt[i]，统计数字“i”出现了多少次
int num[N];
void init(){                    //预计算dp[]
    ten[0] = 1;                 //ten[i]: 10的i次方
    for(int i=1;i<=N;i++){
        dp[i]  = i*ten[i-1];    //或者写成：dp[i]  = dp[i-1]*10+ten[i-1];
        ten[i] = 10*ten[i-1];
    }
}
void solve(ll x, ll *cnt){
    int len = 0;  //数字x有多少位
    while(x){     //分解x，num[i]是x的第i位数字
        num[++len] = x%10;
        x=x/10;
    }
    for(int i=len;i>=1;i--){                            //从高到低处理x的每一位
        for(int j=0;j<=9;j++)      cnt[j] += dp[i-1]*num[i];
        for(int j=0;j<num[i];j++)  cnt[j] += ten[i-1];  //特判最高位比num[i]小的数字
        ll num2 = 0;
        for(int j=i-1;j>=1;j--)    num2 = num2*10+num[j];
        cnt[num[i]] += num2+1;                          //特判最高位的数字num[i]
        cnt[0] -= ten[i-1];                             //特判前导0
    }
}
int main(){
    init();
    ll a,b;  cin >> a>>b;
    solve(a-1, cnta), solve(b, cntb);
    for(int i=0;i<=9;i++)  cout << cntb[i]-cnta[i] <<" ";
}
```

#### 2. 记忆化搜索

```c++
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
const int N = 15;
ll dp[N][N];
int num[N],now;                 //now：当前统计0~9的哪一个数字
ll dfs(int pos,int sum,bool lead, bool limit){    //pos：当前处理到第pos位
    ll ans = 0;
    if(pos == 0) return sum;    //递归到0位数，结束，返回
    if(!lead && !limit && dp[pos][sum]!=-1)  return dp[pos][sum];  //记忆化搜索
    int up = (limit ? num[pos] : 9);    //这一位的最大值，例如324的第3位是up = 3
    for(int i=0;i<=up;i++){                                         //下面以now=2为例：
        if(i==0 && lead)  ans += dfs(pos -1, sum,  true, limit&&i==up); // 计算000~099
        else if(i == now) ans += dfs(pos -1, sum+1,false,limit&&i==up); // 计算200~299
        else if(i != now) ans += dfs(pos -1, sum,  false,limit&&i==up); // 计算100~199
    }
    if(!lead && !limit) dp[pos][sum] = ans;       //状态记录：无前导0
    return ans;
}
ll solve(ll x){
    int len = 0;       //数字x有多少位
while(x){ 
num[++len] = x%10; 
x/=10;
}
    memset(dp,-1,sizeof(dp));
    return dfs(len,0,true,true);
}
int main(){
    ll a,b;    cin>>a>>b;
    for(int i=0;i<10;i++)   now = i, cout << solve(b)-solve(a-1)<<" ";  
    return 0;
}

```

