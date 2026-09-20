## 01. Largest Subsquare Surrounded by X

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-subsquare-surrounded-by-x0558/1)

### Problem Description

**Task:** Given a square matrix mat[][] of size n × n, where each cell contains either 'X' or 'O'. Find the size of the largest square submatrix whose boundary is completely surrounded by 'X'. The cells inside the submatrix can contain either 'X' or 'O'. Only the four sides of the submatrix must contain 'X'.Return side length of the largest such square submatrix. Note: A square of size 1 is valid if its only cell is 'X'. If no such square submatrix exists, return 0.Examples:Input: mat[][] = [[X,X,X,O],[X,O,X,X],[X,X,X,O],[X,O,X,X]] Output: 3

#### Examples

##### Example 1

- **Explanation:** Here, the input represents following matrix of size 4 x 4 The square submatrix starting at (0,0) and ending at (2,2) is the largest submatrix surrounded by X. Therefore, size of that matrix would be 3.Input: mat[][] = [[X,X],[X,X]] Output: 2Explanation: The largest square submatrix surrounded by X is the whole input matrix.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^3)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-20 14:17:35
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def largestSubsquare(self, mat):
        n = len(mat)
        hor = [[0] * n for _ in range(n)]
        ver = [[0] * n for _ in range(n)]

        for i in range(n):
            for j in range(n):
                if mat[i][j] == 'X':
                    hor[i][j] = 1 + (hor[i][j - 1] if j else 0)
                    ver[i][j] = 1 + (ver[i - 1][j] if i else 0)

        ans = 0

        for i in range(n - 1, -1, -1):
            for j in range(n - 1, -1, -1):
                small = min(hor[i][j], ver[i][j])

                while small > ans:
                    if ver[i][j - small + 1] >= small and hor[i - small + 1][j] >= small:
                        ans = small
                        break
                    small -= 1

        return ans
```

*Generated on: 9/20/2026, 2:18:05 PM*