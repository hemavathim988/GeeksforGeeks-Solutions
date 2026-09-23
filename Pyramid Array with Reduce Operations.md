## 01. Pyramid Array with Reduce Operations

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pyramid-form3044/1)

### Problem Description

**Task:** Given an array arr[] consisting of stones, where arr[i] represents the height of the i-th stone.
You need to transform the stones into a pyramid by only reducing the heights of the stones. Reducing the height of a stone by 1 costs 1 unit, and stones cannot be increased or moved.
A valid pyramid consists of a contiguous subarray whose heights follow the pattern: 1, 2, 3, ..., x - 1, x, x - 1, ..., 2, 1 for some positive integer x.
Every stone outside this subarray must have a height of 0.
Find the minimum total cost required to build a pyramid. It is guaranteed that at least one valid pyramid can always be formed.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [1, 2, 3, 4, 2, 1]
```
- **Output:**
```text
4
```
- **Explanation:** We can obtain the array [1, 2, 3, 2, 1, 0] by subtracting 2 out of 4, 1 out of 2, and 1 out of 1. In total, we will subtract 4.

##### Example 2

- **Input:**
```text
arr[] = [1, 2, 1]
```
- **Output:**
```text
0
```
- **Explanation:** The array is already in pyramid form.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-23 06:57:28
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def formPyramid(self, arr):
        n = len(arr)
        left = [0] * n
        right = [0] * n

        left[0] = min(arr[0], 1)

        for i in range(1, n):
            left[i] = min(arr[i], left[i - 1] + 1)

        right[n - 1] = min(arr[n - 1], 1)

        for i in range(n - 2, -1, -1):
            right[i] = min(arr[i], right[i + 1] + 1)

        max_height = 0

        for i in range(n):
            max_height = max(max_height, min(left[i], right[i]))

        return sum(arr) - max_height * max_height
```

*Generated on: 9/23/2026, 6:58:03 AM*