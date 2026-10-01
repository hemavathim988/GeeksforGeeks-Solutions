## 01. Minimum Time to Finish Project

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/project-manager--141631/1)

### Problem Description

**Task:** An IT company is working on a large project consisting of n modules. The time required (in months) to complete the i^th module is stored in the array duration[]. The array dependencies[][], where dependencies[i] = [u, v], indicates that module v can be started only after module u is completed. Multiple modules can be worked on simultaneously as long as all their dependencies have been completed. Find the minimum time required to complete the entire project. If the project cannot be completed due to a cyclic dependency, return -1.

> **Note:** A module is never dependent on itself.

#### Examples

##### Example 1

- **Input:**
```text
duration[] = [10, 20, 30, 10, 30, 20], dependencies[][] = [[5, 2], [5, 0], [4, 0], [4, 1], [2, 3], [3, 1]]
```
- **Output:**
```text
80 The Graph of dependency forms this and the project will be completed when Module 1 is completed. The minimum taken time is 80 months, the maximum taken time is through the path 5 - > 2 - > 3 - > 1 which takes 20 + 30 + 10 + 20
```

##### Example 2

- **Input:**
```text
duration[] = [5, 5, 5], dependencies[][] = [[0, 1], [1, 2], [2, 0]]
```
- **Output:**
```text
-1
```
- **Explanation:** There is a cycle in the dependency graph hence the project cannot be completed.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-01 05:59:02
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minTime(self, duration, dependencies):
        n = len(duration)
        graph = [[] for _ in range(n)]
        indegree = [0] * n

        for u, v in dependencies:
            graph[u].append(v)
            indegree[v] += 1

        dp = duration[:]
        queue = []

        for i in range(n):
            if indegree[i] == 0:
                queue.append(i)

        count = 0
        ans = 0

        while queue:
            u = queue.pop(0)
            count += 1
            ans = max(ans, dp[u])

            for v in graph[u]:
                dp[v] = max(dp[v], dp[u] + duration[v])
                indegree[v] -= 1

                if indegree[v] == 0:
                    queue.append(v)

        if count != n:
            return -1

        return ans
```

*Generated on: 10/1/2026, 5:59:35 AM*