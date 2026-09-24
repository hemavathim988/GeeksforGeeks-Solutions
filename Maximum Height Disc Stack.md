## 01. Maximum Height Disc Stack

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/stacking-up-discs1315/1)

### Problem Description

**Task:** Given two arrays r[] and h[] of size n, where r[i] and h[i] represent the radius and height of the i-th circular disc, respectively. A disc can be placed above another disc only if both its radius and height are strictly smaller than those of the disc below it. Find the maximum possible height of a stack that can be formed using the given discs. Each disc can be used at most once.Examples:Input: r[] = [5, 7, 3], h[] = [6, 5, 4]

#### Examples

##### Example 1

- **Output:**
```text
7
```
- **Explanation:** Neither disc can be placed above the other because both required dimensions are not strictly smaller. Therefore, the maximum possible height is 7.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-24 06:54:35
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def maxStackHeight(self, r, h):
        discs = sorted(zip(r, h))
        max_h = max(h)
        bit = [0] * (max_h + 1)
        ans = 0
        i = 0

        def query(x):
            res = 0
            while x > 0:
                res = max(res, bit[x])
                x -= x & -x
            return res

        def update(x, val):
            while x <= max_h:
                bit[x] = max(bit[x], val)
                x += x & -x

        while i < len(discs):
            j = i
            temp = []

            while j < len(discs) and discs[j][0] == discs[i][0]:
                height = discs[j][1]
                value = query(height - 1) + height
                temp.append((height, value))
                ans = max(ans, value)
                j += 1

            for height, value in temp:
                update(height, value)

            i = j

        return ans
```

*Generated on: 9/24/2026, 6:55:11 AM*