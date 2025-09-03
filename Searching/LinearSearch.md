# 🔍 Linear Search in C++

This repository contains a simple implementation of the **Linear Search** algorithm in C++.

---

## 📌 Code Explanation
- The program takes an integer `n` (size of the array) as input.  
- Then it reads `n` integers into a vector.  
- A target element is provided by the user.  
- Linear Search is applied:
  - The array is scanned element by element.
  - If the target is found, its index is returned.
  - If the element is not present, `-1` is returned.  

---

## 💻 Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int LinearSearch(const vector<int> &a, int t) {
    for (int i = 0; i < a.size(); i++) {
        if (a[i] == t) return i;
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

    cout << "Enter the target element: ";
    int target;
    cin >> target;

    int ans = LinearSearch(a, target);

    if (ans == -1) {
        cout << "Not found" << endl;
        return 0;
    }
    cout << "Element is at index: " << ans << endl;
}

```

⏳ Time Complexity

Best Case: O(1) → when the element is found at the first position

Average Case: O(n)

Worst Case: O(n) → when the element is not present or at the last index

💾 Space Complexity

O(n): to store the input array

O(1): extra space used for variables