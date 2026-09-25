## 01. Easiest Explanation of LIS Approach! - Java

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/box-stacking/1)

### Problem Description

**Task:** Given three arrays height[], width[], and length[] of size n, where height[i], width[i], and length[i] represent the dimensions of the ith box, find the maximum possible height of a stack formed using these boxes.
A box can be rotated so that any of its dimensions becomes its height.
A box can be placed on top of another only if both dimensions of its base are strictly smaller than those of the box below.
Multiple instances of the same box can be used.

#### Examples

##### Example 1

- **Input:**
```text
height[] = [4, 1, 4, 10], width[] = [6, 2, 5, 12], length[] = [7, 3, 6, 32]
```
- **Output:**
```text
60
```
- **Explanation:** One possible arrangement of the boxes from bottom to top is shown below. Note that there can be multiple instances of a box type. Hence, the total height of this stack is 10 + 32 + 4 + 4 + 6 + 1 + 3 = 60. No other combination of boxes produces a height greater than this.

##### Example 2

- **Input:**
```text
height[] = [1, 4, 3], width[] = [2, 5, 4], length[] = [3, 6, 1]
```
- **Output:**
```text
15
```
- **Explanation:** One possible arrangement of the boxes from bottom to top is shown below: Hence, the total height of this stack is 4 + 6 + 1 + 1 + 3 = 15 No other combination of boxes produces a height greater than this.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-25 06:59:35
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def maxHeight(self, height, width, length):
        n = len(height)
        boxes = []

        for i in range(n):
            a = height[i]
            b = width[i]
            c = length[i]

            boxes.append((max(a, b), min(a, b), c))
            boxes.append((max(b, c), min(b, c), a))
            boxes.append((max(a, c), min(a, c), b))

        boxes.sort(reverse=True)

        dp = [0] * len(boxes)

        for i in range(len(boxes)):
            dp[i] = boxes[i][2]

            for j in range(i):
                if boxes[j][0] > boxes[i][0] and boxes[j][1] > boxes[i][1]:
                    dp[i] = max(dp[i], dp[j] + boxes[i][2])

        return max(dp)
```

*Generated on: 9/25/2026, 7:01:04 AM*