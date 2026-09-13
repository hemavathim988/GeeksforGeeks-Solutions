## 01. Party in Town

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/party-in-town3951/1)

### Problem Description

**Task:** Geek Town has n houses numbered from 1 to n, choose a house to host a party such that its distance from its farthest house is as small as possible. Return this minimum possible distance.The houses are connected by n − 1 bidirectional roads, forming a tree. The connections are given as an adjacency list adj, where adj[i] contains all houses directly connected to house i + 1. Examples:Input: adj[][] = [[2], [1, 4, 3], [2], [2]] Output: 1

#### Examples

##### Example 1

- **Explanation:** Party should take place at house number 2 or 3. The minimum distance is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-13 10:12:43
- **Status:** Correct
- **Marks:** 4

```python
from collections import deque

class Solution:

    def bfs(self, adj, start):
        n = len(adj)

        dist = [-1] * n
        q = deque()

        dist[start] = 0
        q.append(start)

        farthest_node = start
        farthest_dist = 0

        while q:
            node = q.popleft()

            for next_node in adj[node]:
                next_node = next_node - 1

                if dist[next_node] == -1:
                    dist[next_node] = dist[node] + 1
                    q.append(next_node)

                    if dist[next_node] > farthest_dist:
                        farthest_dist = dist[next_node]
                        farthest_node = next_node

        return farthest_node, farthest_dist

    def partyHouse(self, adj):

        # First BFS
        farthest_node, _ = self.bfs(adj, 0)

        # Second BFS
        _, diameter = self.bfs(adj, farthest_node)

        return (diameter + 1) // 2
```

*Generated on: 9/13/2026, 10:13:18 AM*