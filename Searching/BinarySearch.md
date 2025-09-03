# 🔎 Binary Search in C++

This repository contains a simple implementation of the **Binary Search** algorithm in C++.  
The program also includes a **sorting step** to ensure the array is sorted before searching, since Binary Search only works on sorted arrays.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of the array) as input.  
- Then it reads `n` integers into a vector.  
- The array is sorted using **`sort(a.begin(), a.end());`**.  
- A target element is provided by the user.  
- Binary Search is applied:
  - The middle element of the range is checked.
  - If it matches the target, its index is returned.
  - If the target is smaller, the search continues in the left half.
  - If the target is larger, the search continues in the right half.
  - If the element is not present, `-1` is returned.  

---

## 💻 Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int BinarySearch(const vector<int> &a, int t) {
    int left = 0;
    int right = a.size() - 1;

    while (left <= right) {
        int mid = (left + right) / 2;

        if (a[mid] == t) {
            return mid;
        } else if (a[mid] > t) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    return -1;
}

int main() {
    int n;
    cin >> n;
    vector<int> a(n);

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    // Sorting the array before applying Binary Search
    sort(a.begin(), a.end());

    cout << "Enter the target element: ";
    int target;
    cin >> target;

    int ans = BinarySearch(a, target);

    if (ans == -1) {
        cout << "Not found" << endl;
        return 0;
    }
    cout << "Element is at index: " << ans << endl;
}

```

⏳ Time Complexity

Sorting Step: O(n log n)

Best Case (Search): O(1) → when the middle element is the target

Average Case (Search): O(log n)

Worst Case (Search): O(log n)

Overall (with sorting included): O(n log n)

💾 Space Complexity

O(n): to store the input array

O(1): extra space used for variables