# Quick Sort
# Implement
```cpp
#include <bits/stdc++.h>
using namespace std;
int part(int a[],int l,int r)
{
    int x=a[r];
    int i=l-1;
    for(int j=l;j<r;j++)
    {
        if(a[j]<=x)
        {
            i++;
            swap(a[j],a[i]);

        }
    }
    swap(a[i+1],a[r]);
    return i+1;
}

void quicksort(int a[],int l,int r)
{
    if(l<r)
    {
        int p=part(a,l,r);
        quicksort(a,l,p-1);
        quicksort(a,p+1,r);

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
    quicksort(arr,0,s-1);  
    for(int i:arr)
        cout<<i<<" ";
}
```