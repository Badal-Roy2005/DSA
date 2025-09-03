# Quick Sort Algorithm (C++ Implementation)

This program implements the **Quick Sort** algorithm in C++ using recursion and partitioning.  
Quick Sort is an efficient, comparison-based, divide-and-conquer sorting algorithm.

---

## 📌 Code

```cpp
#include <bits/stdc++.h>
using namespace std;

// Partition function: places pivot element at its correct position
int calPart(vector<int> &a, int low, int high)
{
    int left = low;          // starting index
    int right = high;        // ending index
    int pivot = a[low];      // choose the first element as pivot

    // Loop until left and right pointers cross
    while (left < right)
    {
        // Move left pointer until finding an element greater than pivot
        while ( left <= high && a[left] <= pivot)
            left++;

        // Move right pointer until finding an element smaller than pivot
        while ( right >= low && a[right] >= pivot)
            right--;

        // If pointers haven't crossed, swap mismatched elements
        if (left < right) {
        swap(a[left], a[right]);
}
    }

    // Place pivot at its correct sorted position
    swap(a[low], a[right]);

    return right;  // return pivot index
}

// Recursive Quick Sort function
void QuickSort(vector<int> &a, int low, int high)
{
    if (low >= high) return;  // Base case: single element

    int partition = calPart(a, low, high);  // Partition index

    // Recursively sort left half
    QuickSort(a, low, partition - 1);

    // Recursively sort right half
    QuickSort(a, partition + 1, high);
}

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    int n;
    cin >> n;  // Input size of array

    vector<int> a(n);
    for (int i = 0; i < n; i++)
    {
        cin >> a[i];  // Input elements
    }

    QuickSort(a, 0, n - 1);  // Sort the array

    // Print sorted array
    for (int i = 0; i < n; i++)
    {
        cout << a[i] << " ";
    }
    cout << "\n";

    return 0;
}

```

⏱️ Time Complexity

Best Case: O(n log n) (balanced partitions).

Average Case: O(n log n) (expected).

Worst Case: O(n^2) (when pivot always gives unbalanced partitions, e.g., sorted input with first element as pivot).

📦 Space Complexity

O(log n) due to recursive stack calls (in average case).

No extra arrays needed (in-place sorting).
