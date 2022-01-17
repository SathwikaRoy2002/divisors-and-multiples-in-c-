#include<iostream>
#include<bits/stdc++.h>
using namespace std;
void countindex(int a[],int n)
{
    int max= *max_element(a,a+n);
    vector<int> freq(max+1,0);
    for(int i=0;i<n;i++)
    freq[a[i]]++;
    vector<int> res(max+1,0);
    for(int i=1;i<=max;i++){
        for(int j=i;j<=max;j+=i)
        {
            if(i==j)
            res[i]+=(freq[j]-1);
            else
            {
                res[i]+=freq[j];
                res[j]+=freq[i];
            }
        }
        
    }
    
    for(int i=0;i<n;i++)
    cout<<res[a[i]]<<endl;
}
int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)
    cin>>arr[i];
    countindex(arr,n);
    return 0;
}
