# 🔎 Interpolation Search in C++

This repository contains a simple implementation of the **Interpolation Search** algorithm in C++.  
The program also includes a **sorting step** to ensure the array is sorted before searching, since Interpolation Search only works on sorted arrays.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of the array) as input.  
- Then it reads `n` integers into a vector.  
- The array is sorted using **`sort(a.begin(), a.end());`**.  
- A target element is provided by the user.  
- Interpolation Search is applied:
  - The position is estimated using the formula:  
    ```
    pos = left + ((target - a[left]) * (right - left)) / (a[right] - a[left])
    ```
  - If the element at `pos` matches the target, its index is returned.  
  - If the target is smaller, the search continues in the left part.  
  - If the target is larger, the search continues in the right part.  
  - If the element is not present, `-1` is returned.  

---

## 💻 Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int InterpolationSearch(const vector<int> &a, int t) {
    int left = 0;
    int right = a.size() - 1;

    while (left <= right && t >= a[left] && t <= a[right]) {
        if (a[left] == a[right]) {
            if (a[left] == t) return left;
            return -1;
        }

        int pos = left + ((double)(t - a[left]) * (right - left)) / (a[right] - a[left]);

        if (a[pos] == t) {
            return pos;
        } else if (a[pos] > t) {
            right = pos - 1;
        } else {
            left = pos + 1;
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

    // Sorting the array before applying Interpolation Search
    sort(a.begin(), a.end());

    cout << "Enter the target element: ";
    int target;
    cin >> target;

    int ans = InterpolationSearch(a, target);

    if (ans == -1) {
        cout << "Not found" << endl;
        return 0;
    }
    cout << "Element is at index: " << ans << endl;
}


```

⏳ Time Complexity

Sorting Step: O(n log n)

Best Case (Search): O(1) → when the element is found in the first probe

Average Case (Search): O(log log n) → for uniformly distributed data

Worst Case (Search): O(n) → when data is not uniformly distributed

Overall (with sorting included): O(n log n)

💾 Space Complexity

O(n): to store the input array

O(1): extra space used for variables