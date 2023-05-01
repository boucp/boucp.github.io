# Selection Sort

## Implement
=== "Python"
    ```python3
    def selectionsort(arr,n):
       for i in range(n):
         min = i
         for j in range(i+1,n):
             if arr[j]<arr[min]:
                 min = j
          if min != i:
              a[min],a[i]=a[i],a[min]

    a=[43,5,4,2,1,6]
    s=len(a)
    selectionsort(a,s)
    print(*a)
    ```
=== "C++"
    ```cpp
    void selectionsort(int arr[],int n)
    {
       for(int i=0;i<n;i++)
       {
           int min = i;
          for (int j=i+1;j<n;j++)
          {
              if(arr[j]<arr[min])
                   min = j;
          }
           if (i != min)
               swap(arr[i],arr[min]);
       }
     }
    ```
