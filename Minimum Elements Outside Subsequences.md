## 01. Minimum Elements Outside Subsequences

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-number-of-elements-which-are-not-part-of-increasing-or-decreasing-subsequence2617/1)

### Problem Description

**Task:** Given an array arr[] of size n, partition its elements into a strictly increasing subsequence and a strictly decreasing subsequence.
Each element can belong to at most one of these subsequences, and some elements may remain unused.
Determine the minimum number of elements that cannot be included in either subsequence.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [7, 8, 1, 2, 4, 6, 3, 5, 2, 1, 8, 7]
```
- **Output:**
```text
2
```
- **Explanation:** One possible increasing subsequence is: [1, 2, 4, 5, 8]. One possible decreasing subsequence is: [7, 6, 3, 2, 1]. The remaining elements are 8 and 7, so the minimum number of unselected elements is 2.

##### Example 2

- **Input:**
```text
arr[] = [1, 4, 2, 3, 3, 2, 4]
```
- **Output:**
```text
0
```
- **Explanation:** One possible increasing subsequence is: [1, 2, 3, 4]. One possible decreasing subsequence is: [4, 3, 2]. All elements are included in one of the two subsequences.

#### Constraints

- **1.** `1 ≤ n ≤ 1001 ≤ arr[i] ≤ 100`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^3)
- **Expected Auxiliary Space Complexity:** O(n^3)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-07 06:59:51
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def minCount(self, arr):
        n = len(arr)

        from functools import lru_cache

        @lru_cache(None)
        def dp(i, inc_last, dec_last):
            if i == n:
                return 0


            ans = dp(i + 1, inc_last, dec_last)

            
            if arr[i] > inc_last:
                ans = max(ans, 1 + dp(i + 1, arr[i], dec_last))


            if arr[i] < dec_last:
                ans = max(ans, 1 + dp(i + 1, inc_last, arr[i]))

            return ans

        
        maximum_used = dp(0, 0, 101)

        return n - maximum_used
```

*Generated on: 9/7/2026, 7:00:33 AM*