# Heap Sort
## Implement
```cpp
#include <bits/stdc++.h>
#define print(a) for(int i:arr)cout<<i<<" "
using namespace std;
void max_heapify(int a[],int n,int i)
{
    int l=2*i+1;
    int r=2*i+2;
    int m=i;
    if(l<n && a[l]>a[m])
        m=l;
    if(r<n && a[r]>a[m])
        m=r;
    if(i!=m)
    {
        swap(a[i],a[m]);
        max_heapify(a,n,m);
    }
}
void maxheap(int a[],int n)
{
    for(int i=n/2+1;i>=0;i--)
        max_heapify(a,n,i);
}
void heapsort(int a[],int n)
{
    maxheap(a,n);
    for(int i=n-1;i>0;i--)
    {
        swap(a[i],a[0]);
        max_heapify(a,i,0);
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
    heapsort(arr,s);
    print(arr);
}
```