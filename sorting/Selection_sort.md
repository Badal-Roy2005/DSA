# 📝 Selection Sort in C++

This repository contains a simple implementation of the **Selection Sort** algorithm in C++.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of array) as input.  
- Then it reads `n` integers into a vector.  
- Selection Sort is applied:  
  - For each position `i`, the smallest element in the unsorted portion (`i … n-1`) is found.  
  - That smallest element is swapped with the element at index `i`.  
  - This process repeats until the array is fully sorted.  

---

## 💻 Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n; 
    cin >> n;
    vector<int> a(n);

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    for (int i = 0; i < n - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < n; j++) {
            if (a[j] < a[minIdx]) {
                minIdx = j;
            }
        }
        if (minIdx != i) {
            swap(a[i], a[minIdx]);
        }
    }

    // Print the sorted array
    for (int i = 0; i < n; i++) {
        cout << a[i] << " ";
    }
    cout << endl;

    return 0;
}


```

⏳ Time Complexity

Best Case: O(n²) → even if the array is already sorted, selection sort still scans the entire unsorted portion.

Average Case: O(n²)

Worst Case: O(n²)

💾 Space Complexity

O(n) → to store the input array

O(1) → extra space used for variables and swaps