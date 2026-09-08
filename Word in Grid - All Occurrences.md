## 01. Word in Grid - All Occurrences

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-the-string-in-grid0111/1)

### Problem Description

**Task:** Given a 2D grid mat[][] of size n × m consisting of characters and a string word, find all starting positions where the word occurs in the grid.
The word can be formed from any cell by moving in any of the 8 directions (2 horizontal, 2 vertical, and 4 diagonal) in a straight line without changing direction.
Each cell can be used at most once per occurrence.
Return all unique starting coordinates in lexicographically smallest order.

#### Examples

##### Example 1

- **Input:**
```text
mat[][] = {{a,b,a,b},{a,b,e,b},{e,b,e,b}}, word = "abe"
```
- **Output:**
```text
{{0,0}, {0,2}, {1,0}}
```
- **Explanation:** From (0,0) we can find "abe" in right-down diagonal. From (0,2) we can find "abe" in left-down diagonal. From (1,0) we can find "abe" in horizontally right direction.

##### Example 2

- **Input:**
```text
mat[][] = {{G,E,E,K,S,F,O,R,G,E,E,K,S}, {G,E,E,K,S,Q,U,I,Z,G,E,E,K}, {I,D,E,Q,A,P,R,A,C,T,I,C,E}}, word = "GEEKS"
```
- **Output:**
```text
{{0,0}, {0,8}, {1,0}}
```
- **Explanation:** From (0,0) we can find "GEEKS" horizontally right. From (0,8) we can find "GEEKS" horizontally right. From (1,0) we can find "GEEKS" horizontally right.

#### Constraints

- **1.** `1 <= n <= m <=`
- **2.** `501 <= |word| <= 20`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n*m*k) where k is constantAuxiliary Space: O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-08 07:10:05
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def searchWord(self, mat, word):
        n = len(mat)
        m = len(mat[0])
        ans = []

        directions = [
            (-1, -1), (-1, 0), (-1, 1),
            (0, -1),           (0, 1),
            (1, -1),  (1, 0),  (1, 1)
        ]

        for i in range(n):
            for j in range(m):
                if mat[i][j] != word[0]:
                    continue

                for di, dj in directions:
                    x = i
                    y = j
                    k = 0

                    while k < len(word):
                        if x < 0 or x >= n or y < 0 or y >= m:
                            break

                        if mat[x][y] != word[k]:
                            break

                        x += di
                        y += dj
                        k += 1

                    if k == len(word):
                        ans.append([i, j])
                        break

        return ans
```

*Generated on: 9/8/2026, 7:17:16 AM*