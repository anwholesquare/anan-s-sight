---
title: "Ugh, Not Sorting Algorithms Again!"
datePublished: Thu May 11 2023 18:41:42 GMT+0000 (Coordinated Universal Time)
cuid: clhjh7f19000i09mm8q9vdkid
slug: sorting-algorithms-again
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683749313743/c3b17591-6b35-4f03-8ff6-ca5bef94316f.png
tags: sorting, quick-sort, bubble-sort, merge-sort, sortingtechniques

---

Before starting the advanced topics for sorting elements, we must have these basic sorting methods:

1. Bubble Sort
    
2. Quick Sort
    
3. Merge Sort
    
4. Insertion Sort
    
5. Selection Sort
    

Let's quickly review the algorithm one by one below:

### Bubble Sort

*The idea is to place the largest/minimal element in its position and keep doing the same for every other element.*

Code:

```cpp
void bubble () {
    int n = v.size();
    for (int i = 0; i<n; i++) {
        for (int j =0; j<n; j++) {
            if (v[i] < v[j]) 
                swap(v[i], v[j]);
        }
    }
}
```

### Selection Sort

![](https://media.geeksforgeeks.org/wp-content/uploads/20230419183518/selection-sort-geeksforgeeks.gif align="left")

Code:

```cpp
void selection () {
    int n = v.size();
    for (int i = 0; i<n; i++) {
        for (int j =i+1; j<n; j++) {
            if (v[i] > v[j]) 
                swap(v[i], v[j]);
        }
    }
}
```

### Insertion Sort

![Sorting Algorithm Explained With GIF Animations | Insertion sort, Bubble  sort, Bubble sort algorithm](https://i.pinimg.com/originals/92/b0/34/92b034385c440e08bc8551c97df0a2e3.gif align="left")

Code:

```cpp
void insertion () {
    int n = v.size();
    for(int i=1;i<n;i++){
        int x = v[i];
        for (int j = i-1; j >=0; j--) {
            if (x < v[j])  {
                v[j+1] = v[j];
                v[j] = x;
            }else {
                break;
            }
        }
    }
}
```

### Quick Sort:

![Using Hermes's Quicksort to run Doom: A tale of JavaScript exploitation](https://engineering.fb.com/wp-content/uploads/2022/07/Hermes-quicksort.gif?w=720 align="left")

Code:

```cpp
void quickSort(int pivot, int last)
{
    if (pivot < last)
    {
        int i = pivot + 1;
        int j = last;
       
        while (v[i] < v[pivot])
                i++;
        while (v[j] > v[pivot])
                j--;
                
        while (i < j)
        {
            swap(v[j], v[i]);
            while (v[i] < v[pivot])
                i++;
            while (v[j] > v[pivot])
                j--;
        }
        swap(v[j], v[pivot]);
        quickSort(pivot, j - 1);
        quickSort(j + 1, last);
    }
}
```

### Merge Sort

![Merge Sort Algorithm - GeeksforGeeks](https://media.geeksforgeeks.org/wp-content/uploads/20230331125035/Merge-sort-gif-(1).gif align="left")

Code:

```cpp
#include <bits/stdc++.h>
using namespace std;
int arr[] = {4, 2, 4, 5, -30, -02, 3, -60};
void merge(int low, int mid, int hi)
{
    int sa1 = mid - low + 1;
    int sa2 = hi - mid;
    int L[sa1 + 1], R[sa2 + 1];
    for (int i = 0; i < sa1; i++)
    {
        L[i] = arr[low + i];
    }
    for (int j = 0; j < sa2; j++)
    {
        R[j] = arr[mid + 1 + j];
    }
    L[sa1] = INT_MAX;
    R[sa2] = INT_MAX;
    int i = 0, j = 0;
    for (int k = low; k <= hi; k++)
    {
        if (L[i] <= R[j])
            arr[k] = L[i++];
        else
            arr[k] = R[j++];
    }
}
void mergeSort(int low, int hi)
{
    if (low < hi)
    {
        int mid = (low + hi) / 2;
        mergeSort(low, mid);
        mergeSort(mid + 1, hi);
        merge(low, mid, hi);
    }
}
int main()
{
    int size = sizeof(arr) / sizeof(arr[0]);
    mergeSort(0, size);
    for (int i = 0; i < size; i++)
    {
        cout << arr[i] << " ";
    }
}
```

**N.B:** Interesting sorting techniques are coming soon in this article.