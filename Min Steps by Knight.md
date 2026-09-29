## 01. Min Steps by Knight

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/steps-by-knight5927/1)

### Problem Description

**Task:** Given a square chessboard of size n × n, the initial position knightPos and target position targetPos of a Knight are given. Find the minimum number of moves required for the Knight to reach targetPos.A Knight moves in an L-shape, covering 2 cells in one direction and 1 cell perpendicular to it. From (x, y), it can move to: (x ± 2, y ± 1) and (x ± 1, y ± 2)This gives at most 8 possible moves:Note: The positions are given using 1-based indexing.Examples:Input: n = 3, knightPos[] = [3, 3], targetPos[] = [1, 2]Output: 1Explanation: Knight takes 1 step to reach from (3, 3) to (1 ,2).Input: n = 6, knightPos[] = [1, 3], targetPos[] = [5, 1]

#### Examples

##### Example 1

- **Output:**
```text
2
```
- **Explanation:** In above diagram Knight takes 2 step to reach from (1, 3) to (5, 0): (1, 3) - > (3, 2) - > (5, 1)

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-29 06:00:06
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minStepToReachTarget(self, knightPos, targetPos, n):
        if knightPos == targetPos:
            return 0

        moves = [
            (2, 1), (2, -1), (-2, 1), (-2, -1),
            (1, 2), (1, -2), (-1, 2), (-1, -2)
        ]

        start = (knightPos[0] - 1, knightPos[1] - 1)
        target = (targetPos[0] - 1, targetPos[1] - 1)

        queue = deque([(start[0], start[1], 0)])
        visited = {start}

        while queue:
            x, y, steps = queue.popleft()

            for dx, dy in moves:
                nx, ny = x + dx, y + dy

                if 0 <= nx < n and 0 <= ny < n and (nx, ny) not in visited:
                    if (nx, ny) == target:
                        return steps + 1

                    visited.add((nx, ny))
                    queue.append((nx, ny, steps + 1))

        return -1
```

*Generated on: 9/29/2026, 6:02:35 AM*