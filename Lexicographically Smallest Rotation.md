## 01. Lexicographically Smallest Rotation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/lexicographically-smallest-string--151951/1)

### Problem Description

**Task:** Given a string s, find the lexicographically smallest string after rotating the string left any number of times including 0.Example:Input: s = "abcd"Output: "abcd"Explanation: String after each rotation are "abcd", "bcda", "cdab", "dabc" and so on. Lexicographically smallest among them is "abcd".Input: s = "baca"

#### Examples

##### Example 1

- **Output:**
```text
"abac"
```
- **Explanation:** Strings after each rotation are "baca", "acab", "caba", "abac" and so on. Lexicographically smallest among them is "abac".

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-02 08:26:21
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def lexiString(self, s):
        n = len(s)
        s2 = s + s
        i = 0
        j = 1
        k = 0

        while i < n and j < n and k < n:
            if s2[i + k] == s2[j + k]:
                k += 1
                continue

            if s2[i + k] > s2[j + k]:
                i = i + k + 1
                if i <= j:
                    i = j + 1
            else:
                j = j + k + 1
                if j <= i:
                    j = i + 1

            k = 0

        start = min(i, j)
        return s2[start:start + n]
```

*Generated on: 10/2/2026, 8:26:53 AM*