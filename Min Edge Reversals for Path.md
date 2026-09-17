## 01. Min Edge Reversals for Path

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-edges/1)

### Problem Description

**Task:** Given a directed graph with n vertices numbered from 1 to n. The graph is represented using a 2D array edges[][] of size m, where each entry edges[i] = [u, v] denotes a directed edge from vertex u to vertex v. You are also given a source vertex src and a destination vertex dst.Find the minimum number of edges that need to be reversed so that there exists at least one path from src to dst. If it is not possible to create a path from src to dst, return -1.Examples:Input: n = 3, edges[][] = [[1, 2], [3, 2]], src = 1, dst = 3 Output: 1

#### Examples

##### Example 1

- **Explanation:** One path already exists between 1 to 4 i.e. 1 - > 2 - > 3 - > 4.Constraints:1 ≤ n, m ≤ 10⁵¹ ≤ edges[i][0], edges[i][1] ≤ n1 ≤ src, dst ≤ n

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(n + m)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-17 06:41:35
- **Status:** Correct
- **Marks:** 4

```python
from collections import deque

class Solution:
    def minimumEdgeReversal(self, edges, n, src, dst):
        graph = [[] for _ in range(n + 1)]

        for u, v in edges:
            graph[u].append((v, 0))   # original direction
            graph[v].append((u, 1))   # reverse direction

        dist = [float('inf')] * (n + 1)
        dist[src] = 0

        dq = deque([src])

        while dq:
            u = dq.popleft()

            for v, cost in graph[u]:
                if dist[u] + cost < dist[v]:
                    dist[v] = dist[u] + cost

                    if cost == 0:
                        dq.appendleft(v)
                    else:
                        dq.append(v)

        if dist[dst] == float('inf'):
            return -1

        return dist[dst]
```

*Generated on: 9/17/2026, 6:42:08 AM*