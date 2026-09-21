## 01. Check Level Anagrams in Binary Trees

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/check-if-all-levels-of-two-trees-are-anagrams-or-not/1)

### Problem Description

**Task:** Given the roots of two binary trees root1 and root2, check whether the nodes at every corresponding level of the two trees are anagrams of each other. Two levels are considered anagrams if they contain the same node values with the same frequencies, regardless of their order.Examples:Input: root1 = [1, 3, 2, N, N, 5, 4], root2 = [1, 2, 3, 4, 5, N, N]Output: true

#### Examples

##### Example 1

- **Output:**
```text
false
```
- **Explanation:** Level 0: [1] and [1] Level 1: [2, 3] and [2, 4] Since the node values at level 1 are not anagrams, the answer is false.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-21 06:41:58
- **Status:** Correct
- **Marks:** 4

```python
from collections import Counter, deque

class Solution:
    def areAnagrams(self, root1, root2):
        q1 = deque([root1])
        q2 = deque([root2])

        while q1 and q2:
            level1 = []
            level2 = []

            for _ in range(len(q1)):
                node = q1.popleft()
                level1.append(node.data)

                if node.left:
                    q1.append(node.left)
                if node.right:
                    q1.append(node.right)

            for _ in range(len(q2)):
                node = q2.popleft()
                level2.append(node.data)

                if node.left:
                    q2.append(node.left)
                if node.right:
                    q2.append(node.right)

            if Counter(level1) != Counter(level2):
                return False

        return not q1 and not q2
```

*Generated on: 9/21/2026, 6:42:31 AM*