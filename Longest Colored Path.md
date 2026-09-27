## 01. Longest Colored Path

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-colored-path--151454/1)

### Problem Description

**Task:** Given an undirected acyclic graph (tree) with n nodes numbered from 1 to n. Each node is colored either Red (R) or Blue (B).The colors of the nodes are given by a string s of length n, where:s[i] = 'R' means node i + 1 is Red.s[i] = 'B' means node i + 1 is Blue.You are also given a list of n - 1 edges edges[][], where each edges[i] = [u, v] represents an undirected edge between nodes u and v.You can start from any node and traverse along the edges to form a path.A path is called valid if, once you visit a Blue node, you cannot visit any Red node after it on the same path.In other words, a valid path must have the following form:Only Red nodes, orOnly Blue nodes, orSome Red nodes followed by some Blue nodes.A path containing a pattern like Blue - > Red is invalid.Find the maximum number of nodes in a valid path.Examples:Input: s = "RBB", edges = [[1, 2], [1, 3]] Output: 2Explanation: The longest path is either 1 - > 2 or 1 - > 3. In both cases, the length of the path is 2.Input: s = "BB", edges = [[1, 2]]

#### Examples

##### Example 1

- **Output:**
```text
2Explanation: The longest path is 1 - > 2. The length of the path is 2.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-27 07:56:41
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def longestPath(self, s, edges):
        n = len(s)

        graph = [[] for _ in range(n)]

        for u, v in edges:
            u -= 1
            v -= 1
            graph[u].append(v)
            graph[v].append(u)
          
        parent = [-1] * n
        order = [0]

        for u in order:
            for v in graph[u]:
                if v == parent[u]:
                    continue
                parent[v] = u
                order.append(v)

      
        down = [1] * n

        for u in reversed(order):
            for v in graph[u]:
                if parent[v] == u and s[v] == s[u]:
                    down[u] = max(down[u], down[v] + 1)

  
        up = [1] * n
        best_arm = [1] * n

        answer = 1

        for u in order:

            first = 0
            second = 0
            first_child = -1

            
            for v in graph[u]:
                if parent[v] == u and s[v] == s[u]:

                    length = down[v]

                    if length > first:
                        second = first
                        first = length
                        first_child = v

                    elif length > second:
                        second = length

            answer = max(answer, 1 + first + second)

       
            best_arm[u] = max(up[u], 1 + first)

       
            for v in graph[u]:

                if parent[v] != u or s[v] != s[u]:
                    continue

                if v == first_child:
                    other = second
                else:
                    other = first

                up[v] = 1 + max(up[u], 1 + other)

    
        for u, v in edges:

            u -= 1
            v -= 1

            if s[u] != s[v]:
                answer = max(
                    answer,
                    best_arm[u] + best_arm[v]
                )

        return answer
```

*Generated on: 9/27/2026, 7:57:22 AM*