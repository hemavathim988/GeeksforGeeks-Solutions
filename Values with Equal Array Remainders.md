## 01. Values with Equal Array Remainders

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/k-modulus-array-element0255/1)

### Problem Description

**Task:** Given an integer array arr[], count the number of positive integers k such that all elements of the array leave the same remainder when divided by k.If there are infinitely many such values of k, return -1.Examples:Input: arr[] = [38, 6, 34]

#### Examples

##### Example 1

- **Output:**
```text
-1Explanation: All elements in the array are equal. Therefore, for every positive integer k, all elements leave the same remainder when divided by k.
```
- **Explanation:** The values of k for which all elements leave the same remainder when divided by k are 1, 2, and 4. For k = 1, all elements leave remainder 0. For k = 2, all elements leave remainder 0. For k = 4, all elements leave remainder 2. No other positive integer satisfies the required condition. Hence, the answer is 3.Input: arr[] = [3, 2] Since there are infinitely many such values of k, the answer is -1.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + sqrt(g)) where g = gcd(|arr[i] - arr[0]|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-11 07:02:12
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def sameMod(self, arr):
        import math

        if all(x == arr[0] for x in arr):
            return -1

        g = 0

        for i in range(1, len(arr)):
            g = math.gcd(g, abs(arr[i] - arr[0]))

        count = 0

        for i in range(1, int(g ** 0.5) + 1):
            if g % i == 0:
                count += 1
                if i != g // i:
                    count += 1

        return count
```

*Generated on: 9/11/2026, 7:02:45 AM*