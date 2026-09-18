## 01. Minimum Absolute Difference In BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-absolute-difference-in-bst-1665139652/1)

### Problem Description

**Task:** Given the root of a Binary Search Tree (BST) containing n (n > 1) nodes, find the minimum absolute difference between the values of any two different nodes in the tree.Return the minimum absolute difference.Examples:Input: root[] = [50, 30, 70, 20, N, 60, 80]Output: 10Explanation: There are no two nodes whose absolute difference is smaller than 10.Input: root[] = [60, 30, 90, 10]Output: 20Explanation: There are no two nodes whose absolute difference is smaller than 20.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-18 07:01:15
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def absDiff(self, root):
        self.prev = None
        self.ans = float('inf')

        def inorder(node):
            if not node:
                return

            inorder(node.left)

            if self.prev is not None:
                self.ans = min(self.ans, node.data - self.prev)

            self.prev = node.data

            inorder(node.right)

        inorder(root)
        return self.ans
```

*Generated on: 9/18/2026, 7:01:53 AM*