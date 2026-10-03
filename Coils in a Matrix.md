## 01. Coils in a Matrix

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/form-coils-in-a-matrix4726/1)

### Problem Description

**Task:** Given a positive integer n, consider a 4n * 4n matrix filled with integers from 1 to (4n) * (4n) in row-major order (left to right, top to bottom). Form two coils from the matrix:The first coil starts from the top-left cell (0, 0) and spirals inward.The second coil starts from the bottom-right cell (4n - 1, 4n - 1) and spirals inward in the opposite direction.Return these two coils in the same order.Examples:Input: n = 1Output: [[1, 5, 9, 13, 14, 15, 11, 7], [16, 12, 8, 4, 3, 2, 6, 10]]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-03 09:14:40
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def formCoils(self, n: int) -> list[list[int]]:
        m = 8 * n * n

        coil1 = [0] * m

        coil1[0] = 8 * n * n + 2 * n

        curr = coil1[0]
        direction = 1
        step = 2
        index = 1

        while index < m:

            for i in range(step):
                curr = curr - 4 * n * direction
                coil1[index] = curr
                index += 1

                if index == m:
                    break

            if index == m:
                break

            for i in range(step):
                curr = curr + direction
                coil1[index] = curr
                index += 1

                if index == m:
                    break

            direction = -direction
            step += 2

        total = 16 * n * n

        coil1 = [total + 1 - x for x in reversed(coil1)]

        coil2 = [total + 1 - x for x in coil1]

        return [coil1, coil2]
```

*Generated on: 10/3/2026, 9:15:16 AM*