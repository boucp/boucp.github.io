---

tags:

- সর্টিং
- ক্রম

---

# Selection Sort

## Pre-requisite topic:

- Array

## সিলেকশন শর্ট

সিলেকশন সর্ট হচ্ছে এমন এক সর্টিং টেকনিক, যা প্রথমে অ্যারের প্রত্যেক আইটেমকে রিড করে এবং অ্যারের সবচেয়ে ছোট আইটেমকে সিলেক্ট করে। এরপর সেই আইটেমের সাথে অ্যারের প্রথম আইটেম পরিবর্তন করে। তারপর একইভাবে দ্বিতীয় ছোট আইটেম খুঁজে বের করে। এবং সেই আইটেমকে অ্যারের দ্বিতীয় আইটেমের সাথে পরিবর্তন করে। এভাবে করে সম্পূর্ণ অ্যারে সর্টেড না হওয়া পর্যন্ত এই প্রসেস চলতে থাকে।

## অ্যালগরিদম

1. Set i to 0.
2. If i is less than the length of the array, go to step 3. Otherwise, the sorting is complete.
3. Set minIndex to i.
4. Iterate over the remaining unsorted part of the array, starting from i+1. For each element:
5. If the current element is smaller than the element at minIndex, update minIndex to the index of the current element.
6. If minIndex is not equal to i, swap the elements at i and minIndex.
7. Increment i by 1 and go back to step 2.

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

````
a=[43,5,4,2,1,6]
s=len(a)
selectionsort(a,s)
print(*a)
```
````

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
 } ```
