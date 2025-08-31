# ✏️ Insertion Sort in C++

This repository contains a simple implementation of the **Insertion Sort** algorithm in C++.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of array) as input.  
- Then it reads `n` integers into a vector.  
- Insertion Sort is applied:  
  - Starting from the second element, each element (`key`) is compared with the elements before it.  
  - Larger elements are shifted one position to the right.  
  - The `key` is placed in its correct position in the sorted portion of the array.  
- This process repeats until the entire array is sorted.  

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

    for (int i = 1; i < n; i++) {
        int key = a[i];
        int j = i - 1;

        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
        }

        a[j + 1] = key; // place key in the correct position
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

Best Case: O(n) → when the array is already sorted (only one comparison per element).

Average Case: O(n²)

Worst Case: O(n²) → when the array is sorted in reverse order.

💾 Space Complexity

O(n) → to store the input array

O(1) → extra space used for variables