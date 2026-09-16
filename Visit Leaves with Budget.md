## 01. Visit Leaves with Budget

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/leaf-under-budget/1)

### Problem Description

**Task:** Given a binary tree and an integer k, where you start from the root at level 1. The cost of visiting a leaf node is equal to the level of that leaf node. You can visit any number of leaf nodes, but the total cost of visiting them must not exceed k. Return the maximum number of leaf nodes that can be visited within the given budget.Examples:Input: root[] = [10, 8, 2, 3, N, 3, 6, N, N, N, 4], k = 8

#### Examples

##### Example 1

- **Output:**
```text
2 Cost For visiting Leaf Node 3: 3 Cost For visiting Leaf Node 4: 4 Cost For visiting Leaf Node 6: 3 To maximize the number of visited leaves, choose the two cheapest leaves: Cost = 3 + 3 = 6 ≤ 8. Thus, the maximum number of leaf nodes that can be visited is 2.Input: root[] = [1, 2, 3, 4, 5, 6, 7], k = 5Output: 1Explanation: The leaf nodes are 4, 5, 6 and 7, and all are at level 3. Therefore, visiting each leaf costs 3. With a budget of 5, we can visit only one leaf because: 3 ≤ 5, but 3 + 3 > 5. Thus, the maximum number of leaf nodes that can be visited is 1.Input: root[] = [1], k = 1 Output: 1Explanation: The root node is also a leaf node and is at level 1. Therefore, its visiting cost is 1. Thus, the maximum number of leaf nodes that can be visited is 1.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-09-16 21:54:52
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def getCount(self, root, k):

        costs = []

        def dfs(node, level):
            if node is None:
                return

            # If the node is a leaf
            if node.left is None and node.right is None:
                costs.append(level)
                return

            dfs(node.left, level + 1)
            dfs(node.right, level + 1)

        # Root is at level 1
        dfs(root, 1)

        # Cheapest leaves first
        costs.sort()

        count = 0
        total = 0

        for cost in costs:
            if total + cost <= k:
                total += cost
                count += 1
            else:
                break

        return count
```

#### Solution 2 (Python)

- **Submitted:** 2026-09-15 07:12:45
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def getCount(self, root, k):

        costs = []

        def dfs(node, level):
            if node is None:
                return

            # If the node is a leaf
            if node.left is None and node.right is None:
                costs.append(level)
                return

            dfs(node.left, level + 1)
            dfs(node.right, level + 1)

        # Root is at level 1
        dfs(root, 1)

        # Cheapest leaves first
        costs.sort()

        count = 0
        total = 0

        for cost in costs:
            if total + cost <= k:
                total += cost
                count += 1
            else:
                break

        return count
```

*Generated on: 9/16/2026, 9:55:46 PM*