## 01. Ways to Reach Origin

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/paths-to-reach-origin3850/1)

### Problem Description

**Task:** Geek is standing at a point (x, y) on a 2D grid and wants to reach the origin (0, 0). From any point, Geek can move in only two directions: left, from (x, y) to (x - 1, y), or down, from (x, y) to (x, y - 1).Find the total number of distinct paths for Geek to reach (0, 0) from (x, y). Since the answer can be very large, return it modulo 10⁹+7.Examples:Input: x = 3, y = 0

#### Examples

##### Example 1

- **Output:**
```text
84
```
- **Explanation:** There are a total of 84 distinct paths from (3, 6) to (0, 0) using only left and down moves.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(x · y)
- **Expected Auxiliary Space Complexity:** O(x · y)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-30 06:02:25
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def ways(self, x: int, y: int) -> int:
        MOD = 10**9 + 7
        dp = [[0] * (y + 1) for _ in range(x + 1)]

        for i in range(x + 1):
            for j in range(y + 1):
                if i == 0 or j == 0:
                    dp[i][j] = 1
                else:
                    dp[i][j] = (dp[i - 1][j] + dp[i][j - 1]) % MOD

        return dp[x][y]
```

*Generated on: 9/30/2026, 6:03:02 AM*