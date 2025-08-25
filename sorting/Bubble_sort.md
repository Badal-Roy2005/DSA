# 🌀 Bubble Sort in C++

This repository contains a simple implementation of the **Bubble Sort** algorithm in C++ with an optimization to stop early if the array becomes sorted.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of array) as input.
- Then it reads `n` integers into a vector.
- Bubble Sort is applied:
  - Adjacent elements are compared and swapped if they are in the wrong order.
  - If during a full pass no swaps occur, the algorithm stops early (optimization).

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
        bool isSwapped = false;
        for (int j = 0; j < n - i - 1; j++) {
            if (a[j] > a[j + 1]) {
                swap(a[j], a[j + 1]);
                isSwapped = true;
            }
        }
        if (!isSwapped) break;
    }

    // Print the sorted array
    for (int i = 0; i < n; i++) {
        cout << a[i] << " ";
    }
    cout << endl;

    return 0;
}



⏳ Time Complexity

Best Case: O(n) → when the array is already sorted (only one pass required)

Average Case: O(n²)

Worst Case: O(n²) → when the array is sorted in reverse order

💾 Space Complexity

O(n) → to store the input array

O(1) → extra space used for variables and swaps

✅ Overall: O(n)    