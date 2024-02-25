# update_range
#include <iostream>
#include<algorithm>
#include<queue>
#define ll long long
using namespace std;

int main()
{
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

//range sum 2
long long n,m,q;
cin>>n>>m>>q;
vector<vector<long long>>arr(n+1,vector<long long>(m+1));
for(long long i=1;i<=n;i++)
{
    for(long long j=1;j<=m;j++)
        cin>>arr[i][j];
}
vector<vector<long long>>pref(n+1,vector<long long>(m+1));
for(long long i=1;i<=n;i++)
{
    for(long long j=1;j<=m;j++)
    {
        pref[i][j]=pref[i][j-1]+arr[i][j];
    }
}
for(long long j=1;j<=m;j++)
{
    for(long long i=1;i<=n;i++)
    {
        pref[i][j]+=pref[i-1][j];
    }
}
ll x1,x2,y1,y2;
while(q--)
{
    cin>>x1>>y1>>x2>>y2;
    cout<<pref[x2][y2]-pref[x2][y1-1]-pref[x1-1][y2]+pref[x1-1][y1-1]<<"\n";
}


    return 0;
}
