# 🔀 Merge Sort in C++

This repository contains a simple implementation of the **Merge Sort** algorithm in C++ with clear, step-by-step logic.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of the array) as input.  
- Then it reads `n` integers into a vector.  
- **Merge Sort** is applied using a recursive divide-and-conquer approach:  
  1. The array is divided into two halves.  
  2. Each half is recursively sorted.  
  3. The two sorted halves are merged into a single sorted array.  
- The `merge` function handles combining two sorted subarrays into one while maintaining order.  

---

## 💻 Code

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to merge two sorted subarrays into one
void merge(vector<int> &a , int low , int mid , int high){
    vector<int> temp; // Temporary array to store merged elements

    int left = low;       // Start index of left subarray
    int right = mid + 1;  // Start index of right subarray

    // Merge elements from left and right subarrays in sorted order
    while(left <= mid && right <= high){
        if(a[left] <= a[right]){
            temp.push_back(a[left++]);
        }
        else{
            temp.push_back(a[right++]);
        }
    }

    // Copy any remaining elements from left subarray
    while(left <= mid) temp.push_back(a[left++]);

    // Copy any remaining elements from right subarray
    while(right <= high) temp.push_back(a[right++]);

    // Copy the merged elements back to the original array
    for(int i = low, j = 0; i <= high; i++, j++){
        a[i] = temp[j];
    }
}

// Recursive Merge Sort function
void mergeSort(vector<int> &a , int low , int high){
    if(high <= low) return; // Base case: single element is already sorted

    int mid = low + (high - low) / 2; // Find the middle index

    // Recursively sort the left half
    mergeSort(a , low , mid);

    // Recursively sort the right half
    mergeSort(a , mid + 1 , high);

    // Merge the two sorted halves
    merge(a , low , mid , high);
}

int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    int n; 
    cin >> n; 
    vector<int> a(n); 

    for(int i = 0; i < n; i++){
        cin >> a[i]; 
    }

    mergeSort(a , 0 , n - 1); 

    for(int i = 0; i < n; i++){
        cout << a[i] << " "; 
    }
    cout << endl;

    return 0;
}

```

⏳ Time Complexity

Best Case: O(n log n) → array already sorted

Average Case: O(n log n)

Worst Case: O(n log n) → array sorted in reverse order

💾 Space Complexity

O(n) → temporary array used during merging

O(log n) → recursive call stack space