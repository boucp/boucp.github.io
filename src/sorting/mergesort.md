# Merge sort
## Implement
```cpp
#include <bits/stdc++.h>
#define INF 9999
using namespace std;
void merge(int a[],int l,int m, int r)
{
    int n1=m-l+1;
    int n2=r-m;
    int arr1[n1+1],arr2[n2+1];
    arr1[n1]=INF;
    arr2[n2]=INF;
    for(int i=0;i<n1;i++)
        arr1[i]=a[l+i];
    for(int i=0;i<n2;i++)
        arr2[i]=a[m+1+i];
    int i=0,j=0;
    for(int k=l;k<=r;k++)
    {
        if(arr1[i] <= arr2[j])
        {
            a[k]=arr1[i];
            i++;
        }
        else
        {
            a[k]=arr2[j];
            j++;
        }
    }
}
void mergesort(int a[],int l,int r)
{
    if(l<r)
    {
        int m=(l+r)/2;
        mergesort(a,l,m);
        mergesort(a,m+1,r);
        merge(a,l,m,r);
    }    
}
int main()
{
    freopen("input.txt","r",stdin);
    freopen("output.txt","w",stdout);
    int s;
    cin>>s;
    int arr[s];
    for(int i=0;i<s;i++)
        cin>>arr[i];
    mergesort(arr,0,s-1);  
    for(int i:arr)
        cout<<i<<" ";
}
```