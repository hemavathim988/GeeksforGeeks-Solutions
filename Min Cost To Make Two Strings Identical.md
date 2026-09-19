## 01. Min Cost To Make Two Strings Identical

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-cost-to-make-two-strings-identical1107/1)

### Problem Description

**Task:** Given two strings s1 and s2, and two integers costS1 and costS2, where costS1 is the cost of deleting one character from s1 and costS2 is the cost of deleting one character from s2, find the minimum cost required to make the two strings identical.You can delete any number of characters from either string, but the order of the remaining characters must be preserved.Examples:Input: s1 = "abcd", s2 = "acdb", costS1 = 10, costS2 = 20

#### Examples

##### Example 1

- **Output:**
```text
60
```
- **Explanation:** The two strings have no common characters, so delete all characters from both strings. The total cost is (2 × 10) + (2 × 20) = 60.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s1|*|s2|)
- **Expected Auxiliary Space Complexity:** O(min(|s1|, |s2|))

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-19 22:25:36
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def findMinCost(self, s1, s2, cost1, cost2):
        n = len(s1)
        m = len(s2)

        dp = [[0] * (m + 1) for _ in range(n + 1)]

        for i in range(1, n + 1):
            dp[i][0] = i * cost1

        for j in range(1, m + 1):
            dp[0][j] = j * cost2

        for i in range(1, n + 1):
            for j in range(1, m + 1):
                if s1[i - 1] == s2[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                else:
                    dp[i][j] = min(
                        dp[i - 1][j] + cost1,
                        dp[i][j - 1] + cost2
                    )

        return dp[n][m]
```

*Generated on: 9/19/2026, 10:26:14 PM*